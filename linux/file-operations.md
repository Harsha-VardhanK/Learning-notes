File Compression and Archival
File Compression and Archival
Viewing file sizes
The du command, which stands for disk usage is a popular command to inspect the size of the file.

du with -sk shows the size of a file or directory in Kilobytes

$ du -sk test.img
du with -sh shows the size of a file or directory in human readable format

$ du -sh test.img
we can also use long list , ls -lh to print the size of the file.

$ ls -lh test.img
Archiving Files
Let us know take a look at widely used utility called tar

tar is used to group multiple files and directories into a single file. Hence it is specially used for archiving data.
tar is an abrevation for tape archive.
Files created with tar are often called tarballs.
To archive a file or directory. Use tar command followed by -c to create an archive and the -f is used to specify the name of the tar file to be created. These is followed by files or directories to be archive.

$ tar -cf test.tar file1 file2 file3 
$ ls -ltr test.tar
The tar command followed by -tf option followed by the tar filename is used to see the contents of the tarball.

$ tar -tf test.tar
The tar command followed by -xf option followed by the tar filename is used to extract the contents from the tarball.

$ tar -xf test.tar
The tar command followed by -zcf option is used to compress the tarball to reduce its size.

$ tar -zcf test.tar
Compression
Compression is the technique used to reduce the size consumed by a file or a dataset.

To reduce the size of a file or directory in the linux file system, there are commands specificly used for compression.
Let us now look at the three popular ones
bzip2 (.bz2 extension)

gzip (.gz extension)

xz (.xz extension)

$ bzip2 test.img
$ gzip test1.img
$ xz test2.img
The space of the compressed files created by these three commands depends on a few factors, such as the type of data being compressed, the other factors that effect the size are the compression algorithm used by these commands and the compression level used.
The compressed files can be uncompressed by using the below commands
bunzip2

gunzip

unxz

$ bunzip2 test.img
$ gunzip test1.img
$ unxz test2.img
compress-uncompress

Compressed files need not to be uncompressed everytime
Tools such as zcat , bzcat and xzcat allow the compressed files to be read without an uncompress
$ zcat hostfile.txt.bz2
$ zcat hostfile.txt.gz
$ zcat hostfile.txt.xz
compress-cat

-----------------------------------------------------------------------------------------
Searching for files and Patterns:

locate
Lets say you want to find the files with the name City.txt. Easiest way to do this is to make use of locate command.

Run locate command followed by the filename you are searching as an argument. This should return all paths matching the pattern.

$ locate City.txt
The downside of the locate command is it depends on a database called mlocate.db for querying the filename.

If you have just installed linux or if the file you are trying to locate was created recently. The locate command may not give you useful results. This is because it is possible that the DB is not been updated yet.

To manually update the DB, run the command updatedb and then run the locate command again

$ sudo updatedb
Please note that the updatedb command needs to be run as root user to work.

find
Another way to do this is make use of the find command. Use the find command followed by the directory under which you want to search. To search file by a name use the -name option followed by the name of the file.

$ find /home/michael -name City.txt
locate-find

Grep
To search within files, the most popular command in linux is grep.

Grep is commonly used to print lines of a file matching a pattern but it also offers a variety of other options as well.
The grep command is case-sensitive
To search for the word second from the sample.txt

$ grep second sample.txt
To search for the word capital with case-insensitive use -i flag.

$ grep -i capital sample.txt
To search for a pattern recursively.

$ grep -r "thrid Line" /home/michael
To print the lines that don't matches the pattern

$ grep -v "printed" sample.txt
grep

What if you want to match a pattern that form a whole word?
To search for the whole word called exam. Use grep followed by -w flag

$ grep -w exam examples.txt
You can also combine multiple options together. For example, to reverse the search and print all lines of the same file that doesn't match the whole word exam. Use grep -vw

$ grep -vw exam examples.txt
To print the number of lines after and before matching a pattern. Use grep command with -A and -B flags respectively.

$ grep -A1 Arsenal premier-league-table.txt
$ grep -B1 4 premier-league-table.txt
grep1

Finally, the -A and -B can be combined into one single search.

$ grep -A1 -B1 Chelsea premier-league-table.txt
grep2


--------------------------------------------------------------------------------------------
IO Redirection:

IO Redirection
Standard Streams in Linux
There are three data streams created when you launch a linux commnad.

Standard Input (STDIN)

STDIN is the standard input stream which accepts text as an input.
Standard Output (STDOUT)

Text output is delivered as STDOUT or the standard out stream
Standard ERROR (STDERR)

Error messages of the command are sent through the standard ERROR stream (STDERR)
io

With IO Redirection, the STDIN, STDOUT and STDERR can be redirected to a text file.

REDIRECT STDOUT
To redirect STDOUT to a file instead of printing it on the screen.

