## Debian Packaging

**dpkg** is the underlying *package manager* for these systems. It can install, remove, and build packages.
For Debian-based systems, the higher-level package management system is the **apt** (Advanced Package Tool) system of utilities. Generally, while each distribution within the Debian family uses apt, it creates its own user interface on top of it (for example, apt-get, aptitude, synaptic, Ubuntu Software Center, Update Manager, etc). Use **synaptic**.

## Red Hat Package Manager (RPM)	

**Red Hat Package MAnager (RPM)** is the other package management system popular on Linux distributions. It was developed by Red Hat, and adopted by a number of other distributions, including openSUSE, Mandriva, CentOS, Oracle Linux, and others.
The high-level package manager differs between distributions: Red Hat family distributions have historically used the repository format used by **yum** (Yellowdog Updater, Modified), although recent Fedora uses a replacement, **dnf**, still using the same format. SUSE family distributions also use RPM, but use the **zypper** interface, The GNOME project also uses **PackageKit** as unified interface.

## OpenSUSE's YaST Software Management

The **YaST (Yet another Setup Tool)** software maganer is similar to other graphical package managers. It is an RPM-based application. You can add, remove, or Update packages using this application very easily. To access the YaST software manager:

1. Click *Activities*
2. In the *Search box*, type "YaST"
3. Click the *YaST* icon
4. Click *Software Manager*

## Some Basic Utilities

There a some basic command lines utilities that are used constantly:

- **cat** : used to type out a file (or combine files)
- **head** : used to show the first few lines of a file
- **tail** : used to show the last few lines of a file
- **man** : used to view documentation 

## The Command Line

Most input lines entered as the shell prompt have three basic elements:

* Command
* Options
* Arguements

The **Command** is the name of the program you are executing. It may be followed by one or more options (or switches) that modify what the command may do. **Options** usually start with one or two dashes, for example **-p** or **--print**, in order to differentiate the from arguements, which represent what the command operates on.

## Steps for Setting Up and Running sudo

If your system does not already have sudo set up and enabled, you need to do the following steps:

1. You will need to make modifications as the administrative or superuser, root. While sudo will become the preferred method of doing this, we do not have it set up yet, so we will use *su* instead. At the command line prompt, type **su** and press **Enter**. You will then be prompted for the root password, so enter it and press **Enter**. You should end up with a different looking prompt, often ending with '#'.
For example:
```
$ su Password:
#
```
2. Now, you need to create a configuration file to enable your user account to use sudo. Typically, this file is created in the `/etc/sudoers.d/` directory or in `/etc/sudoers` file directory with the name of the file the same as your username. For example, for this demo, let’s say your username is “student”. After doing step 1, you would then create the configuration file for “student” by doing this:
`user@domain: # echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student`
3. Finally, some Linux distributions will complain if you do not also change permissions on the file by doing:
`user@domain: # chmod 440 /etc/sudoers.d/student`

## Virtual Terminals

**Virtual Terminals (VT)** are console sessions that use the entire display and keyboard outside of a graphical environment. Such terminals are considered "virtual" because, although there can be multiple active terminals, only one terminal remains visible at a time. A VT is not quite the same as a command line terminal window; you can have many of those visible at once on a graphical desktop.

One virtual terminal (usually number one or seven) is reserved for the graphical environment, and text logins are enabled on the unused VTs. Ubuntu uses **VT 7**, but CentOS/RHEL and openSUSE use **VT 1** for the graphical display.

An example of a situation where using VTs is helpful is when you run into problems with the graphical desktop. In this situation, you can switch to one of the text VTs and troubleshoot.

To switch between VTs, press **CTRL-ALT-function key** for the VT. For example, press **CTRL-ALT-F6** for **VT 6**. Actually, you only have to press the **ALT-F6** key combination if you are in a VT and want to switch to another VT.

## Turning Off The Graphical Desktop

Linux distributions can start and stop the graphical desktop in various ways. The exact method differs from distributions and among distributions versions. For the newer systemd-based distributions, the display manager is run as service, you can stop the GUI desktop with systemctl utility and most distributions will also work with the telinit command, as in:

`user@domain: $ sudo systemctl stop gdm` or `sudo telinit 3`

and restart it (after logging into the console) with:

`user@domain: $ sudo systemctl start gdm` or `sudo telinit 5`

On Ubuntu version befor 18.04 LTS, substitute lightdm for gdm

## Rebooting and Shutting Down

