1. 
<img width="620" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/2fd87a87-e372-46d1-bbf5-f5101bf2bfb4">
<img width="603" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/95ef1431-93a8-41ee-aa2c-838b9e7962ff">


`ssh cs15lfa23iq@ieng6.ucsd.edu <enter>`

This command was used to ssh into the remote computer ieng6.



2.
<img width="578" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/6f84a828-f060-4d7c-960d-a6540d617d6e">


`git clone git@github.com:HaRa909/lab7.git <enter>`

This command clones the forked repository that can be later pushed to.

3. 
<img width="491" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/d3387840-b6da-4694-9d54-08f9013bfb49">

`bash test.sh <enter>`

Command ran, the command simply runs through a script explaining there is an issue with ListExamples.java file.




4. 


<img width="694" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/b7c93d4a-ca3a-4e8f-82fc-a74cd85dff13">
<img width="685" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/96491735-dfe1-4c12-8b0e-d97de2aa74dc">

`vim ListExamples.java file`
Command puts us in the vim interface

`<shift+g>`
Command will move curser to the end of the file. This was useful because the problem with the file was located at the end of the java file.

`<6k> <enter>`
Command will move the curser up 6 lines, the reason being was because that was where the line of interest was. The 6 ran the command that moves up a line, k, 6 times.

`<shift+e>`
Command will move the curser to the end of the first word, where the issue with the code was, where the 1 needed to be changed into a 2.

`<x>`
Command will delete the character the curser is on, which was done by the last command, this is the first part of fixing the bug with the variable name.
  
`<a> <enter>`
Command will put Vim into insert mode, allowing us to add to the java file now.
  
`<2>`
This is text that will be inserted via vim's insert mode, we now fix the bug by putting in the correct number for the variable.

`<esc>`
Command will exit insert mode and put us in normal mode, we are done with our edits.

`<:wq> <enter>`
Command will write our changes onto the java file and then quit vim, bringing us back to the terminal.


5.
<img width="355" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/6c75819d-b5ab-4fda-b1d0-97627c4acf7c">

`bash test.sh <enter>`

command ran, the command simply runs through a script explaining that the Java file now matches with the testing, meaning the changes made were successful.

6. 


<img width="575" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/1345834d-75c2-4e89-8fe0-6b4b7ae3d584">


`git add ListExamples.java <enter>`

This will add the file we just saved and editted on our remote computer, ListExamples.java, and add it to a list of file we will prepare to commit and push onto the github repository.

`git commit <enter>`

This will confirm all the files we used `git add` on and prepare it for the next command. THe command puts us in a vim terminal. Over here we can either add commit messages or not. In the case of wanting to do commit messages, do **<a> `enter`** for insert mode, then type in whatever it is you want to leave as a message, then click **<esc>** to go into normal mode, then type in **<:wq> `enter`** to save and exit the commit message, which will exit vim and put you back in the terminal. If you don't want to go into vim, you can use the -m command with commit like git commit -m "comment" or you can simply exit without putting any messages in.

`git push <enter>`

This will push the committed changes to the github repository, successfully updating to the fixed product.
