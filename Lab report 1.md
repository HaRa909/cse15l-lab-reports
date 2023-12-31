
# Examples of using the command with no arguments.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/24850c81-e0ad-44a4-b9a4-7c5b637932eb)

cd: The change directory command requires a directory input to do anything, otherwise it defaults to the home directory, hence why nothing happened when there was no directory specified. There is no error as the command is working exactly as it is meant to.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/f4103566-3526-4778-bc22-ad135040f692)

ls: the ls command lists files and directories on what is essentially the root, the only files that show up upon this command are going to be the ones at the root like Lecture1 and lab1, due to them being the master folders. There is no error as the comand worked exactly as it was meant to.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/241b9d7f-b95e-448a-9484-cacfef37fc89)

cat: the cat command reads data in a file, and due to the lack of a file selected, nothing happens. There is somewhat of an error where the output, requiring the exit command of control v to escape from it due to the fact the cat command needs something to read, the complete emptiness in parameters causes a problem.

# Examples of using the command with a path to a directory as an argument.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/dfd08f0a-8fc3-4a06-bcfa-3e5baa9d9100)

cd: The change directory command is given a directory to go to, the lecture1 directory, and so changes the location to the lecture1 directory. No error occurs as a result.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/e58e89e8-4d85-4e87-b89c-78d36eae579b)

ls: the lecture1 directory contains Hello.class, Hello.java, messages, and README in it, making it so that when the ls command is carried out, all files and directories inside the lecture1 folder are displayed. No error occurs here.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/ad9c5a9c-d447-48c7-99ce-fb6f5471dfa2)

cat: Due to the fact the cat command is carried out in a directory, it displays the "Is a directory" message because of the lack of files to read. This could be seen as an error due to the lack of cat doing what it is designed to do, read files.

# Examples of using the command with a path to a file as an argument.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/b25d9c0a-f035-43bb-9b5e-f6ef2aaeed35)

cd: Using the cd command on an actual file doesn't work, hence why the error "Not a directory" is displayed, cd is meant to navigate directories and not files.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/160fca75-ebbc-47cd-b44f-8cb07a12df3a)

ls: The ls command is meant to display files underneath a directory, when there is an actual file that is being read the syste, essentially confirms that the file is indeed there. There is no error going on wth the input, and ls is returning what was typed in because the input was indeed a file.

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/3aa9537f-c312-43bd-8127-5fcbeeeda40f)

cat: The cat command attempts to read a file and dsiplay its contents through text, hence why this time the command was succesful. There was no error like the previous two times becasue the file path actually led to something it could read, a text file.