The **halt** and **power-off** command issue `shutdown -h` to halt the system; **reboot** issues `shutdown -r` and causes the machine to reboot instead of just shutting dow. Both rebooting and shutting down from the command line requires superuser (root) access.

When administering a multiuser system, you have the option of notifying all users prior to shutting down, as in:

`user@domain: $ sudo shutdown -h 10:00 "Shutting down for scheduled maintenance"`

## Locating Applications

One way to locate programs is to employ the **which** utility. For example, to find out exactly where the ostinato program resides on the filesystem:

```
user@domain: $ which ostinato
/usr/bin/ostinato
```
If **which** does not find the program, **whereis** is a good alternative because it looks for packages in a broader range of system directories:

```
user@domain: $ whereis ostinato
ostinato: /usr/bin/ostinato /usr/share/man/man1/ostinato.1.gz
```
as well as locating source and man files packaged with the program.

## Accesing Directories

When you first log into the system or open a terminal, the default directory should be your *Home* directory. You can print the exact path of this by typing **echo $HOME**. Many Linux distributions actually open new graphic terminals is **$HOME/Desktop**. The following commands are usefull for directory navigation:

**pwd** 				Displays the present working directory

**cd ~ or cd**  		Change to your home directory

**cd ..** 				Change to parent directory

**cd -** 				Change to previous directory

## Understanding Absolute and Relative Paths

There are two ways to identify paths:

- **Absolute pathname**
	An absolute pathname begin with the root directory and follows the tree, branch by branch, until it reaches the desired directory or file. 
	Absolute paths always starts with `/`.

- **Relative pathname**
	A relative pathname starts from present working directory. Relative paths never start with `/`.

Multiple slashes ("/") between directories and files are allowed. But multiple slashes between elements in the pathname is ignored by the system.
///usr//bin is valid, but seen as /usr/bin by the system.

Most of the time, it is most convenient to use relative paths, which require less typing. Usually, you take advantage of the shortcuts provided by: **.** (present directory), **..** (parent directory) and **~** (home directory)

## Exploring the Filesystem

Traversing up and down the filesystem tree can get tedious. The **three** command is good what to get a bird's-eye view of the filesystem tree.
Use **tree -d** to view just the directories and to suppress listing file names.

The following commands can help in exploring the filesystem:

**cd /** 		Changes your current directory to the root (/) directory (or path you supply)

**ls** 			List the contents of the present working directory

**ls –a** 		List all files, including hidden files and directories (those whose name start with . )

**tree** 		Displays a tree view of the filesystem

## Hard Links

The **ln** utility is used to create hard links and (with the **-s** option) soft links, also known as symbolic links of symlinks. These two kind of links are very usefull in UNIX-based operating systems.

Suppose that **file1** already exist. A hard link, called **file2**, is created with the command:

`user@domain: $ ln file1 file2`

Note that two files now appear to exist. However. a closer inspection of the file listing shows that this is not quite true.

`user@domain: $ ls -li file1 file2`

The **-i** option to **ls** prints out in the first column the inode number, which is a unique quantity for each file object. This field is the same for both of these files; what is really going on here is that it is only one file, but it has more than one name associated with it, as is indicated by the **2** that appears in the **ls** output. Thus, there was already another object linked to **file1** before the command was executed.

Hard links are very useful and they save space, but you have to be careful with their use, sometimes in subtle ways. For one thing, if you remove either **file1** or **file2** in the example, the inode object 
(and the remaining file name) will remain, which might be undesirable, as it may lead to subtle errors later if you recreate a file of that name.

If you edit one of the files, exactly what happens depends on your editor; most editors, including vi and gedit, will retain the ling *by default*, but it is possible that modifying one of the names may break the link and result in creation of two objects.

## Soft (Symbolic) Links

Soft (or Symbolic) links are created with the **-s** options, as in:

```
user@domain: $ ln -s file1 file3
user@domain: $ ls - li file1 file3
```
Notice **file3** no longer appears 	to be a regular file, and it clearly points to **file1** and has a different inode number.

Symbolic links take no extra space on the filesystem (unless their names are very long). There are extremely convenient, as they can easily be modified to point to different places. An easy way to creat a shortcut from your **home** directory to long pathnames is to create a symbolic link.

Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media, which may or may not be currently avainble or even exist. In the case where the link does not point to a currently available or existing object, you obtain a dangling link.

## Navigating the Directory History

The **cd** command remembers where you were last, and lets you get back there with **cd -**. For remembering more than just the last directory visited, use **pushd** to change the directory instead of **cd**; this pushes your starting directory onto a list. Using **popd** will then send you back to those directories, walking in reverse order (the most recent directory will be the first one retrieved with **popd**). The list of directories is displayed with the **dirs** command.

## Viewing Files

You can use the following command line utilities to view files:

**cat**			Used for viewing files that are not very long; it does not provide any scroll-back

**tac**			Used to look at a file backwards, starting with the last line

**less**		Used to view larger files because it is a paging program. It pauses at each screen full of text, provides scroll-back capabilities, and lets you search and navigate within the file.
				**Note**: Use / to search a pattern in the forward direction and ? for a pattern in the backward direction. An older program name more is still used, but has fewer capabilities: "less is more"

**tail**		Used to print the last 10 lines of a file by default. You can change number of lines by doing **-n 15** or just **-15** if you wanted to look at the last 15 lines instead of the default.

**head**		The opposite of **tail**; by default, it prints the first 10 lines of a file.

## touch

**touch** is often used to set or update the access, change, and modify times of files. By default, it resets a file's timestamp to match the current time.

However, you can also create an empty file using **touch**:

`user@domain: $ touch <filename>`

This is normally done to create an empty file as a placeholder for a later purpose.

**touch** provide several useful options. For example, the **-t** options allows you to set the date and timestamp of the file to a specific value, as in:

`user@domain: $ touch -t 12091600 myfile`

This sets the **myfile** file's timestamp to 4 p.m. (16:00) and December 9th (12 09 1600)

## mkdir and rmdir

**mkdir** is used to create a directory:

**mkdir sampdir** - it creates a sample directory named **sampdir** under the current directory

**mkdir /usr/sampdir** - it creates a sample directory called **sampdir** under */usr*

