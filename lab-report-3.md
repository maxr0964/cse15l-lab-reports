# Lab Report 3 - Researching Grep
**Function 1 - Counting the Number of Matches**
* To count the number of matches, use <code>grep -c</code>
* For example, counting the number of matches for "Lucayans" in ./written_2:
```
grep -r -l -Z "Lucayans" written_2 | xargs -r -0 grep -c "Lucayans"
```
* This produces the following result:
```
2
```
* This could be useful when there are multiple files that contain the target word, and the file with the most instances of that word is needed. 
*Note: xargs is a command that converts input into argument for the next command. Using xargs passes the results of the first grep as the files to use for the second grep, and the -Z and -0 flags make sure that xargs doesn't use whitespace chars as delimiters in case filenames have spaces in them.*

* Another example is counting the number of <code>.txt</code> files in ./written_2:
```
find written_2 | grep -c ".txt"
```
* This produces the following result:
```
224
```
Sources: 
https://www.gnu.org/software/grep/manual/grep.html
https://www.man7.org/linux/man-pages/man1/xargs.1.html

**Function 2 - Files Without Match
* While <code>-l</code> returns the names of the input files that would normally print output, <code>-L</code> returns the names of files that wouldn't have printed any output.
* For example, searching for files without the word "they":
```
grep -r _l "they" written_2"
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
* Source: https://www.gnu.org/software/grep/manual/grep.html


