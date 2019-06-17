## Issue
Today when I tried to pull code from one of my repository, an error happened and it prevented me from get codes from the repository. The error looked like that  
![image](https://github.com/fengandzhy/Blog/raw/master/Images/git/article02/1.png) 
## Reason
This is because there was another git process running in the repository when I tried to pull code from it, the two processes confilct with each other. 
## Solution
close another process and run rm -f ./.git/index.lock in the bash shell command. 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/git/article02/2.png) 