Removing a directory is done with rmdir. The directory must be empty or the command will fail. To remove a directory and all of its contents you have to do **rm -rf**.

## Moving, Renaming or Removing a File

Note that **mv** does double duty, in that it can:

- Simply rename a file
- Move a file to another location, while possibly changing its name at the same time.

If you are not certain about removing files that match a pattern you supply, it is always good to run rm interactively (**rm -i**) to prompt before every removal

**mv**		Rename a file

**rm**		Remove a file

**rm -f**	Forcefully remove a file

**rm -i**	Intercatively remove a file

## Modifying the Command Line Prompt

The **PS1** variable is the character string that is displayed as the prompt on the command line. Most distributions set PS1 to a known default value, which is suitable in most cases. However, users may want custom informations to show on the command line. For example, some system administrators require the user and the host system name to show up on the command line as in:

`user@host $`

This could prove useful if you are working in multiple roles and want to be always reminded of who you are and what machine you are on. The prompt above could be implemented by setting the **PS1** variable to: 

`\u@\h \$`.

## Standart File Streams

When commands are executed, by default there are three standard file streams (or descriptors) always open for use: standard input (standard in or stdin), standard output (standard out or stdout) and standard error (or stderr).

|	**Name** 		|**Symbolic name** 	|	**Value** 		|	**Example** 		|
| ----------------- | ----------------- | ----------------- | ----------------------|
|	standad input 	|	stdin			| 0					| keyboard				|
|	standard output |	stdout 			| 1 				| terminal 				|	
|	standard error 	|	stderr 			| 2 				| log file 				|

Usually, stdin is your keyboard, and stdout and stderr are printed on your terminal. stderr is often redirected to ann error logging file, while stdin is supplied by directing input to come from a file or from the output of a previous command through a pipe. stdout is also often redirected into a file. Since stderr is where error messages are written, usually nothing will go there.

In Linux, all open files are represented internally by what are called file descriptors. Simply put, these are represented by numbers starting at zero. stdin is file descriptor 0, stdout is file descriptor 1, and stderr is file descriptor 2. Typically, of other files are opened in addition to these three, which are opened by default, they will start at file descriptor 3 and increase from there.

## I/O Redirection

Through the command shell, we can redirect the three standart file streams so that we can get input from either a file or another command, instead of from our keyboard, and we can write output and errors to files or use them to provide input for subsequent commands.

For example, if we have a program called **do_something** that reads from stdin and writes to stdout and stderr, we can change its input soure by using the less-than sigh ( **<** ) followed by the name of the file to be consumed for input data:

`$ do_something < input-file`

If you want to send the output to a file, use the greater-than sign ( **>** ) as in:

`$ do something > output-file`

Because stderr is not the same as stdout, error messages will still be seen on the terminal windows in the above example.

