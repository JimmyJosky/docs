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
`# echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student`
3. Finally, some Linux distributions will complain if you do not also change permissions on the file by doing:
`# chmod 440 /etc/sudoers.d/student`

## Virtual Terminals

**Virtual Terminals (VT)** are console sessions that use the entire display and keyboard outside of a graphical environment. Such terminals are considered "virtual" because, although there can be multiple active terminals, only one terminal remains visible at a time. A VT is not quite the same as a command line terminal window; you can have many of those visible at once on a graphical desktop.

One virtual terminal (usually number one or seven) is reserved for the graphical environment, and text logins are enabled on the unused VTs. Ubuntu uses **VT 7**, but CentOS/RHEL and openSUSE use **VT 1** for the graphical display.

An example of a situation where using VTs is helpful is when you run into problems with the graphical desktop. In this situation, you can switch to one of the text VTs and troubleshoot.

To switch between VTs, press **CTRL-ALT-function key** for the VT. For example, press **CTRL-ALT-F6** for **VT 6**. Actually, you only have to press the **ALT-F6** key combination if you are in a VT and want to switch to another VT.

## Turning Off The Graphical Desktop

Linux distributions can start and stop the graphical desktop in various ways. The exact method differs from distributions and among distributions versions. For the newer systemd-based distributions, the display manager is run as service, you can stop the GUI desktop with systemctl utility and most distributions will also work with the telinit command, as in:

`$ sudo systemctl stop gdm` or `sudo telinit 3)`

and restart it (after logging into the console) with:

`$ sudo systemctl start gdm` or `sudo telinit 5)`

On Ubuntu version befor 18.04 LTS, substitute lightdm for gdm