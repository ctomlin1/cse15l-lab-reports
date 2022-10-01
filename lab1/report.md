## 1. Installing VScode
- Download and install VScode if you haven't already: https://code.visualstudio.com/
- If you do everything correctly it should look like this when you launch the app:
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/installingvscode.png)
## 2. Remotely Connecting
- Connect to the remote host using the command ```$ ssh cs15lfa22ny@ieng6.ucsd.edu```
- Enter the password if needed and you should get a result like this:
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/remotelyconnecting.png)
## 3. Trying Some Commands
- Run some commands to familiarize yourself with remote hosting and make sure everything is working
- Below are a few examples:
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/tryingsomecommands.png)
## 4. Moving Files with ```scp```
- For this example I made a file called ```WhereAmI.java``` and moved it to the remote host
- This program displays some basic information about the computer on which it is run
- I used the command ```scp WhereAmI.java cs15lfa22ny@ieng6.ucsd.edu:~/``` to move the file, then compiled and ran it on the remote host and got the following result:
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/scp.png)
## 5. Setting an SSH Key
- SSH keys can really speed up the process of remote hosting because they remove the step of typing your password every time you log into the server
- Run the commands shown in the image below to create an SSH key and copy it to the server
- I wasn't prompted to enter a password when I logged in at the end, which means the SSH key worked
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/sshkey.png)
## 6. Optimizing Remote Running
- Along with SSH keys, there are countless shortcuts to speed up the process of remote hosting
- In the image below I made a local edit to ```WhereAmI.java```, then copied it to the remote server and ran it in the most efficient way I could think of
- I still have a lot to learn about optimization and for all I know this could be embarrasingly inefficient
![](https://ctomlin1.github.io/cse15l-lab-reports/lab1/images/optimizingremoterunning.png)