$ echo $SHELL > shell.txt
To append STDOUT to an exisiting file

$ echo $SHELL >> shell.txt
REDIRECT STDERR
To redirect just the ERROR message we need to use 2 followed by forward arrow > symbol and then the name of the filename in which the errors are written.

$ cat missing_file 2> error.txt
To append the STDERR to the exisiting file

$ cat missing_file 2>> error.txt
If you want to execute and not print ERROR messages on the screen even if it generates a standard ERROR. You can redirect to /dev/null

$ cat missing_file 2> /dev/null
Command Line Pipes
Command Line Pipes allow the linking of multiple commands.

In simple terms, pipes allows the first commands standard output to be used as the standard input for the second command.

The pipes are defined using vertical bar symbol (|).

$ grep Hello sample.txt | less 
pipe

Another command to work with STDIN and STDOUT is the tee command.

Instead of the redirect operator, we can use the command line pipe (|) followed by tee command.

$ echo $SHELL | tee shell.txt
Use tee with -a option, to append instead of overwritting it

$ echo "This is the bash shell" | tee -a
tee

-----------------------------------------------------------------------------------
LAB:
Create a tarball of the directory called python and compress it using gzip. The compressed tar file should be available at /home/bob/python.tar.gz

$ tar -cf /home/bob/python.tar /home/bob/reptile/snake/python
$ gzip /home/bob/python.tar
There is a compressed file called eaglet.dat.gz located under the eagle directory. Extract it in the same location

$ gunzip /home/bob/birds/eagle/eaglet.dat.gz
A file has been copied to the laptop by the name of caleston-code. But he does not remember which directory he saved it in.Can you find it?

$ sudo find / -name caleston-code
Find the location of the file called dummy.service and redirect its absolute path to the file /home/bob/dummy-service. You can use the redirect operator with the echo command to save the answer to the file.

$ sudo find / -name dummy.service
$ echo /etc/systemd/system/dummy.service > /home/bob/dummy-service 
Find the file under /etc directory that contains the string 172.16.238.197. Save the answer using the absolute path in the file **/home/bob/ip**

$ sudo grep -ir 172.16.238.197 /etc/ > /home/bob/ip
Create a new file called /home/bob/file_wth_data.txt. This file should have one line of text that says a file in my home directory. Make use of the redirect operator.

$ echo "a file in my home directory" > /home/bob/file_wth_data.txt
Run the command python3 /home/bob/my_python_test.py and redirect the standard error to the file /home/bob/py_error.txt.

$ python3 /home/bob/my_python_test.py 2>/home/bob/py_error.txt
Read the file /usr/share/man/man1/tail.1.gz and without extracting it copy the first line of this file to /home/bob/pipes

$ zcat /usr/share/man/man1/tail.1.gz | head -1 > /home/bob/pipes

-----------------------------------------------------------------------------------------
Vi Editor:

Text Editor
There are several options available, we will be focusing on the VI Editor.

Most popular text editor in linux is the VI Editor.
The VI EDITOR is available in all most all of the linux distribution out of the box.
The command to open the vi editor is vi followed by the filename that you want to create or append.
$ vi /home/michael/sample.txt
The VI EDITOR has three operation modes.
Command Mode

When the vi editor opens a file, it always goes to the COMMAND MODE first.
In this mode, the editor only understands the commands
Insert Mode

To switch from command mode to INSERT MODE type lower case i
This mode allows you to write text into the file.
Once you are done with editing the file, to go back to command mode hit the ESC button.
While going into insert mode from command mode you may use other options such as I, o, O, a, or A
Last Line Mode

Pressing the : key will take you to the LAST LINE MODE
In this mode you can choose to save changes to the file, discard changes, or save and edit.
From the last line mode hit the ESC key to go back to the command mode.
vi

Command Mode
command1

command2

command3

Insert Mode
insert

Last Line Mode
lastline

There is another popular editor called VIM which is an improved version of VI with added features but very similar in appereance to VI.
In the most distros today, the VI is the symblic to the VIM editor
---------------------------------------------------------------------------------------------------------
VIM

Go to insert mode

Press i
Exit from insert mode and go to command mode

Press ESC
To remove a character

Move Cursor to the characters to be removed and press x to remove them
Change the file contents to Welcome to KodeKloud and save file.

Go to insert mode by pressing i and delete all content and type in new content. Once done press ESC key and go to command mode. Then type in command :w!
Update the port it listens on from 80 to 5000 in apache webserver.

Go to insert mode by pressing i and replace 80 with 5000 in line 10
Remove the line that starts with LogFormat.

Go to the line 33 and press dd (d twice) to remove the entire line.
To undo the previous change

Press u to undo previous change
There's a 6 hiding in the file. Find it.

find command /6

