# Lab Report 3 - Researching Grep
**Function 1 - Counting the Number of Matches**
* To count the number of matches, use <code>grep -c</code>
* For example, counting the number of matches for "Lucayans" in <code>./written_2</code>:
```
grep -r -l -Z "Lucayans" written_2 | xargs -r -0 grep -c "Lucayans"
```
* This produces the following result:
```
2
```
* This could be useful when there are multiple files that contain the target word, and the file with the most instances of that word is needed. 
*Note: xargs is a command that converts input into argument for the next command. Using xargs passes the results of the first grep as the files to use for the second grep, and the -Z and -0 flags make sure that xargs doesn't use whitespace chars as delimiters in case filenames have spaces in them.*

* Another example is counting the number of <code>.txt</code> files in <code>./written_2</code>:
```
find written_2 | grep -c ".txt"
```
* This produces the following result:
```
224
```
* This is useful because it does the same thing we did in lab when counting the number of <code>.txt</code> files, but in fewer steps (without <code>wc</code>). 
* Sources: 
[grep](https://www.gnu.org/software/grep/manual/grep.html)
[xargs](https://www.man7.org/linux/man-pages/man1/xargs.1.html)

**Function 2 - Files Without Match**
* While <code>-l</code> returns the names of the input files that would normally print output, <code>-L</code> returns the names of files that wouldn't have printed any output.
* For example, searching for files without the word "they":
```
grep -r -L "they" written_2"
```
* This produces the following result:
```
written_2/non-fiction/OUP/Castro/chQ.txt
written_2/non-fiction/OUP/Castro/chW.txt
written_2/travel_guides/berlitz1/HandRHongKong.txt
written_2/travel_guides/berlitz1/HandRIbiza.txt
written_2/travel_guides/berlitz1/HandRIstanbul.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
written_2/travel_guides/berlitz1/HandRJerusalem.txt
written_2/travel_guides/berlitz1/HandRLakeDistrict.txt
written_2/travel_guides/berlitz1/HandRLasVegas.txt
written_2/travel_guides/berlitz1/HandRLisbon.txt
written_2/travel_guides/berlitz1/HandRLosAngeles.txt
written_2/travel_guides/berlitz1/HandRMadeira.txt
written_2/travel_guides/berlitz1/HandRMallorca.txt
written_2/travel_guides/berlitz1/IntroIstanbul.txt
written_2/travel_guides/berlitz1/WhatToFrance.txt
written_2/travel_guides/berlitz1/WhereToHawaii.txt
written_2/travel_guides/berlitz2/Berlin-History.txt
written_2/travel_guides/berlitz2/Cuba-History.txt
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt
```
* Another example, searching for files without "time" and piping the results into <code>wc</code>
```
grep -r -L "time" written_2 | xargs wc -w
```
* This produces the following result:
```
 2163 written_2/travel_guides/berlitz1/HandRHawaii.txt
  152 written_2/travel_guides/berlitz1/HandRHongKong.txt
   86 written_2/travel_guides/berlitz1/HandRIbiza.txt
  121 written_2/travel_guides/berlitz1/HandRIstanbul.txt
  179 written_2/travel_guides/berlitz1/HandRJerusalem.txt
  202 written_2/travel_guides/berlitz1/HandRLakeDistrict.txt
  201 written_2/travel_guides/berlitz1/HandRLasVegas.txt
  129 written_2/travel_guides/berlitz1/HandRLisbon.txt
  191 written_2/travel_guides/berlitz1/HandRMallorca.txt
  248 written_2/travel_guides/berlitz1/WhatToFrance.txt
  351 written_2/travel_guides/berlitz1/WhatToHawaii.txt
  309 written_2/travel_guides/berlitz1/WhereToHawaii.txt
 3454 written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt
 7786 total
 ```
 * This use of grep could be useful if you're dealing with a large amount of very similar files, and you need to find files with some specific words missing.
* Source: [grep](https://www.gnu.org/software/grep/manual/grep.html)

**Function 3 - Extended Regular Expressions**
* Using the <code>-E</code> flag with grep allows the use of parentheses to apply operators to groups of patterns.
* For example, searching for files that contain 'beach' and 'ocean' or 'ocean' and 'cliff'.
```
grep -E -r -w -l '(beach.*ocean)|(ocean.*cliff)' written_2
```
* This produces the following result
```
written_2/travel_guides/berlitz2/Algarve-Intro.txt
written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/California-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/Cancun-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-WhereToGo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
```
* Another example, searching for "food" and "good" or "food" and "local"
```
grep -E -r -l -w '(beach.*ocean)|(ocean.*cliff)' written_2
```
* This produces the following result:
```
written_2/non-fiction/OUP/Castro/chA.txt
written_2/non-fiction/OUP/Rybczynski/ch1.txt
written_2/travel_guides/berlitz1/HandRIsrael.txt
written_2/travel_guides/berlitz1/WhatToDublin.txt
written_2/travel_guides/berlitz1/WhatToIbiza.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt
written_2/travel_guides/berlitz2/Berlin-WhatToDo.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-WhereToGo.txt
written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt
```
* This could be useful if searching for files that contain one combination of patterns but not another (using the not operator, <code>^</code>.
* Source: [grep](https://www.gnu.org/software/grep/manual/grep.html)
 
**Function 4: Only Matching**
* Using the -o flag will print only the matching part of matched lines. 
* For Example: searching for "Lucayans" in <code>./written_2</code>:
```
grep -r -l -Z "Lucayans" written_2 | xargs -r -0 grep -o -n  "Lucayans"
```
* This produces the following ouput:
```
6:Lucayans
7:Lucayans
```
*Note: I also added <code>-n</code> flag to print the line numbers*
* Another example: searching for "Bahamas"
```
grep -r -l -Z "Bahamas" written_2 | xargs -r -0 grep -o -n  "Bahamas"
```
* This Produces the following output:
```
written_2/travel_guides/berlitz1/WhatToFWI.txt:111:Bahamas
written_2/travel_guides/berlitz2/Bahamas-History.txt:6:Bahamas
#bunch of output in the same format that I removed
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt:343:Bahamas
```
*Note: the output was really long so I cut most of it out.
* This could be useful if you need the line numbers of a specific word, but don't want <code>grep</code> to print the entire line.
* Source: [grep](https://www.gnu.org/software/grep/manual/grep.html)



