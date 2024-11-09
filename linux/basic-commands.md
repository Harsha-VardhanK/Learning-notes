
Command Prompt
You can configure the command prompt to show whatever you want, such as the hostname , date or time.
It is currently configured to show the current working directory. The ~ symbol here represents the home directory
Command and Arguments
To interact with the linux system using the shell, a user has to type in commands
When a command is run it executes a program to achieve a specific task.
For example: The echo command is used to print a line of text on the screen.
                        $ echo 
An argument acts as an input to command
For example: To print a hello message type echo hello command.
                        $ echo hello
There are several commands that can work without an argument too.
For example: Type in the command called uptime, this is used to print information about how long a system has been running for since the last reboot along with the other information (This command doesn't need an argument)
                        $ uptime 
A command can also have options that modify its behaviour in some predetermine way. The option also sometime referred to as a switch or a flag
For example: To print a same word hello but without a trailing line, use echo command with -n flag.
                        $ echo -n hello



Command Types
Command types in linux can be generally categorized in two types

Internal or Built-in Commands
Internal commands are part of the shell itself. It come bundled with it, there are in total about 30 such commands
For example: echo, cd, pwd, set e.t.c.
External Commands
External commands on the other hand are binary programs or scripts which are usually located in distinct files in the system. They either come with pre-install with the distribution package manager or can be created or installed by the user
For Example: mv, date, uptime, cp e.t.c.
To determine a command is internal or external, use type command



To print the present working directory. Run pwd command

$ pwd
To see the contents of the directory. Run ls command

$ ls 
To make (or) create a directory. Run mkdir command

$ mkdir Asia
To make (or) create multiple directories. Run mkdir command followed by <directory_name1> <directory_name2> .. <directory_nameN>

$ mkdir Europe Africa America
To change a directory from the current directory. Run cd <directory_name>

$ cd Asia
To recursively created directories. Run mkdir -p <directory_name1>/<sub_directory_of_name1>

$ mkdir -p India/Mumbai
To go back to one directory up. Run cd ..

$ cd ..
To go back directly to a home directory of the current user from any location in the system. Run cd

$ cd


Alternative to the cd is the pushd\popd command. To change directory using pushd, run pushd <directory_name>

$ pushd /etc
You can change to subdirecties under /etc as many times as you wish

$ pushd /var
$ pushd /tmp
$ pwd
/etc/var/tmp
To return back to origin directory(say your home directory), use the popd command

$ popd


To move file or directory. Run mv <source> <destination> command

$ mv /home/michael/Europe/Morocco /home/michael/Africa/ (Absolute path)
$ mv Europe/Morocco Africa/ (Relative Path)
To rename a directory. Run mv <oldname> <newname> command

$ mv Asia/India/Munbai Asia/India/Mumbai
To copy a file to a directory. Run cp <filename> <destination_directorypath> command

$ cp Asia/India/Mumbai/City.txt Africa/Egypt/Cairo
To delete a file from a directory. Run rm /path/<filename> command

$ rm Europe/UK/London/Tottenham.txt
To copy a directory recursively. Run cp -r <sourcepath> <destinationPath> command

$ cp -r Europe/UK Europe/UnitedKingdom
To print the content of a file. Run cat /path/to/<filename> command

$ cat Asia/India/Mumbai/City.txt
To add a content to a file with cat(redirect) . Run cat > /path/to/<filename> command

$ cat > Africa/Egypt/Cairo/City.txt
  Cairo
  `Type Ctrl + d from keyboard`
To create an empty file. Run touch /path/to/filename command

$ touch /home/michael/Asia/China/Country.txt
To see the content of a file in a scrollable manner. Run more /path/to/filename command <-- not recommended for large files

$ more new_file.txt
To see the content of a file and navigate throught the file. Run less /path/to/filename command

$ less new_file.txt
To get the long list of files and directories. Run ls -l command

$ ls -l
To list all files including the hidden. Run ls -la command

$ ls -a
To list all the files in the order they were modified. Run ls -lt command

$ ls -lt
To list all the files form oldest to newest. Run ls -ltr command

$ ls -ltr


If you are new to using linux or bash shell or if you are not sure which command does what, there are few commands in bash that can help get started.
Lets take a look of those
First command is whatis , this command will displays a one line description of a command does.

Syntax: whatis <command>

$ whatis date
Most of the commands internal or external come bundled with man pages which provides information about the command in detail (with examples, usecases and with command options)

Syntax: man <command>

$ man date
Several commands will provide -h or --help to provide users with the options and usecases available in a command

$ date -h
$ date --help
To search through the man page names and descriptions for instances of the keyword use apropos. This is useful if you want to look for all commands within the system that contains the specifc keyword.

Syntax: apropos <keyword>

$ apropos modpr


--------------------------------------------------
To check the home directory for a particular user say bob

$ grep bob /etc/passwd | cut -d ":" -f6
To check the home directory for a particular user using built in shell variables

$ echo $HOME
In the command echo Welcome, what does the word Welcome represent with respect to the command?

$ echo Welcome 
  - Where Welcome is an argument
To check git command type

$ type git
To create a directory

$ mkdir /home/bob/birds
To create directories recursively

$  mkdir -p /home/bob/fish/salmon
Create few more directories

$ mkdir -p /home/bob/mammals/elephant
$ mkdir -p /home/bob/mammals/monkey
$ mkdir /home/bob/birds/eagle
$ mkdir -p /home/bob/reptile/snake
$ mkdir -p /home/bob/reptile/frog
$ mkdir -p /home/bob/amphibian/salamander
To move a directory

$ mv /home/bob/reptile/frog /home/bob/amphibian
To rename a directory

$ mv /home/bob/reptile/snake /home/bob/reptile/crocodile
To delete a directory

$ rm -r /home/bob/reptile
linux-basics-

------------------------------------------------------------------
Different types of Shells
In this section, we will take a look at different types of shells.

There are different types of shells in linux, some of the popular ones are below
Bourne Shell (sh)
C Shell (csh or tsh)
Korn Shell (ksh)
Z Shell (zsh)
Bourne again shell (Bash)
To check the shell being used. Use the command echo $SHELL

$ echo $SHELL
To change the default shell. Use the command chsh, you will be prompted for the password and following that input the name of the new shell. You have to login into new terminal session to see this change though.

$ chsh
Bash Shell Features
Bash supports command auto-completion. What this means is bash means to auto-complete commands for you if you type part of it and press the tab key

bash-auto

bash-auto1

In Bash we can set custom aliases for the actual commands

$ date
$ alias dt=date
$ dt
Use the history command to list the previous run commands that you ran earlier

$ history
Bash environment variables
To print SHELL environment variable

$ echo $SHELL
To see a list of all environment variables. Run env from the terminal

$ env
To set an environment variable with in the shell. The value is not carry forward to any other process.

$ OFFICE=caleston
To set an environment variable we can use the export command. To make the value carry forward to any other process.

$ export OFFICE=caleston
To persistently set an environment variable over subsequent login or a reboot add them to the ~/.profile or ~/.pam_environment in the users home directory.

$ echo "export OFFICE=caleston" >> ~/.profile (or)
$ echo "export OFFICE=caleston" >> ~/.pam_environment
To check the value of a environment variable called LOGNAME

$ echo $LOGNAME
Path Variable
Speaking about the environment variables, when a user issues an external command into the shell, the shell uses path variable to search for these external commands
To see the directories defined in path variable. Use the command echo $PATH.

$ echo $PATH
To check if the location of the command can be identified. Use the which command

Syntax: which <command>

$ which obs-studio
To define a command in the PATH variable. To add we can use the export command.

$ export PATH=$PATH:/opt/obs/bin
$ which obs-studio
Customize Bash Prompt
Once you login into the shell, the line you see is the bash prompt.

bash-prompt

It can be customized to see the username and the hostname

bash-prompt1

The bash prompt is set in control by a set of special shell environment variables. The most common of these and the one we will focus on is PS1 variable.
bash-prompt2

To see the value assign to PS1, type echo $PS1

$ echo $PS1
To change the PS1 to only display the word ubuntu-server.

$ PS1="ubuntu-server"
$ echo $PS1
To customize further, have a look at the below special character.
bash-prompt3

To change the bash prompt to display date, time, username of the current user, the hostname and the current working directory

$ PS1="[\d \t \u@\h:\w ] $ "

-----------------------------------------------------
To check the default shell for the current user. Display the shell for the current user but not necessarily the shell that is running at the movement.
$ echo $SHELL
To change the shell for bob from Bash to Bourne Shell
$ chsh -s /bin/sh bob
What is the value of the environment variable TERM
echo $TERM
Create a new environment variable called PROJECT=MERCURY and make it persistent by adding the variable to the ~/.profile file.
echo export PROJECT=MERCURY >> ~/.profile
Which of the following directories is not part of the PATH variable?
/opt/caleston-code
Set an alias called up for the command uptime and make it persistent by adding to ~/.profile file.
echo alias up=uptime >> ~/.profile
Update Bob's prompt so that it displays the date as per the format below: Example: [Wed Apr 22]bob@caleston-lp10:~$ Make sure the change is made persistent.
PS1='[\d]\u@\h:\w\$'
or
echo 'PS1=[\d]\u@\h:\w$' >> ~/.profile

----------------------------------------------------------------------------------------------------
Kernel and User Space
One of the important functions of the linux kernel is the Memory Management . We will now see how memory is seperated within the linux kernel
Memory is divded into two areas.

Kernel Space
Kernel Code
kernel Extensions
Device Drivers
User Space
C
Java
Python
Ruby e.t.c
Docker Containers
memory-management

Let us know see how programs running in the User Space work
All user programs function by manipulating data that is stored in memory and on disk. User programs get access to data by making special request to the kernel called System Calls

Examples include, allocating memory by using variables or opening a file.

user-space

For example, opening a file such as the /etc/os-release to see the operating system installed, results in a system call


--------------------------------------------------------------------------
HARDWARE:

we will look at how linux works with the hardware resources available to the system and how to make use of kernel modules

We will look at how linux identifies and manages hardware devices attached to the system
We will then see ways to list and get detailed information about these devices from the command line.
Lets take an example of USB Disk be used in the system.

As soon as the USB device is attached to the system a corresponding device driver which is part of the kernel space detects the stage change and generates an event.
This event which is called uevents is then sent to the User Space device manager daemon called udev.
The udev service is then responsible for dynamically creating a device node associated with the newly attached USB drive in the /dev/ filesystem.
Once the process is complete, the newly attached disk should be visible under /dev/ filesystem.

Use dmesg display messages from the area of kernel called Ring Buffer . When a linux operating system boots up there were numerous messages generated by the kernel that appear on the display screen. These messages also contain logs from the hardware devices that the kernel detects and provide good indication wheather it is able to configure

$ dmesg
$ dmesg | grep -i usb
The udevadm is the management utility for udev which queries the database for device information.

$ udevadm info --query=path --name=/dev/sda5
The udevadm monitor listens to the kernel new uevents upon detecting an event, it prints the details such as the device path and the device name on the screen. This command is handy to determine the details of the newly attached or removed device.

$ udevadm monitor
To list all PCI (Peripheral Component Interconnect) devices that are configured in the system. Examples of PCI devices are Ethernet Cards, RAID Controllers, Video Cards and wireless Adaptors that directly attached to PCI slots in the motherboard of the computer

$ lspci

To list information about Block Devices

$ lsblk

To display detail information about the CPU such as CPU architecture, cpu op-modes (32 bit, 64 bit) etc.

$ lscpu
To list available memory in the system.

$ lsmem --summary
Another alternate command to see the information about the memory. This command will list total used and free memory.

$ free -m
To extract detail information about the entire hardware information of the machine

$ lshw
To run commands with root privileges. Not every user can run all the commands in the linux system some commands need to be run as the root or the super-user. Use sudo followed by ( input the sudo password ).
$ sudo lshw



To check the exact kernel version that is running in this system.

$ uname -r
what is the kernel version in 4.15.0-88-generic?

Look for the first digit. In this case, it is 4
What is the major version number of the kernel 4.15.0-88-generic

Look for the second digit after the kernel version separated by a . In this case, it is 15
Which command would you run to print the messages generated by the kernel?

Type the command dmesg to see the messages.
$ dmesg
To list/count all block devices of type disk that are present in the system

Run: lsblk and count the number of disk devices.
$ lsblk
To check total number of physical cores in the system.

Run lscpu and multiply the Core(s) per socket with the number of Socket(s):
$ lscpu
To check total online memory

Run the lsmem command and look for the value of online memory
$ lsmem


-------------------------------------------------------------------------
Boot Sequence:

Linux Boot Sequence
Take me to the Video Tutorial
In this section, we look at the boot process in a simplied manner by dividing it into four broader steps.

The boot process can be broken down into four stages

BIOS POST
Boot Loader (GRUB2)
Kernel Initialization
INIT Process
boot-sequence

How to initiate a linux boot process?
This can be achieved in one of the two ways.
The first method is to start a linux device which is in a halted or stopped state
Second method is to reboot or reset a running system
BIOS POST
The first stage, called BIOS POST has very little to do with linux itself.
POST Stands for Power On Self Test.
In this stage, BIOS runs a POST test, to ensure the hardware components that are attached to the device are functioning correctly, if POST fails the computer may not be operable and the system will not be proceed to next stage of the boot process
BIOS

Boot Loader
The next stage after BIOS POST is Boot Loader after successful of POST test.
BIOS loads and executes the boot code from the boot device, which is located in the first sector of the harddisk. In Linux this is located in the /boot file system.
The boot loader will provide the user with the boot screen, often with multiple options to boot into. Such as Microsoft windows O.S or Ubuntu 18.04 O.S in an example of a dual boot system.
Once the selection is made at the boot screen, boot laoder loads the kernel into the memory supplies it with some parameters and handsover the control to kernel
A popular example of the boot loader is GRUB2 (GRand Unified Bootloader Version 2). Its a primary boot loader now for most of the operating system.
boot-loader

Kernel Initialization
After the selected kerenl is selected and loads into the memory, it usually decompress and then loads kernel into the memory.
At this stage, kernel carries out tasks such as initializing hardware and memory management tasks among other things.
Once it is completely operational , kernel looks for INIT Process to run. Which sets up the User Space and the process is needed for the environment.
kernel-initialize

INIT Process
In most of the current day linux distribution, the INIT function then calls the systemd daemon.
The systemd is responsible for bringing the linux host to usable state.
systemd is responsible for mounting the file systems, starting and managing system services.
systemd is the universal standard these days, but not too long ago another initialization process called system V (five) init was used. It is also called **Sys5
For example these were used in RHEL 6 or CentOS 6 distribution
Once of the key advantages of using systemd over system V(five) init is that it reduces the system startup time by parallelizing the startup of services.
To check the init system used run ls -l /sbin/init, if it is systemd then you will see a pointer to /lib/systemd/systemd

$ ls -l /sbin/init


--------------------------------------------------------------------------------------
RUN LEVEL:

Systemd Targets (Run Levels)
We can setup the server to boot either into graphical mode or non-graphical mode. Linux can run in multiple modes and these modes are set by something called runlevel

The operation mode which provide a graphical interface is called runlevel 5

The operation mode which provide a non-graphical mode is called runlevel 3

run-levels

To see the operation mode run in the system. Run the command runlevel from the terminal

$ runlevel
During boot, the init process checks the runlevel, it make sure that all programs need to get the system operation in that mode are started.

For example: The Graphical User mode requires a display manager service to run for the GUI to work, however this service is not required for the non-graphical mode

run-levels1

In the boot process section, we saw that the systemd is used as the init process in most new linux distributions suchs as Ubuntu 18.04.

In systemd, runlevels are called as targets.
The RunLevel 5 is called as the graphical target

The Runlevel 3 is called as the multiuser target

run-levels2

Now that we are familiar with runlevels in systemd target unit. Lets now take a look at how we change these values from a shell.
To see the default target, run the command systemctl get-default. This command looks at the file located at /etc/systemd/system/default.target

$ systemctl get-default
To change the default target, we can make use of systemctl set-target <desired target name goes here as an argument>

$ systemctl set-default multi-user.target 


The term runlevels is used in the sysV init systems. These have been replaced by systemd targets in systemd based systems.

The complete list of runlevels and the corresponding systemd targets can be seen below:

runlevel 0 -> poweroff.target

runlevel 1 -> rescue.target

runlevel 2 -> multi-user.target

runlevel 3 -> multi-user.target

runlevel 4 -> multi-user.target

runlevel 5 -> graphical.target

runlevel 6 -> reboot.target

Runlevels
-----------------------------------------------------------------

Filesystem Hierarchy:

Linux uses single rooted, inverted tree like file system
/home : It is the location that contains the home directories for all users, except the root user (root user home directory is located at /root)

/opt : If you want to install any third party programs put them in the /opt filesystem.

/mnt : It is the default mount point for any partition and it is empty by default. It is used to mount filesystems temporarly in the system

/tmp : It is used to store temporary data

/media : All external media is mounted on /media

/dev : Contains the special block and character device files

/bin : The basic programs such as binaries cp, mv, mkdir are located in the /bin directory

/etc : It stores most of the configuration files in Linux.

/lib : The directory /lib and /lib64 is the place to look for shared libraries to be imported into your program

/usr : In older systems, /usr directory is used for User Home Directories, however in the modern linux operating systems it is the location where all user land applciations in their data reside

/var : It contains variable data like mails, log files

filesystem

To print all the mounted filesystems, run df (disk filesystem) command

$ df -hP















