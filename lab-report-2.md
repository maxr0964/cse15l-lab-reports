# Lab Report 2
**Part 1: String Server**
* My code for the StringServer web server:
![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/webServerCode.png)
* Adding the first message:

![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/firstAddMessage.png)
-Running <code>java StringServer 4000</code> calls StringServer's main method, which starts the server
 using port 4000. Next, when visting the url [!http://localhost:4000/add-message?s=seeYaLater](http://localhost:4000/add-message?s=seeYaLater), StringServer's handleRequest method is called with the  arguments <code>/addMessage?s=seeYaLater</code>. Since the url contains the string <code>"/addMessage"</code>, the part of the string after the <code>=</code> is added to <code>allStrings</code> with a newline, and then <code>allStrings</code> is returned and displayed by <code>Server.java</code>.
* Adding the second message:

![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/secondAddMessage.png)
-Visting the url [!http://localhost:4000/add-message?s=SYKE!!!](http://localhost:4000/add-message?s=SYKE!!!) calls StringServer's handleRequest method with the  arguments <code>/addMessage?s=SYKE!!!</code>. Since the url contains the string <code>"/addMessage"</code>, the part of the string after the <code>=</code> is added to <code>allStrings</code> with a newline, and then <code>allStrings</code> is returned and displayed by <code>Server.java</code>.

**Part 2: Bugs**
* Bug: <code>ArrayExamples.reversed()</code> doesn't always reverse an array correctly.
* Input that doesn't induce failure:
```
 @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
 }
 ```
 * Failure-inducing input:
```
  @Test
  public void testReversed() {
       int[] input2 = {1, 2, 3, 4};
       int[] input2reversed = {4, 3, 2, 1};
       assertArrayEquals(input2reversed, ArrayExamples.reversed(input2));
  }
  ```
  * Symptom as a result of running those tests:
  ![Image](https://raw.githubusercontent.com/maxr0964/cse15l-lab-reports/main/runningTests.png)
  *Note: I put both of the tests detailed above into one method to make running them easier.*
  
  * The bug (before and after fix):
  -Before:
  ```
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
    return arr;
  ```
  -After:
  ```
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  ```
  The original code sets the element at <code>i</code> of <code>arr</code> to <code>arr[arr.length - i - 1]</code> instead of <code>newArray</code>, so only the first half of the array is reversed. It also returns <code>arr</code> instead of <code>newArray</code>. The fixed code addresses both of these issues by changing <code>arr[i]</code> to <code>newArray[i]</code> and then returning <code>newArray</code>.
 
 



**Part 3: Reflection**

One thing I learned from last week's lab was that the port number can be decided by the programmer. When I was an intern, I was primarily writing webcode, so I did a lot of testing using <code>localhost</code>. I thought the port number was always automatically generated, but it turns out the programmer can specify it. I also learned some strategies for designing tests in this week's lab. For example, for <code>averageWithoutLowest</code> it was important to test arrays that had no lowest value, such as <code>{1, 1, 1, 1}</code>.
