# Part 1

`The code for StringServer is down below:

import java.io.IOException;
import java.net.URI;
import java.util.ArrayList; // import the ArrayList class

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> foods = new ArrayList<String>(); // Create an ArrayList object
    
    public String handleRequest(URI url) {
         if (url.getPath().equals("/")) {return String.format("Hello");}

            else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                   foods.add(parameters[1]);                      
                    StringBuffer sb = new StringBuffer();
                     sb.delete(0,foods.size());

                for(int i = 0; i < foods.size();i++){
                        sb.append(i+1);
                        sb.append(". ");
                        sb.append(foods.get(i));
                        sb.append("\n");   }
                String output = sb.toString();
             String output1=output.replace("+"," ");
             return String.format("%s\n", output1);
                }
            }
           
        }
         return "404 Not Found!";
        }

        
    }


        

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}


![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/c388b6f9-85d2-4e6b-a62f-8e23f220718d)

The main method in class StringServer and the handleRequest method of Handler class are both called. The relevant argument to the main method would be the port number which is required to start up the server, which is taken by the String args and turned into an integer. The relevant argument to the handleRequest method would be the url. The portnumber value is found in the port integer of the void main method, with it not changing no matter the input once the server is started. Relevant values such as String Arraylist foods, stringbuffer sb, and string output are used in the handleRequest method, with output 1 working as a formatter for output. The /add-message?s=Hello part of the url is the main part that will be changing in the object of the handleRequest method. The values that changed from /add-message?s=Hello would be the Arraylist, which has an element added into it from the part of the url after the /add-message?s=. The "Hello" string is then added to the substring sb, formatted by having a number and period placed before the string followed by newline after the new string is added. The string output will take the stringbuffer converted to a string, while string output2 will not change anything. 


![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/06772093-abd1-40c6-9e0a-97e96a891ebe)


The main method in class StringServer and the handleRequest method of Handler class are both called. The relevant argument to the main method would be the port number which is required to start up the server, which is taken by the String args and turned into an integer. The relevant argument to the handleRequest method would be the url. The portnumber value is found in the port integer of the void main method, with it not changing no matter the input once the server is started. Relevant values such as String Arraylist foods, stringbuffer sb, and string output are used in the handleRequest method, with output 1 working as a formatter for output. The /add-message?s=How are you part of the url is the main part that will be changing in the object of the handleRequest method. The values that changed from /add-message?s=How are you would be the Arraylist, which has an element added into it from the part of the url after the /add-message?s=, with this part being the second element of the arraylist after the “Hello” string. The "How are you" and “Hello” string are then added to the substring sb, formatted by having a number and period placed before the string followed by newline after the new string is added. The string output will take the stringbuffer converted to a string, while string output2 will make sure that the value displayed is correctly showing the spaces between the words of the string “How are you.”

# Part 2

1,2 ![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/ce16920e-5b25-42f4-b356-f0a8853417fd)

3 ![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/f2b7a652-3442-44ef-9158-ad42ae9a5fa9)


# Part 3

The most important things I have learned from labs these past two weeks would be how web servers work and a general idea of how urls work. Another thing I did not know before was the general idea behind how search engines work, with the small project regarding designing one bringing me to a surface level understanding of how they function.



