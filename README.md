# Mini-Project-Basic-Linux-Commands 

# Linux Commands Deep Dive 

A Linux command deep dive involves exploring a range of commands beyond basic file and directory manipulation. It includes understanding advanced options, process management, system information, and more. This exploration helps in effectively managing and troubleshooting a Linux system. 

## What is Linux Command? 

A linux command refers to a program or utility that runs in the command-line interface (CLI), The CLI is a text-based environment where you interact with the system by typing commands. 


- Executables (usually binaries or scripts).

- Found in directories listed in your $PATH.

- Run in a shell like bash, zsh, or fish.

Linux commands are executed by entering text in the Terminal and pressing enter. These commands enable you to perform a wide range of tasks, including installing packages, managing users, manipulating files and directories, configuring system settings, and many more. 

### Examples of Linux commands: 

- ls – Lists the contents of a directory.

- cd – Changes the current directory.

- pwd – Prints the current working directory.

- cp – Copies files or directories.

- mv – Moves or renames files or directories.

- rm – Removes files or directories.

- touch – Creates an empty file.

- mkdir – Creates a new directory.

- cat – Displays the contents of a file.

- man – Shows the manual (help documentation) for a command

The general syntax  of a Linux command is as follows (Try the commands used as example as you read along) 

![General Syntax](./img/01.%20General%20Syntax.png) 

A command may consist of options and parameters, but they are not always required. Here are the key components of a command: 

**CommandName:** This represents the action or task you want to perform using the command. For example if you wish to list files in a folder, you basically use the 'ls' command. 

**Option or Flag:** An option modifies the behaviour of a command. It is typically preceded by a hyphen (-) or double hyphen (--)and can be used to customise the command's functionality. For Example , if I want to show extra information for each listed file. I will run the command 'ls -l' 

**Parameter or Argument:** A parameter provides specific information or data required 
by the command to execute the desired action. For example, to create a new directory (or folder), I will use the 'mkdir' command. The parameter will be the name of the directory in which I will pass to it. 'mkdir photos' willcreate a **photos** directory. 

It's important to note that Linux commands are case sensitive, so their is a need to write them as they are spelled and formatted. 


## Manipulating Files and Directories on Linux 

Manipulating files and directories in Linux is mostly done via the terminal using a variety of built-in commands.

## The **sudo** command 

In Linux some action need special permission to be carried out, like creating files in certain areas or changing important system settings. This is where the sudo command comes into play. "sudo" stands for "superuser do," and it allows you to run commands with the security previleges of another user, typically the superuser or "root." 

## Why Use sudo? 

**Security:** It helps in keeping the system secure by limiting access to powerful commands. 

**Tracking:** It logs who excuted which command, adding a layer of accountability. 

## How sudo Works: 

When you run a command with sudo, the system checks if you're authorized to run that command as root. If you are authorized, you'll typically be asked for your own user password (not the root password). This is to verify that you're allowed to execute commands with elevated privileges. Once you enter the correct password, the command runs with root privileges. 

- If you’re using sudo for the first time in a session, you’ll be asked for your password.

- After you successfully authenticate, your session is typically "cached" for a short period (usually 5–15 minutes). During this time, you don’t need to type your password again for subsequent sudo commands. 

## Creating a Folder with sudo: 

Sometimes you need superuser previleges to create a folder in certain location on your system. Here's how you can do that. 

1. Open the terminal and connect to you linux server using SSH. 

![Terminal to Server (SSH)](./img/02.%20Terminal%20to%20Server%20(SSH).png) 

- **EC2 Dashboard Showing Server Running**

![EC2 Dashboard](./img/03.%20EC2%20Dashboard.png)

2. Try create a folder in a restricted location. For example, let's try to create a folder named "example" in the '/root' directory, which is reserved for the root user. 

![Make Root Directory](./img/04.%20Make%20Root%20Directory.png) 

3. Observe the failure. You will like encounter a permissiom denied error like this 

![Error Encounter](./img/05.%20Error%20Encounter.png) 

This error occur because regular users do not have the necessary permissions to create directories in /'root'.

4. Use sudo to successfully create the folder 

![Successfully Created](./img/06.%20Successfully%20Created.png)

**Pres Enter:** Beacause you now include 'sudo' in the command. It executes successfully without error, in some cases, you may be prompted to provide a password. If it does simply provide trhe password for access to be granted for the creation of the file. The command should succeed without errors. 

**Verify the Folder's Creation:** You can check the folder's existence by listing the contents of '/root' using the 'ls' command. It should it should include the newly created folder in the output on your screen. Though you may need to use sudo again to view the contents of this directory. 

![Verifying](./img/07.%20Verifying.png) 

