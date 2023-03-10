# Lab Report 1
**Step 1: Installing VScode**
* To install VSCode, visit this link: [Visual Studio Code](https://code.visualstudio.com/) and follow the install instructions for your OS.
*Note: I didn't do this step during the lab, as I already had VSCode installed on my computer.*
![Image](https://github.com/maxr0964/cse15l-lab-reports/blob/8ce0f13db117c942d288430a8fd41efd2cf37cda/Vscode%20after%20install.png?raw=true)
VSCode window after installation

**Step 2: Remotely Connecting**
* If you're using windows, this step requires you to install git. Follow the instructions at this link: [Git for Windows](https://gitforwindows.org/)
* After installing git, set the terminal in VScode to use git bash by opening the command palette with control-shift-p and selecting Git Bash as the default profile
* Next, connect to the <code>ieng6</code> server by typing: <code>ssh cs15lwi23zz@ieng6.ucsd.edu</code> (make sure to use your cs15l account instead of zz).
* If it's your first time connecting to the server, type yes and enter your password when prompted.
*Note: I didn't install git during the lab, as I already had it on my computer.*
![Image](https://github.com/maxr0964/cse15l-lab-reports/blob/8ce0f13db117c942d288430a8fd41efd2cf37cda/connected%20with%20login.png?raw=true)
Connecting to the server

**Step 3: Running Some Commands**
* Now, try running some of these useful commands: <code>cd ~</code>, <code>ls -lat</code>, <code>ls -a</code>, <code>ls (directory)</code>, <code>mkdir</code>
* To log out of the server, use Ctrl-D or use <code>exit</code>
![Image](https://github.com/maxr0964/cse15l-lab-reports/blob/8ce0f13db117c942d288430a8fd41efd2cf37cda/ran%20some%20commands.png?raw=true)
Running some commands

One thing I learned by running <code>mkdir</code> and <code>rmdir</code> is that I can create directories directly on the remote computer without having to <code>scp</code> them from my local machine. I also learned that even though other people also use this computer, my account has its own home directory that other users can't directly access. 