If you want to redirect stderr to a separate file, you use stderr's file descriptor number (2), the greater-than sign (>), followed by the name of the file of the file you want to hold everything the running command writes to stderr:

`$ do_something 2> error-file`

*Note*: By the same logic, **do_something 1> output-file** is the same as **do_something > output-file**.

A special shorthand notation can send anything written to file descriptor **2** (stderr) to the same place as file descriptor **1** (stdout): **2>&1**.

`$ do_something > all-output-file 2>&1`

bash permits an easier syntax for the above:

`$ do_something >& all-output-file`

## Pipes

The UNIX/Linux philosophy is to have many simple and short programs (or commands) cooperate together to produce quite complex results, rather than have one complex program with many possible options and modes of operation. In order to accomplish this, extensive use or pipes is made. You can pipe the output of one command or program into another as its input.

In order to do this, we use the vertical-bar, |, (pipe symbol) between command as in:

`$ command1 | command2 | command3`

The above represents what we often call a pipeline, and allows Linux to combine the actions of several commands into one. This is extraordinarily efficient becaus **command2** and **command3** do not have to wait for the previous pipeline command to complete before they can begin hacking at the data in their input streams; on multiple CPU or core system, the available computing power is much better utilized and things get done quicker.

Furthermore, there is no need to save output in (temporary) files between the stages in the pipeline, which saves disk space and reduces reading and writing from disk, which is often the slowest bottleneck in getting something done.

## Searching for Files

Being able to quickly find the files you are looking for will save your time and enhance productivity. You can search for files in both your home directory space, or in any other directory or location on the system.

The main tools for doing this are the **locate** and **find** utilities.

## locate

The **locate** utility program performs a search taking advantage of a previously constructed database of files and directories on your system, matching all entries that contain a specified character string. This can sometimes result in a very long list.

To get a shorter (and possibly more relevant) list, we can use the **grep** program as a filter. **grep** will print only the lines contain one or more specified strings, as in:

`$ locate zin | grep bin`

which will list all the files and directories with both **zip** and **bin** in their name.

**locate** utilizes a database created by the related utility, **updatedb**. Most Linux systems run this automatically once a day. However, you can update it at any time by just running **updatedb** from the command line as a root user.

## Wildcards and Matching File Names

You can search for a filename containing specific characters using wildcards.

**?**		Matches any single character

**\***		Matches any string of character

**[set]**	Matches any character in the set characters, for example **[adf]** will match any occurrence of **"a", "d"**, or **"f"**

**[!set]**	Matches any charcter not in the set of characters

To search for files using the ? wildcard, replace each unknown character with ?. For example, if you know only the first two letters are 'ba' of a three-letter filename with an extension of **.out**, type **ls ba?.out** .

To search for files using the \* wildcard, replace the unknown string with \*. For example, if you remember only that the extension was **.out**, type **ls \*.out**.

## The find Program

**find** is an extremelly useful and often-used utility program in the daily life of a Linux system administrator. It recurses down to filesystem tree from any particular directory (or set of directories) and locates file that match specified conditions. The default pathname is always the present working directory.

For example, administrators sometimes scan for potentially large core files (which contain diagnostic information after a program fails) that are more than several weeks old in order to remove them.

Its also common to remove file in inessential or outdates file in **/tmp** (and other volatile directories, such as those containing cached files) that have not been accessed recently. Many Linux distributions use shell script that run periodically (through **cron** usually) to perform such house cleaning.

## Using find

When no arguments are given, **find** lists all files in the current directory and all of its subdirectories. Commonly used options to shorten the list include **-name** (only list files with a certain pattern in their name), **-iname** (also ignore the case of file names), and **-type** (which will restrict the result to files of a certain specified type, such as **d** for directory, **l** for symbolic link, or **f** for a regular file, etc.)

Searching for files and directories name **gcc**:

`$ find /usr -name gcc`

Searching only for directories named gcc:

`$ find /usr -type d -name gcc`

Searching only for regular files named gcc:

`$ find /usr -type f -name gcc`

## Using Advanced find Options

Another good use of **find** is being able to run commands on the files that match your search criteria. The **-exec** option is used for this purpose.

To find and remove all files that end with **.swp**:

`$ find -name "*.swp" -exec rm {} \;`

The **{}** (squiggly brackets) is a placeholder that will be filled with all the file names that result from the find expression, and the preceding command will be run on each one individually.ъ

*Note*: You have to end the command with either **';'** (including single-quotes) or **\;**. Both forms are fine.

