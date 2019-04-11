## Debian Packaging

**dpkg** is the underlying *package manager* for these systems. It can install, remove, and build packages.
For Debian-based systems, the higher-level package management system is the **apt** (Advanced Package Tool) system of utilities. Generally, while each distribution within the Debian family uses apt, it creates its own user interface on top of it (for example, apt-get, aptitude, synaptic, Ubuntu Software Center, Update Manager, etc).

## Red Hat Package Manager (RPM)	

**Red Hat Package MAnager (RPM)** is the other package management system popular on Linux distributions. It was developed by Red Hat, and adopted by a number of other distributions, including openSUSE, Mandriva, CentOS, Oracle Linux, and others.
The high-level package manager differs between distributions: Red Hat family distributions have historically used the repository format used by **yum** (Yellowdog Updater, Modified), although recent Fedora uses a replacement, **dnf**, still using the same format. SUSE family distributions also use RPM, but use the **zypper** interface, The GNOME project also uses **PackageKit** as unified inte