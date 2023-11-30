#1. Symptom and description


<img width="482" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/ac414c06-e6b1-49d0-90ad-356d051aa78d">

.
<img width="353" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/edfb2e17-fb15-4261-a1bc-f018deb39742">

When I test my code's output, I get a list of every single file in the system, about one thousand entries in total. I'm thinking that the issue comes from the searching the failure inducing input is supposed to do, where instead of listing only the files that satisfy the search condition of the string, the only files that should be displayed are the files containing the string but everything shows up instead.

This is the failure inducing input

<img width="696" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/2c9533d0-a7c2-4f6b-9439-b110b14dfdad">


#2. TA response

Check to see what your String is being compared to in your code. I would recommend printing statements of whatever variables you are comparing with to see what it is that fulfills the condition of those files being added to the output. 


#3. What Student got by trying that

<img width="485" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/c0bdb463-c7e8-4826-a3d7-31660700100c">

The bug is coming from the fact that instead of the correct string being compared against for the program, the string "q" is compared, and every file with the letter q in it is then listed, and because almost every file has that single letter, all of them pop up in the output. This comes from how the parameters string array, an array composed of two elements, one part being q and the other part being the actual string after the query, which is parameters[1] that equals string "Resonance", while parameters[0] is just the string "q".





#4. All info needed for setup



```
technical/
-  biomed/
   * ar615.txt ("Resonance")
-  plos/
   * journal.pbio.0020150.txt ("Resonance")
- any 1389 more .txt files with any text

TestDocServer.java
test.sh
DocSearchServer.java
Server.java
```

the test.sh script will put the output in a file to analyze

#File contents

TestDocServer.java
```
import static org.junit.Assert.*;
import org.junit.*;
import java.net.URI;
import java.net.URISyntaxException;
import java.io.IOException;

public class TestDocSearch {
	@Test 
	public void testIndex() throws URISyntaxException, IOException {
    Handler h = new Handler("./technical/");
    URI rootPath = new URI("http://localhost/");
    assertEquals("There are 1391 total files to search.", h.handleRequest(rootPath));
	}
	@Test 
	public void testSearch() throws URISyntaxException, IOException {
    Handler h = new Handler(".\\technical\\");
    URI rootPath = new URI("http://localhost/search?q=Resonance");
    String expect = "Found 2 paths:\n.\\technical\\biomed\\ar615.txt\n.\\technical\\plos\\journal.pbio.0020150.txt";
    assertEquals(expect, h.handleRequest(rootPath));
	}
}
```

test.sh
```
set -e
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestDocSearch > Outputs.txt

```
DocSearchServer.java
```
import java.io.File;
import java.io.IOException;
import java.net.URI;
import java.net.URISyntaxException;
import java.net.InetAddress;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.ArrayList;
import java.util.List;
import java.util.Collections;

class FileHelpers {
    static List<File> getFiles(Path start) throws IOException {
        File f = start.toFile();
        List<File> result = new ArrayList<>();
        if(f.isDirectory()) {
            File[] paths = f.listFiles();
            for(File subFile: paths) {
                result.addAll(getFiles(subFile.toPath()));
            }
        }
        else {
            result.add(start.toFile());
        }
        return result;
    }
    static String readFile(File f) throws IOException {
        return new String(Files.readAllBytes(f.toPath()));
    }
}

class Handler implements URLHandler {
    Path base;
    Handler(String directory) throws IOException {
      this.base = Paths.get(directory);
    }
    public String handleRequest(URI url) throws IOException {
       List<File> paths = FileHelpers.getFiles(this.base);
       if (url.getPath().equals("/")) {
           return String.format("There are %d total files to search.", paths.size());
       } else if (url.getPath().equals("/search")) {
           String[] parameters = url.getQuery().split("=");
           if (parameters[0].equals("q")) {
               String result = "" ;
               List<String> foundPaths = new ArrayList<>();
               for(File f: paths) {
                   if(FileHelpers.readFile(f).contains(parameters[0])) {
                       foundPaths.add(f.toString());
                   }
               }
               Collections.sort(foundPaths);
               result = String.join("\n", foundPaths);
               return String.format("Found %d paths:\n%s", foundPaths.size(), result);
           }
           else {
               return "Couldn't find query parameter q";
           }
       }
       else {
           return "Don't know how to handle that path!";
       }
    }
}

class DocSearchServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler(args[1]));
    }
}
```

Server.java
```
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.InetAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url) throws IOException;
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server started at http://" + InetAddress.getLocalHost().getHostName() + ":" + port);
        System.out.println("(Or, if it's running locally on this computer, use http://localhost:" + port + " )");
    }
}
```




The edit required to fix the bug is by going to this section of DocSearchServer.java, and replacing the parameters[0] with parameters[1] instead, this fixes the issue

```
for(File f: paths) {
                   if(FileHelpers.readFile(f).contains(parameters[0])) {
                       foundPaths.add(f.toString());
```


After making the change described, the output obtained in the OUtputs.txt file is as shows:

<img width="397" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/563160ea-db50-4aef-8012-37f17c4a50c4">




#Part 2 Reflection


Something interesting I learned from the second part of this class was how to use VIM, which was something I had no idea existed. I thought it was very cool that what is essentially a text editing tool could be loaded into a command line interface. It is also very cool how it sort of a baseline text editor that can be used on just about any terminal.
