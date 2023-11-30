#1. Symptom and description


<img width="482" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/ac414c06-e6b1-49d0-90ad-356d051aa78d">

.
<img width="353" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/edfb2e17-fb15-4261-a1bc-f018deb39742">

When I test my code's output, I get a list of every single file in the system. I'm thinking that the issue comes from the searching the failure inducing input is supposed to do, where instead of listing only the files that satisfy the search condition of the string, the only files that should be displayed are the files containing the string but everything shows up instead.

This is the failure inducing input

<img width="696" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/2c9533d0-a7c2-4f6b-9439-b110b14dfdad">


#2. TA response

Check to see what your String is being compared to in your code. I would recommend printing statements of whatever variables you are comparing with to see what it is that fulfills the condition of those files being added to the output. 


#3. What Student got by trying that

<img width="485" alt="image" src="https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/c0bdb463-c7e8-4826-a3d7-31660700100c">

The bug is coming from the fact that instead of the correct string being compared against for the program, the string "q" is compared, and every file with the letter q in it is then listed, and because almost every file has that single letter, all of them pop up in the output. This comes from how the parameters string array, an array composed of two elements, one part being q and the other part being the actual string after the query, which is parameters[1] that equals string "Resonance", while parameters[0] is just the string "q".





#4. All info needed for setup

file/directory structure
.\technical\biomed\ar615.txt
.\technical\plos\journal.pbio.0020150].txt

technical
-  biomed
   * ar615.txt
-  plos
   * journal.pbio.0020150.txt




