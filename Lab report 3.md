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

**grep -h**

**grep -o**
