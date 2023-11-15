1. 
<img width="620" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/2fd87a87-e372-46d1-bbf5-f5101bf2bfb4">
<img width="603" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/95ef1431-93a8-41ee-aa2c-838b9e7962ff">


**ssh cs15lfa23iq@ieng6.ucsd.edu** `enter`

This command was used to ssh into the remote computer ieng6.



2.
<img width="578" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/6f84a828-f060-4d7c-960d-a6540d617d6e">


**git clone git@github.com:HaRa909/lab7.git**

This command clones the forked repository that can be later on pushed to.

3. 
<img width="491" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/d3387840-b6da-4694-9d54-08f9013bfb49">

**test.sh** command ran, the command simply runs through a script explaining there is an issue with ListExamples.java file




4.
<img width="694" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/b7c93d4a-ca3a-4e8f-82fc-a74cd85dff13">
<img width="685" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/96491735-dfe1-4c12-8b0e-d97de2aa74dc">


**<shift+g>** 
Command will move curser to the end of the file. This was useful because the problem with the file was located at the end of the java file.

**<6k> `enter`**
Command will move the curser up 6 lines, the reason being was because that was where the line of interest was. The 6 ran the command that moves up a line, k, 6 times.

**<shift+e>** 
Command will move the curser to the end of the first word, where the issue with the code was, where the 1 needed to be changed into a 2.

**<x>** 
Command will delete the character the curser is on, which was done by the last command, this is the first part of fixing the bug with the variable name.
  
**<a>** 
Command will put Vim into insert mode, allowing us to add to the java file now.
  
**<2>** 
This is text that will be inserted via vim's insert mode, we now fix the bug by putting in the correct number for the variable.

**<esc>**
Command will exit insert mode and put us in normal mode, we are done with our edits.

**<:wq> `enter`** 
Command will write our changes onto the java file and then quit vim, bringing us back to the terminal.


5.
<img width="355" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/6c75819d-b5ab-4fda-b1d0-97627c4acf7c">

**test.sh** command ran, the command simply runs through a script explaining that the Java file now matches with the testing, meaning the changes made were successful.

6. 
<img width="341" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/26fd1f77-513f-4079-ad67-6ca2cbbc3a60">

**git add ListExamples.java**

**git commit**

**git push**