One can also use the **-ok** options, which behaves the same as **-exec**, expect that **find** will prompt you for permissions before executing the command. This makes it a good way to test your results before blindly executing any potentially dangerous commands.

## Finding Files Based on Time and Size

It is sometimes the case that you wish to find files according to attributes, such as when they were created, last used etc., or based on their size. It is easy to perform such searches.

To find files based on time:

`$ find / -ctime 3`

Here, **-ctime** is when the inod metadata (i.e. file ownership, permissions, etc.) last changed; its often, but not necessarily, when the file was first created. You can also search for accessed/last read **(-atime)** or modified/last written **(-mtime)** times. The number is the number of days and can be expressed as either a number **(n)** that means exactly that value, **+n**, which means greater than that number, or **-n**, which means less than that number. There are similar options for times in minutes (as in **-cmin, -amin**, and **-mmin**).

To find files based on sizes:

`$ find / -size 0`

Note the size here is in 512-byte blocks, by default; you can also specify bytes (c), kilobytes (k), megabytes (M), gigabytes (G), etc. As with the time numbers above, file sizes can aslo be exact numbers **(n)**, **+n** or **-n**. For details, consult the man page for find.

For example, to find files greater than 10MB in size and running a command on those files:

`$ find / -size +10MB -exec command {} \;`

## Package Management Systems on Linux

The core parts of a Linux distribution and most of its add-on software are installed via the Package Management System. Each package contains the files and other instructions needed to make one software component work well and cooperate with the other components that comprise the entire system. Packages can depend on each other. For example, a package for a web-based application written on PHP can depend on the PHP package.

There are two broad families of package manager: those based on Debian and those which use RPM as their low-level package manager. The two system are incompatible, but broadly speaking, provide the same features and satisfy the same needs. There are some other systems used by more speacialized Linux distributions.

## Package Manager: Two levels

Both package management systems operate on two distinct levels: a low-level tool (such as dpkg or rpm) takes care of the details of unpacking individual packages, running scripts, getting the software installed correctly, while a high-level tool (such as apt-get, yum, dnf or zypper) works with groups of packages, downloads packages from a vendorm and figures out dependencies.

Most of times users need to work with only high-level tool, which will take care of calling the low-level tool as needed. Dependency resolution is a particularly important feature of the high-level tool, as it handles the details of finding and installing each dependency for you. Be careful, however, as installing a single package could result in many dozens or even hundreds of dependent packages being installed.

## Working With Different Package Management Systems

**The Advantage Packaging Tool (apt)** is the underlying package management system that manages software on Debian-based systems. While it forms the backend for graphical package managers, such as Ubuntu Software Center and synaptic, its native user interface is at the command line, with programs that include apt-get and aph-cache.

**Yellowdog Updater Modified (yum)** is na open source command-line package-management utility for RPM-compatible Linux systems that belongs to the Red Hat/Fedora family. **yum** has both command line and graphical user interfaces. Recent Fedora versions have replaced **yum** with a new utility called **dnf**, which has less historical baggage, has nice new capabilities and is mostly backwards-compatible with **yum** for day-to-day commands.

**zypper** is the package management system for the SUSE/openSUSE family and is also based on RPM. **zypper** also allows you to manage repositories from the command line. **zypper** is fairly straightforward to use and resembles **yum** quite closely.

*Basic packaging commands*:

|**Operation**					  |**RPM**							|**deb**				  |	
| ------------------------------- | ------------------------------- | ----------------------- |
| Install package				  | 		rpm -i foo.rpm 			| dpkg --install foo.deb  |
| Install package, dependencies	  | 		yum install foo 		| apt-get install foo 	  |
| Remove package 				  | 		rmp -e foo.rpm 			| dpkg --remove foo.deb   |
| Remove package, dependencies	  | 		yum remove foo 			| apt-get autoremove foo  |
| Update package 				  | 		rpm -U foo.rpm 			| dpkg --install foo.deb  |
| Update package, dependencies	  | 		yum update foo 			| apt-get install foo.deb |
| Update entire system 			  | 		yum update 				| apt-get dist-upgrade 	  |
| Show all installed packages 	  | rpm -qa or yum list installed   | dpkg --list 			  |
| Get information on package 	  | 		rpm -qil foo 			| dpkg --listfiles foo 	  |
| Show package named *foo* 		  |		yum list "foo" 			    | apt-cache search foo 	  |
| Show all available packages 	  |  		yum list 				| apt-cache dumpavail foo |
| What package is *file* part of? | 		rpm -qf file 			| dpkg --search file 	  |
