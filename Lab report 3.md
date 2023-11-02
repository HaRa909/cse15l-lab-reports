# Part 1 - Bugs

The method tested was the averageWithoutLowest method that is part of the ArrayExamples.java class.

**A failure-inducing input for the buggy program**
```
double[] input3 = {2,2,2,4,8};

assertEquals(6, ArrayExamples.averageWithoutLowest(input3),.01);
```
The Failure inducing input was the array of 2,2,2,4,8.


**An input that doesn’t induce a failure**

```
double[] input2 = {2,4,6,8,10};

assertEquals(7, ArrayExamples.averageWithoutLowest(input2),.01);
```
The input 2,4,6,8,10, works successfully.


**The symptom, result of testing previously 2 inputs**

![image](https://github.com/HaRa909/cse15l-lab-reports/assets/146860413/c6886785-9ab4-4fd9-acb4-ecae36340740)

**The bug**

Original code, has the bug
```
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

Revised code, fixes the bug

```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    short tracker = 0;
    double sum = 0;
    for(double num: arr) {
      if(num == lowest)
      {
        tracker+=1;
      }
      else{ sum += num; }
    }
       return sum / (arr.length - tracker);
  }
```

The reason why the new code fixes the old code is because when the AverageWithoutLowest method is given an array of numbers that have two or more numbers that fulfill that fit the label of lowest number, and it will throw away all of that number, excluding it from the calculation of the average, with the error being that this code only thinks about what would happen if there is one lowest number rather than multiple. The solution is to track how many times the lowest number comes up and subtract by what the total sum is dividing by, this way the average really does ignore the smallest numbers completely.




# Part 2 - Researching the grep command

**grep - i**
```
$ grep -o "words are" */*.txt


biomed/1472-6882-3-3.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
plos/journal.pbio.0020310.txt:words are
```
```
$ grep -o -i "wOrdS aRe" */*.txt


biomed/1472-6882-3-3.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
plos/journal.pbio.0020310.txt:words are
```



The -o command removes all excess words that don't fit the matching parameters in the grep command. The -o command is useful when you want to only see the words matching against the arguments being placed in the grep command, as seen with how it is used in conjunction with the -i command in the second example.


Source: https://linuxcommand.org/lc3_man_pages/grep1.html.


**grep - n**

```
$ grep -n "words are" */*.txt

biomed/1472-6882-3-3.txt:70:        Plus. Author Keywords are taken from a list of keywords
biomed/gb-2002-3-8-research0040.txt:12:        most other words are used infrequently. When the size of
biomed/gb-2002-3-8-research0040.txt:24:        word against its rank, where words are ranked according to
biomed/gb-2002-3-8-research0040.txt:83:          for the different-length words are nearly identical (
plos/journal.pbio.0020310.txt:7:        about ethics and aesthetics; the latest buzzwords are commodities and consumers.
```
```
$ grep -n "Usage" */*.txt

911report/chapter-13.2.txt:268:                the situation. See FBI report, "American Airlines Airphone Usage," Sept. 20, 2001;
911report/chapter-13.2.txt:376:            56. FBI report, "American Airlines Airphone Usage," Sept. 20, 2001; FBI report of
911report/chapter-13.2.txt:387:                Airlines Airphone Usage," Sept. 20, 2001; FBI report of investigation, interview of
911report/chapter-13.2.txt:391:            58. FBI report, "American Airlines Airphone Usage," Sept. 20, 2001; FBI report of
biomed/1471-2091-2-13.txt:506:          The program Codon Usage Tabulated from GenBank (CUTG)
biomed/1471-2148-2-8.txt:634:        using the Countcodon program available from the Codon Usage
biomed/1471-2334-2-24.txt:532:        Control Group Status variable and the Odds of Condom Usage
biomed/gb-2001-2-4-research0010.txt:790:        CUTG (Codon Usage Tabulated from GenBank) [ 2, 76], which
biomed/gb-2003-4-2-r14.txt:1176:          genomes were obtained from the Codon Usage Database [ 47,
```

The -n command is stating the line number of which the string being matched to comes from. The reason this is useful is because knowing the line number makes it much easier to navigate the files you have found a string match for.

Source: https://linuxcommand.org/lc3_man_pages/grep1.html.


**grep -h**
```
$ grep -h "Usage" */*.txt

               the situation. See FBI report, "American Airlines Airphone Usage," Sept. 20, 2001;
            56. FBI report, "American Airlines Airphone Usage," Sept. 20, 2001; FBI report of
                Airlines Airphone Usage," Sept. 20, 2001; FBI report of investigation, interview of
            58. FBI report, "American Airlines Airphone Usage," Sept. 20, 2001; FBI report of
          The program Codon Usage Tabulated from GenBank (CUTG)
        using the Countcodon program available from the Codon Usage
        Control Group Status variable and the Odds of Condom Usage
        CUTG (Codon Usage Tabulated from GenBank) [ 2, 76], which
          genomes were obtained from the Codon Usage Database [ 47,
```

```
$ grep -h "Hello" */*.txt

    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President: There's been at least three instances here where we've had reports of aircraft approaching Washington-a couple were confirmed hijack. And, pursuant to the President's instructions I gave authorization for them to be taken out. Hello?
```

The -h command removes the file directory from the output, leaving only the contents being searched for inside the file. The use of the command would be to analyze the outputs of the file without caring for where the file’s path is, it would be useful for collecting information in files for analysis.

Source: https://linuxcommand.org/lc3_man_pages/grep1.html.


**grep -o**

```
$ grep -o "words are" */*.txt

biomed/1472-6882-3-3.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
plos/journal.pbio.0020310.txt:words are
```
```
$ grep -o -i "wOrdS aRe" */*.txt

biomed/1472-6882-3-3.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
biomed/gb-2002-3-8-research0040.txt:words are
plos/journal.pbio.0020310.txt:words are
```

The -o command removes all excess words that don't fit the matching parameters in the grep command. The -o command is useful when you want to only see the words matching against the arguments being placed in the grep command, as seen with how it is used in conjunction with the -i command in the second example.


Source: https://linuxcommand.org/lc3_man_pages/grep1.html.