**Note:** Using sudo gives you significant power over your system, including the ability to change or delete crucial system files. So it's wise to use it carefully and only when necessary. 

**pwd command** 

Use the 'pwd' command to find the path of your current working directory. Simply entering 'pwd' will return the full current path - a path of all the directories that starts with a forward slash (/). For example, '/home/username/'. The pwd command uses the following syntax: 

![pwd Syntax](./img/08.%20pwd%20Syntax.png) 

## The Linux Directory Structure 

The Linux directory structure is a hierarchical organization of files and directories, starting from the root directory (/). It's standardized by the Filesystem Hierarchy Standard (FHS). Here's a breakdown of the main directories you'll find on a typical Linux system. 

The Root Directory ('/') 

At the top of the Linux filesystem hierachy is the root directory, denoted by a single slash '(/)'. Unlike Windows, which uses different drives ('C', 'D':, etc), Linux organises everything starting from this root directory. Under '/', you will find various directories with specific purposes. 

/**bin:** Essential user command binaries (programs) that need to be available to all users are stored here (e.g., ls cp). 

/**etc:** Configuration files for the system can be found here. 

/**home:** Personal directories for users. 

/**root:** The home directory for the root user. 

/**var:** Variable data like logs. 

/**usr:** Secondary hierachy for user data, contains majority of user utilities and applications. 'ls' command to explore them and get some experience navigating Linux.
 
To navigate through the Linux files and directories, use the 'cd' command.

Let's navigate to the root filesystem on your server. Remember, the root filesystem is like the "C:" drive on the Windows. It is the starting point of the folder and it's represented by '/' on Linux. To go to the root filesystem, simply type; to confirm that you are the directory you change to use 'pwd' command to check. 

!['pwd'](./img/09.%20'pwd'..png)

!['cd' and 'ls'](./img/10.%20'cd'%20and%20'ls'.png) 

If I want to navigate to any of the directories in the output, lets say the 'usr', then 'cd' command to enter that directory. 

!['cd'](./img/11.%20'cd'.png) 

It can be seen from the 'usr' that it has '/' prefix. On linux navigation start from the root. 


## Side Hustle Task 1: 

- Create a directory called 'photos' inside '/usr' directory. 

![Create Directory](./img/12.%20Create%20Directory.png) 

- Navigate into the 'photos' directory 

![Navigate Success](./img/13.%20Navigate%20Success.png)

- Create 3 more random directories inside the 'photos' directory. 

![More Directory](./img/14.%20More%20Directory.png)

- Show the newly creted directories on the terminal. 

![Show](./img/15.%20Show.png) 

![Show Parameter](./img/16.%20Show%20Parameter.png)

- Navigate into one of them. 

- Show the full path where you currently are on the screen. 

![Showing Path](./img/17.%20Showing%20Path.png) 

## ls command

The 'ls'command lists files and directories. Running it with a flag or parameter will show the current working directory's content. For in the current the following are shown 

![Other 'ls' Command](./img/18.%20Other%20'ls'%20Command.png) 

## cat command 

'Concatenate' or 'cat' is one of the most frequently used Linux commands. It lists, combines, and writes file content to the standard output (i.e to the terminal console). To run the 'cat' command, type cat followed by the file name and its extension. For example: 

!['cat' Command](./img/19.%20'cat'%20Command.png) 

## cp command 

To copy one file to from the current directory to another enter 'cp' followed by the file name and the destination directory. For example: 

!['cp' Command](./img/20.%20'cp'%20Command.png)

To copy multiple file to a directory enter the names followed by the destination directory: 

![Mupltiple Copy](./img/21.%20Multilple%20Copy.png) 

To copy the coontent of a file to a new file in the same directory, enter 'cp' followed by the source file and the destination file as shown in the image above. 

To copy entire directory, pass the -R flag before typing the source directory, followed the destination directory: 

![Directory Copy](./img/22.%20Directory%20Copy.png) 

## mv command 

The primary use of the 'mv' command is to move and rename files or directories. Additionally it does not produce an output upon execution. 

![Move Command](./img/23.%20Move%20Command.png) 

![To Rename](./img/24.%20To%20Rename.png) 

## rm command 

The 'rm' command is used to delete files within a directory. 

**Caution:** This is very dangerous command as it deletes the files completely. 

To remove a single file 

![To Remove](./img/25.%20To%20Remove.png)

To remove multiple files 

![Multiple Removal](./img/26.%20Multiple%20Removal.png) 

## touch command 

The touch command allows you to create an empty file. For example 

![Create Empty File](./img/27.Create%20Empty%20File.png) 

## find Command 

Use find command to search for a file or files within a specific directory and perform subsequent operations. 

![Find Command](./img/28.%20Find%20Command.png) 