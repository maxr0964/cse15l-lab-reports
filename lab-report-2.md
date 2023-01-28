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
-visting the url [!http://localhost:4000/add-message?s=SYKE!!!](http://localhost:4000/add-message?s=SYKE!!!) calls StringServer's handleRequest method with the  arguments <code>/addMessage?s=SYKE!!!</code>. Since the url contains the string <code>"/addMessage"</code>, the part of the string after the <code>=</code> is added to <code>allStrings</code> with a newline, and then <code>allStrings</code> is returned and displayed by <code>Server.java</code>.

**Part 2: Bugs**


**Part 3: Reflection**
