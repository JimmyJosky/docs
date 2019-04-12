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

**cd ~** or **cd**  	Change to your home directory

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

**rm -i**	Intercatively remova a file