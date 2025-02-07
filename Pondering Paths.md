# Pondering Paths 

#### Root is a way to access different files and directories from the Linux file system. All files are located in Directories. Directories can contain files and directories inside them. You can access files and directories through these paths. Paths can be accessed by *"/"*. Every path is demarcated by slash.

## The Root
#### To access the root directory, we have to invoke the  absolute path; for that, we have to do */*. For the flag we have to do : **/pwn**

## Program and Absolute Paths 
#### A root directory will contain multiple directories and files in itself. To access a root directory, we should use the /directoryname command. After that, we should use another*"/"* command and then the specific file or folder name to access it. So, for this challenge we should do: **/challenge/run**

## Position thy self
#### Another way of skipping from one directory to another is to us the **_cd_** command. The cd means Changing directory. we can use **~**, which shows the current path that your shell is located at. For the task, we have to first run **_/challenge/run_** after which it will tell that you are not in **etc** directory and then u have to cd into etc directory after which you have to run **_/challenge/run_** inorder to get the flag.

## Position elsewhere
#### Same as the previous challenge

## Position yet elsewhere
#### Same as the previous challenge, but the specific path is **_/var_**

## implicit relative paths, from /
#### Now knowing about absolute paths, we know that If you put in absolute paths everywhere, then it really doesn't matter what directory you are in. 
#### However, current working directories (cwd) are necessary for relative paths 
A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your cwd is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
If my cwd is /tmp, then a relative path to the file is a/b/my_file.
If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /.
For this challenge, we have to first cd into **_/_** and then applying the concept of relative path we have to type : **_challenge/run_**.

## explicit relative paths, from/
#### This image explains explicit relative paths in a Linux-like file system. Here’s a breakdown of the concepts:

    ### **Implicit Directory Entries**
    In Linux and many other operating systems, every directory has two special entries:
    1. `.` (dot) → Refers to the **current directory**.
    2. `..` (double dot) → Refers to the **parent directory**.
    
    ### **Absolute Paths**
    An absolute path starts from the root (`/`) and specifies the full location of a directory or file. The following absolute paths listed in the image are **identical**:
    - `/challenge`
    - `/challenge/.` → Refers to the same directory (`.` means "current directory").
    - `/challenge/./././././././.` → Multiple dots (`.`) still refer to the same directory.
    - `/./././challenge/././` → Any number of `.` components do not change the path.
    
    ### **Relative Paths**
    A relative path specifies a location starting from the current working directory instead of the root. The following relative paths are **equivalent**:
    - `challenge` → Directly specifying the directory.
    - `./challenge` → Adding `.` (current directory) does not change the path.
    - `../../challenge` → Navigating up levels (`..`) before reaching `challenge` still resolves to the same place if within the same hierarchy.
    - `challenge/.` → Adding `.` at the end still refers to `challenge`.
    
    ### **Summary**
    The image demonstrates that:
    - Using `.` in a path has no effect because it refers to the same directory.
    - Using `..` moves up one level in the directory hierarchy.
    - Paths that include multiple `.` or `..` elements may look complex but resolve to the same location when simplified.
#### In this challenge for the flag we have to cd into **_/_** and then after that access a relative path as **_./challenge/run_**

## Implicit Relative Paths
#### In this challenge we learn to use **.** more. so here to access the flag we have to cd into challenge using: **_cd /challenge_** and then explicitly do run as : **_./run_**

## Home sweet home 
    ####Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.
    
    Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:
    
    hacker@dojo:~$
    The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:
    
    hacker@dojo:~$ echo LOOK: ~
    LOOK: /home/hacker
    hacker@dojo:~$ cd /
    hacker@dojo:/$ cd ~
    hacker@dojo:~$ cd ~/asdf
    hacker@dojo:~/asdf$ cd ~/asdf
    hacker@dojo:~/asdf$ cd ~
    hacker@dojo:~$ cd /home/hacker/asdf
    hacker@dojo:~/asdf$
    Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.
    
    Fun fact: cd will use your home directory as the default destination:
    
    hacker@dojo:~$ cd /tmp
    hacker@dojo:/tmp$ cd
    hacker@dojo:~$
#### In this challenge, we have to write an argument into the home directory, which is /home/hacker, which is abbreviated to ~ so now applying all the constraints we should do : **_/challenge/run ~/x_** inorder to get the flag.
