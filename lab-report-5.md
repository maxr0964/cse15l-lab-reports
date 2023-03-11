# Lab Report 5 - Racing Task Script
**Script:**

![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/ScriptScreenshotReal.png)

* To run the script on the remote server, I used the command <code>ssh cs15lwi23ajf@ieng6.ucsd.edu 'bash' < CLDQScript.sh</code>. Since I created a ssh key during lab 7, I don't need to input my password to use ssh. Putting <code>'bash'</code> runs <code>bash</code> on the remote server, and <code>< CLDQScript</code> means that <code>bash</code> reads the script from my local computer.
* Line 1: Declare a CPATH variable so that I don't have to type the entire classpath every time I want to run the junit tests.
* Line 2: Remove the lab7 directory if it already exists on the remote server.
* Line 3: clone the forked <code>lab7</code> repository from my Github account.
* Line 4: <code>cd</code> into the cloned directory.
* Lines 5/6: Compile all necessary files for the <code>JUnit</code> tests and then run the tests.
* Line 7: Use the <code>sed</code> command to edit <code>ListExamples.java</code> automatically. The <code>-i</code> flag tells said to edit in place instead of creating a new file. <code>"43s/index1\ +=\ 1/index2\ +=\ 1/"</code> tells said that it should replace <code>index1 += 1</code> on line 43 with <code>index2 += 1</code>.
* Line 8: Display the contents of <code>ListExamples.java</code> to make sure that <code>sed</code> made the correct changes. I commented this line out after I knew that the command was making the correct changes.
* Lines 9/10: Compile all necessary files for the <code>JUnit</code> tests and then run the tests.
  
 **Output:**
  ![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/ScriptOutput.png)
* The output of the script shows that it clones the repository, runs the <code>JUnit</code> tests on the original files (where one of the tests fails), and then runs the tests again (this time without any failures).
* After running the script once, the <code>up arrow</code> key or <code>ctrl-R</code> command can be used to retrieve <code>ssh cs15lwi23ajf@ieng6.ucsd.edu 'bash' < CLDQScript.sh</code> out of the terminal's history. This means that steps 4-9 of the lab 7 tasks can be completed in as little as two key presses (<code>up arrow</code> and <code>enter</code>).
  
 

  
  
  
