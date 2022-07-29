# Linux commands
## Basic commands
Open windows Command Promt into current directory
```Bash
$ start
```
Open windows directory/ file system into current directory
```Bash
$ start .
```
Open PhpStorm editor
```Bash
$ phpstorm64
```
Open current folder into PhpStorm
```Bash
$ phpstorm64 .
```
Create alias. Go to home directory and execute the command. I make alias "storm" for the "phpstorm64".This can be used for any command in git
```Bash
$ echo alias storm=\'phpstorm64\' >> .bashrc
```
Opening Visual Studio Code editor
```Bash
$ code
```
Show current directory
```Bash
$ pwd
```
Clear the screen
```Bash
$ clear
```
Show all files (including the hidden ones and their permissions)
```Bash
$ ls -la 
```
Create new directory with name "netauto"
```Bash
$ mkdir netauto
```
Enter into the directory with name "netauto"
```Bash
$ cd netauto
```
Exit from directory
```Bash
$ cd ..
```
Rename folder "initializer" with name "web-project"
```Bash
$ mv initializer web-project
```
Create a new file (miki.txt)
```Bash
$ touch miki.txt 
```
Read what is inside the text file (miki.txt)
```Bash
$ cat miki.txt
```
Copy file "example.txt" into new file "example1.txt"
```Bash
$ cp example.txt example1.txt
```
Open "Vim" text editor. (After you enter in the vim text editor you need to press "i" so you can write something or editing. When you finished with everything you need to press "esc" and then you can save the file and exit by pressing ":wq")
```Bash
$ vi miki.txt 
```
Unzip file that is in "downloads" folder in "home" directory
```Bash
$ unzip ~/downloads/initiealizer.zip
```
Remove file (myfile.txt)
```Bash
$ rm myfile.txt
```
Remove directory (letters) and all the files inside
```Bash
$ rm -rf letters/
```

## SSH Comunication with the server
Connect to the server (Enter password)
```Bash
$ ssh cybermickey@cybermickey.com
```
Exit from the server
```Bash
[server $] exit 
```
Find information and ip address of the remote server
```Bash
$ ifconfig 
```
Copying file "hello.sh" from the local machine to remote server "codebind@192.168.245.141" into the folder "/home/codebind". First we need to navigate where the folder is then we write
```Bash
$ scp hello.sh codebind@192.168.245.141:/home/codebind 
```
Copying all files from "test" folder from the local machine to remote server "codebind@192.168.245.141" into the folder "/home/codebind". First we need to navigate where the folder is then we write
```Bash
$ scp -r test codebind@192.168.245.141:/home/codebind 
```
Copying file "miki.txt" from the remote server "codebind@192.168.245.141:/home/codebind" into the folder "/home/desktop". First we need to navigate where the folder is then we write
```Bash
$ scp codebind@192.168.245.141:/home/codebind/miki.txt  /home/desktop/ 
```
If port of the remote server is different then 22 (in this case is 1234) -P 1234, and if we like to connect with the public key to serever private key we add (-i /path/), in our case the publick key is in the folder /home/keys/:
```Bash
$  scp codebind@192.168.245.141:/home/codebind/miki.txt  /home/desktop/ -P1234 -i /home/keys/
```
