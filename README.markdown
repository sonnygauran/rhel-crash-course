# Red Hat Crash Course
This training module contains minimal literature to get started and be comfortable with Red Hat Linux and MySQL.

### `gnome-terminal`
To start a terminal (Gnome Terminal), start the Run dialog.
And then type the following command to run the terminal.

	# Hit `Ctrl+F2`, the type
	gnome-terminal

> ![Run Dialog](/rhel-crash-course/images/run-dialog.png)
	
or run the terminal through the main menu

> ![Gnome-terminal icon](/rhel-crash-course/images/main-menu-gnome-terminal.png)
> ![Gnome-terminal](/rhel-crash-course/images/gnome-terminal.png)

## Unit 1: Getting Started with the GNOME Graphical Desktop
There are many available graphical applications to the gnome desktop.
Here are the what you'll need to get familiar with:

* Terminal
* Text Editor
* File browser

### `gedit` (Gnome Edit)
To start the gnome text editor

	$ gedit

or supply the file(s) after the command. This filenames can be
existing files or files that will be created after *Save* or hitting `Ctrl+S`

	$ gedit file.txt
	
The gnome editor is also accessible via the Main Menu.

> ![Gnome Edit Menu](/rhel-crash-course/images/main-menu-gedit.png)
> ![Gnome Edit](/rhel-crash-course/images/gedit.png)

## Unit 2: Manage Files Graphically with `nautilus`
To start the file browser, you can execute the following command.

	$ nautilus

Or just click on the Home icon.

> ![Home icon](/rhel-crash-course/images/home-icon.png)
> ![Nautilus](/rhel-crash-course/images/nautilus.png)


## Unit 3: Configure Local Services
Here, we configure show how to configure the clock and view running processes.

Right-click the Clock on the upper-right corner and tweak by selecting *Adjust Date & Time*.

> ![Home icon](/rhel-crash-course/images/clock-adjust.png)

## Unit 4: Manage Physical Storage

To list available partitions

> ![Available Partitions](/rhel-crash-course/images/fdisk-l.png)

	$ fdisk -l

## Unit 5: Manage System Resources
What to monitor:

* CPU power
* Bandwidth
* Memory
* Storage


1. free. The free command displays system memory utilization. 

> ![free](/rhel-crash-course/images/unit_5-free.png)

2. top. The top command displays pretty much everything. CPU utilization, process statistics, memory utilization — top monitors it all. In addition, unlike the free command, top's default behavior is to run continuously; there is no need to use the watch command.

> ![top](/rhel-crash-course/images/unit_5_1.png)

3. The GNOME System Monitor. If you are more comfortable with graphical user interfaces, the GNOME System Monitor may be more to your liking. Like top, the GNOME System Monitor displays information related to overall system status, process counts, memory and swap utilization, and process-level statistics.

However, the GNOME System Monitor goes a step further by also including graphical representations of CPU, memory, and swap utilization, along with a tabular disk space utilization listing.

> ![GNOME System Monitor](/rhel-crash-course/images/unit_5-gnome_system_monitor2.png)

4. df and du. The df command reports filesystem disk usage. du estimates the filesystem usage.

> ![top](/rhel-crash-course/images/unit_5-df.png)
> ![top](/rhel-crash-course/images/unit_5-du1.png)

	
## Unit 6: Manage System Software
RPM, or the RPM Package Manager, is the default package management system for Red Hat Linux. The name RPM variously refers to the .rpm file format, files in this format, software packaged in such files, and the package manager itself. 

1. Sample Query Commands

		[root@genesis ~]# rpm -ql iputils
		/bin/ping
		/bin/ping6
		/bin/tracepath
		/bin/tracepath6
		/etc/rc.d/init.d/rdisc
		/sbin/arping
		/sbin/ifenslave
		/sbin/rdisc
		/usr/sbin/arping

		[root@genesis ~]# rpm -qf /bin/ping
		iputils-20020927-46.el5

		[root@genesis ~]# 

		[percy@linux-mlvx ~]$ rpm -qi iputils
		Name        : iputils                      Relocations: /usr 
		Version     : ss021109                          Vendor: openSUSE
		Release     : 300.1.1                       Build Date: Thu 29 Jul 2010 12:37:18 AM PHT
		Install Date: Wed 12 Jan 2011 05:06:10 PM PHT      Build Host: build33
		Group       : Productivity/Networking/Other   Source RPM: iputils-ss021109-300.1.1.src.rpm
		Size        : 223310                           License: BSD3c ; GPLv2+
		Signature   : RSA/8, Thu 29 Jul 2010 12:37:35 AM PHT, Key ID b88b2fd43dbdc284
		Packager    : http://bugs.opensuse.org
		URL         : ftp://ftp.tux.org/people/alexey-kuznetsov/ip-routing
		Summary     : IPv4and IPv6 Networking Utilities
		Description :
		This package contains some small network tools for IPv4 and IPv6 like
		rdisc, ping6, traceroute6, tracepath, and tracepath6.



		Authors:
		--------
		    Alexey Kuznetsov <kuznet@ms2.inr.ac.ru>
		Distribution: openSUSE 11.3

		[percy@linux-mlvx ~]$ 


2. To install new package,

		# rpm -i packagename.rpm
		# rpm -iv packagename.rpm
		# rpm -hiv packagename.rpm

3. To update package,
		# rpm -u packagename.rpm
		# rpm -uv packagename.rpm
		# rpm -huv packagename.rpm

3. To remove package,
		# rpm -e packagename.rpm

## Unit 7: Getting Started with `bash`

Basically, when you start your terminal. The program (commonly known as the '*shell*') that executes your commands is by default, `bash`.

### Checking Commands
To check any command's documentation.
	
	# Substitute <command> with the command you want to check
	# Syntax: `man <command>`
	$ man man
	$ man bash

In some cases, a summary can be available through a *flag*.

	$ man --help
	$ bash --help


### Check your shell
You can check what shell you're using by the following commands.

	$ echo $0
	$ echo $SHELL
	
	

##### From [Bash Shell Scripting - 10 Seconds Guide](http://ow.ly/7yc0J)

This Bash shell scripting guide is not a detailed study but a quick reference to the BASH syntax. So lets begin...

### Common Environment Variables
*PATH* - Sets the search path for any executable command. Similar to the PATH variable in MSDOS.

	$ echo $PATH
*HOME* - Home directory of the user.
	
	$ echo $HOME
*MAIL* - Contains the path to the location where mail addressed to the user is stored. 
	
	$ echo $MAIL
*IFS* - Contains a string of characters which are used as word seperators in the command line. The string normally consists of the space, tab and the newline characters. To see them you will have to do an octal dump as follows:

	$ echo $IFS | od -bc

 *PS1* and *PS2* - Primary and secondary prompts in bash. PS1 is set to $ by default and PS2 is set to '>' . To see the secondary prompt, just run the command :

	# Primary Prompt
	$ echo $PS1
	# Secondary Prompt
	$ echo $PS2
	
	# To access Secondary Prompt - PS2
	$ ls | # ... and press enter.
*USER* - User login name.

	$ echo $USER
*TERM* - indicates the terminal type being used. This should be set correctly for editors like Vim to work correctly.

	$ echo $TERM
*SHELL* - Determines the type of shell that the user sees on logging in.

	$ echo $SHELL


#### Some Bash Shell Scripting Rules

The first line in your script must be `#!/bin/bash`
 > ... that is a # (Hash) followed by a ! (bang) followed by the path of the shell. This line lets the environment know the file is a shell script and the location of the shell.

Before executing your script, you should make the script executable. You do it by using the following command:

	$ chmod ugo+x your_shell_script.sh

The name of your shell script must end with a `.sh`. This lets the user know that the file is a shell script. This is not compulsary but is the norm.

### Conditional Statements

#### `If` Statement
The `if` statement evaluates a condition which accompanies its command line.
syntax:

	# Syntax
	if condition_is_true
	then
	   execute commands
	else
	   execute commands
	fi

`if` condition also permits multiway branching. That is you can evaluate more conditions if the previous condition fails.

	if condition_is_true
	then
	   execute commands
	elif another_condition_is_true
	then
	   execute commands
	else
	   execute commands
	fi

Example :

	if grep "linuxhelp" thisfile.html
	then
	   echo "Found the word in the file"
	else
	   echo "Sorry no luck!"
	fi

#### `If`'s Companion - `test`
test is an internal feature of the shell. `test` evaluates the condition placed on its right, and returns either a true or false exit status. For this purpose, 'test' uses certain operators to evaluate the condition. They are as follows:

##### Relational Operators

* -eq - Equal to
* -lt - Less than
* -gt - Greater than
* -ge - Greater than or Equal to
* -le - Less than or Equal to

##### File related tests

* -f file - True if file exists and is a regular file.
* -r file - True if file exists and is readable.
* -w file - True if file exists and is writable.
* -x file - True if file exists and is executable.
* -d file - True if file exists and is a directory.
* -s file - True if file exists and has a size greater than zero.

##### String tests

* -n str - True if string str is not a null string.
* -z str - True if string str is a null string.
* str1 == str2 - True if both strings are equal.
* str - True if string str is assigned a value and is not null.
* str1 != str2 - True if both strings are unequal.
* -s file - True if file exists and has a size greater than zero.

Test also permits the checking of more than one expression in the same line.

* -a  - Performs the AND function
* -o  - Performs the OR function

A few Example snippets of using test

	test $d -eq 25 && echo $d

... which means, if the value in the variable d is equal to 25, print the value. Otherwise don't print anything.

	test $s -lt 50 && do_something
	if [ $d -eq 25 ]
	then
	echo $d
	fi

In this example, I have used square brackets instead of the keyword test - which is another way of doing the same thing.

	if [ $str1 == $str2 ]
	then
	do something
	fi

	if [ -n "$str1" -a -n "$str2" ]
	then
	echo 'Both $str1 and $str2 are not null'
	fi

... here, I have checked if both strings are not null then execute the echo command.

###### Things to remember while using test

If you are using square brackets [] instead of test, then care should be taken to insert a space after the [ and before the ].
test is confined to integer values only. Decimal values are simply truncated.
Do not use wildcards for testing string equality - they are expanded by the shell to match the files in your directory rather than the string.

#### Case Statement

Case statement is the second conditional offered by the shell.

	# Syntax:
	case expression in
	pattern1) execute commands ;;
	pattern2) execute commands ;;
	...
	esac

The keywords here are in, case and esac. The ';;' is used as option terminators. The construct also uses ')' to delimit the pattern from the action.

##### Example:

	...
	echo "Enter your option : "
	read i;

	case $i in
	1) ls -l ;;
	2) ps -aux ;;
	3) date ;;
	4) who ;;
	5) exit
	esac

##### Note
The last case option need not have ;; but you can provide them if you want.

	# Here is another example:
	case `date |cut -d" " -f1` in
	Mon) commands ;;
	Tue) commands ;;
	Wed) commands ;;
	...
	esac

Case can also match more than one pattern with each option.You can also use shell wild-cards for matching patterns.

	...
	echo "Do you wish to continue? (y/n)"
	read ans

	case $ans in
	Y|y) ;;
	[Yy][Ee][Ss]) ;;
	N|n) exit ;;
	[Nn][Oo]) exit ;;
	*) echo "Invalid command"
	esac

In this case, if you enter YeS, YES,yEs and any of its combinations, it will be matched.

This brings us to the end of conditional statements.

### Looping Statements

#### while loop

Syntax

	while condition_is_true
	do
	execute commands
	done

Example:

	while [ $num -gt 100 ]
	do
	sleep 5
	done

	while :
	do
	execute some commands
	done

The code implements a infinite loop. You could also write 'while true' instead of 'while :' .
Here I would like to introduce two keywords with respect to looping conditionals. They are break and continue.

* `break` - This keyword causes control to break out of the loop.
* `continue` - This keyword will suspend the execution of all statements following it and switches control to the top of the loop for the next iteration.

#### until loop
Until complements while construct in the sense that the loop body here is executed repeatedly as long as the condition remains false.

	# Syntax
	until false
	do
	execute commands
	done

Example:

	...
	until [ -r myfile ]
	do
	sleep 5
	done

The code is executed repeatedly until the file myfile can be read.

#### for loop

Syntax

	for variable in list
	do
	execute commands
	done

Example

	...
	for x in 1 2 3 4 5
	do
	echo "The value of x is $x";
	done

Here the list contains 5 numbers 1 to 5. Here is another example:

	for var in $PATH $MAIL $HOME
	do
	echo $var
	done

Suppose you have a directory full of java files and you want to compile those. You can write a script like this:

	...
	for file in *.java
	do
	javac $file
	done

##### Note
You can use wildcard expressions in your scripts.

### Special Symbols Used In BASH Scripting

* `$*` - This denotes all the parameters passed to the script at the time of its execution. Which includes $1, $2 and so on.
* `$0` - Name of the shell script being executed.
* `$#` - Number of arguments specified in the command line.
* `$?` - Exit status of the last command.

The symbols are known as positional parameters. Let me explain the positional parameters with the aid of an example. Suppose I have a shell script called `my_script.sh` . Now I execute this script in the command line as follows :

	$ ./my_script.sh linux is a robust OS

... as you can see, I have passed 5 parameters to the script. In this scenario, the values of the positional parameters are as follows:

* `$*` - will contain the values 'linux','is','a','robust','OS'.
* `$0` - will contain the value `my_script.sh` - the name of the script being executed.
* `$#` - contains the value 5 - the total number of parameters.
* `$$` - contains the process ID of the current shell. You can use this parameter while giving unique names to any temporary files that you create at the time of execution of the shell.
* `$1` - contains the value 'linux'
* `$2` - contains the value 'is' ... and so on.

### The Set And Shift Statements

`set` - Lets you associate values with these positional parameters .

For example, try this:

	$ set `date`
	$ echo $1
	$ echo $*
	$ echo $#
	$ echo $2

`shift` - transfers the contents of a positional parameter to its immediate lower numbered one. This goes on as many times it is called.

Example :

	$ set `date`
	$ echo $1 $2 $3
	$ shift
	$ echo $1 $2 $3
	$ shift
	$ echo $1 $2 $3

To see the process Id of the current shell, try this:

	$ echo $$
	2667

Validate that it is the same value by executing the following command:

	$ ps -f |grep bash

### Make Your BASH Shell Script Interactive

#### `read` statement
Make your shell script interactive. `read` will let the user enter values while the script is being executed. When a program encounters the read statement, the program pauses at that point. Input entered through the keyboard id read into the variables following read, and the program execution continues.
Eg:

	#!/bin/sh
	echo "Enter your name : "
	read name
	echo "Hello $name , Have a nice day."

#### Note:
To see what are the values held by the above environment variables, just do an echo of the name of the variable preceeded with a $. For example, if I do the following:

	$ echo $USER
	telupay

## Unit 8: Establish Network Connectivity

### Configuration tools

There are many network configuration tools today. They are:

* `netconf` - A GUI interactive interface 
* `linuxconf` - A GUI interactive interface, includes `netconf` configuration.
* `netconfig` - A GUI step by step interface
* `ifconfig` - A text based program to configure the network interface. Type `man ifconfig` for info.

These programs will modify values in the following files:

* `/etc/sysconfig/network` - Defines your network and some of its characteristics.
* `/etc/HOSTNAME` - Shows the host name of this host. IF your name is "myhost" then that is exactly the text this file will contain.
* `/etc/resolv.conf` - Specifies the domain to be searched for host names to connect to, the nameserver address, and the search order for the nameservers.
* `/etc/host.conf` - Specifies the order nameservice looks to resolve names.
* `/etc/hosts` - Shows addresses and names of local hosts.
* `/etc/networks` - Provides a database of network names with network addresses similar to the `/etc/hosts` file. This file is not required for operation.
* `/etc/sysconfig/network-scripts/ifcfg-eth*` - There is a file for each network interface. This file contains the IP address of the interface and many other setup variables.

### Analysis Tools

* `netstat` - Displays information about the systems network connections, including port connections, routing tables, and more. The command `netstar -r` will display the routing table.
* `traceroute` - This command can be used to determine the network route from your computer to some other computer on your network or the internet. To use it you can type `route <IPaddress>` of the computer you want to see the route to.
* `nslookup` - Used to query DNS servers for information about hosts.
* `arp` - This program lets the user read or modify their arp cache.
* `tcpdump` - This program allows the user to see TCP traffic on their network.
* `dig(1)` - Send domain name query packets to name servers for debugging or testing.

### Manual Configuration

You can use one of the above tools or configure the network the old fashioned way as follows:

First to use networking on any permanent basis you should setup the file `/etc/sysconfig/network` similar to the example shown:
Assign an ip address with
	
	`ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up`.
	
Tell your machine that a hub is ready for information with the command
	
	`route add -net 192.168.0.0 netmask 255.255.255.0 eth0`.
	
To contact hosts outside your network if a machine with IP address `192.168.1.1` is the gateway use the command

	route add default gw 192.168.1.1 eth0

If using a dialup connection use the command

	route add default ppp0
	# The word `default` says if the packet
	#    is not for a machine on your local network,
	#    send it to the default device.

These settings are not permanent, but go away the next time you boot. They are normally set up in the directory `/etc/sysconfig/network-scripts`.
Add the network interface to the file `/etc/sysconfig/network-scripts/ifcfg-eth*`.

	$ ls /etc/sysconfig/network-scripts/ifcfg-eth*
	
For example the file `ifcfg-eth0` if for the first ethernet interface,
`ifcfg-eth1` for the second, ifcfg-lo is for the local interface.

An example output:

> ![Eth0](/rhel-crash-course/images/ifcfg-eth0.png)

Unless you know what you're doing it is best to use a network configuration tool.


### Networking file formats, examples and considerations

Below are listed some more in depth information about the networking files.

* `/etc/sysconfig/network`

> The `/etc/inittab` file contains the entry "si::sysinit:/etc/rc.d/rc.sysinit" which causes the system at startup to run the `rc.sysinit` script. The `rc.sysinit` file expects to find the file `/etc/sysconfig/network` if networking is to be enabled.

The network file looks like this:

	NETWORKING=yes
	FORWARD_IPV4=false
	HOSTNAME=mymachine.mycompany.com
	DOMAINNAME=mycompany.com
	GATEWAY=192.168.1.1
	GATEWAYDEV=eth0

Where `GATEWAYDEV` is the network interface card that is attached to the network the gateway machine is on. The `GATEWAY` is the actual IP address of the gateway machine.

`/etc/hosts` - Defines local hosts.

	127.0.0.1	localhost	localhost.localdomain
	192.168.1.100	mymachine.mycompany.com	mymachine
	
`/etc/services` - Internet network services list. It associates port numbers with names of services. The file contains three fields which are name, port/protocol, and aliases with an optional comment.

`/etc/protocols` - Describes DARPA internet protocols available from the TCP/IP subsystem. Maps protocol ID numbers to protocol names. It includes protocol name, number, and aliases. The protocol file on my system:

	# /etc/protocols:
	# $Id: protocols,v 1.1 1995/02/24 01:09:41 imurdock Exp $
	#
	# Internet (IP) protocols
	#
	#	from: @(#)protocols	5.1 (Berkeley) 4/17/89
	#
	# Updated for NetBSD based on RFC 1340, Assigned Numbers (July 1992).

	ip	0	IP		# internet protocol, pseudo protocol number
	icmp	1	ICMP		# internet control message protocol
	igmp	2	IGMP		# Internet Group Management
	ggp	3	GGP		# gateway-gateway protocol
	ipencap	4	IP-ENCAP	# IP encapsulated in IP (officially ``IP'')
	st	5	ST		# ST datagram mode
	tcp	6	TCP		# transmission control protocol
	egp	8	EGP		# exterior gateway protocol
	pup	12	PUP		# PARC universal packet protocol
	udp	17	UDP		# user datagram protocol
	hmp	20	HMP		# host monitoring protocol
	xns-idp	22	XNS-IDP		# Xerox NS IDP
	rdp	27	RDP		# "reliable datagram" protocol
	iso-tp4	29	ISO-TP4		# ISO Transport Protocol class 4
	xtp	36	XTP		# Xpress Tranfer Protocol
	ddp	37	DDP		# Datagram Delivery Protocol
	idpr-cmtp	39	IDPR-CMTP	# IDPR Control Message Transport
	rspf	73	RSPF		#Radio Shortest Path First.
	vmtp	81	VMTP		# Versatile Message Transport
	ospf	89	OSPFIGP		# Open Shortest Path First IGP
	ipip	94	IPIP		# Yet Another IP encapsulation
	encap	98	ENCAP		# Yet Another IP encapsulation

`/etc/named.conf` - Used for domain name service to configure named. Other files used are dependent on this file. This file is explained further in the DNS section
`/etc/resolv.conf` - Specifies the domain to be searched for host names to connect to, the nameserver address, and the search order for the nameservers.

	domain mycompany.com
	search mycompany.com mynet.net
	nameserver 192.168.1.100
	nameserver 192.168.199.1
	nameserver 192.168.1.10

The third line specifies that DNS should be tried on my machine first then use the normal nameserver on the fifth line. The fourth line specifies that my machine is running nameservices on another network which is using interface `192.168.199.1`. This assumes the nameserver is set up on my machine which is explained in another section.

`/etc/host.conf` - Specifies the order nameservice looks to resolve names. An example file:

	order hosts, bind
	multi on
	nospoof on

The order specifies that when resolving names to first look in the `/etc/host` file, then use BIND8 (DNS) to resolve the name. The line "multi on" specifies that all valid addresses for a host found in the hosts file should be returned.

The files in `/etc/sysconfig/network-scripts` control your network interfaces. The network interface file is described above in the section "Manual Configuration". If you want or need more in depth knowledge about how these files are used, you will need to read the document "How Linux Works CTDP Guide" or "The CTDP Linux Startup Manual". Otherwise you will need to analyze the system startup scripts which is no small task.


## Unit 9: Administer Users and Groups

UNIX-standard methods of adding, deleting, and modifying user groups:

		groupadd 
		groupmod
		groupdel 

UNIX-standard methods of adding, deleting and modifying user accounts:

		useradd
		usermod
		userdel

UNIX-standard method of administering the /etc/group file.

		gpasswd 


Managing users and groups can be a tedious task, but Red Hat Enterprise Linux provides tools and conventions to make their management easier.
The easiest way to manage users and groups is through the graphical application, User Manager (system-config-users). 


> ![User and Groyp Management](/rhel-crash-course/images/ug1.png)

> ![User and Groyp Management](/rhel-crash-course/images/ug2.png)

> ![User and Groyp Management](/rhel-crash-course/images/ug3.png)

> ![User and Groyp Management](/rhel-crash-course/images/ug4.png)

> ![User and Groyp Management](/rhel-crash-course/images/ug5.png)

> ![User and Groyp Management](/rhel-crash-course/images/ug6.png)



## Unit 10: Manage Files from the Command Line
Red Hat Enterprise Linux uses the Filesystem Hierarchy Standard (FHS) file system structure, which defines the names, locations, and permissions for many file types and directories.

The FHS document is the authoritative reference to any FHS-compliant file system, but the standard leaves many areas undefined or extensible. This section is an overview of the standard and a description of the parts of the file system not covered by the standard.

The two most important elements of FHS compliance are:

* Compatibility with other FHS-compliant systems

* The ability to mount a `/usr/` partition as read-only. This is especially crucial, since `/usr/` contains common executables and should not be changed by users. In addition, since `/usr/` is mounted as read-only, it should be mountable from the CD-ROM drive or from another machine via a read-only NFS mount.


Filesystem Heirarchy Organization

* `/boot` contains the files required to boot the system
* `/home` contains the user files (ie documents, etc)
* `/var` is for variable data files, which include spool directories/files, logging data, transient/temporary files, and the like.
* `/etc` is usually reserved for configuration files that are local to the machine. It shouyld not contain binaries or any executable files.
* `/usr` The `/usr/` directory is for files that can be shared across multiple machines. The `/usr/` directory is often on its own partition and is mounted read-only.
* `/lib` should only contain libraries needed to execute the binaries. This is the repository for the shared objects.
* `/media` contains the subdirectories used as mount points for removable media such as USB drives, DVS's, etc.
* `/mnt` is reserved for temporarily mounted filesystems.
* `/opt` is normally reserved for software and add-on packages that are not part of the default installation. A package that installs to /opt/ creates a directory bearing its name, e.g. `/opt/packagename/`. In most cases, such packages follow a predictable subdirectory structure; most store their binaries in `/opt/packagename/bin/` and their man pages in `/opt/packagename/man/`
* `/sbin` stores binaries essential for booting, restoring, recovering, or repairing the system. The binaries in `/sbin/` require root privileges to use. In addition, `/sbin/` contains binaries used by the system before the `/usr/` directory is mounted; any system utilities used after `/usr/` is mounted is typically placed in `/usr/sbin/`
* `/srv` contains site-specific data served by a Red Hat Enterprise Linux system. This directory gives users the location of data files for a particular service, such as FTP, WWW, or CVS.
* `/sys` The `/sys/` directory utilizes the new sysfs virtual file system specific to the 2.6 kernel. With the increased support for hot plug hardware devices in the 2.6 kernel, the `/sys/` directory contains information similar to that held by /proc/, but displays a hierarchical view device information specific to hot plug devices.
* `/dev` contains the device nodes that represent the physical devices attached to the system or virtual devices provided by the kernel
* `/proc` contains special files that either extract information from the kernel or send information to it. 
* The swap partitions which are used to support virtual memory. In other words, data is written to a swap partition when there is not enough RAM to store the data your system is processing. Recommended swap sizing is:
	* 4G RAM or less : at least 2G swap space
	* 4G - 16G RAM : at least 4G swap space
	* 16G - 64G RAM : at least 8G swap space
	* 64G - 256G RAM : at least 16G swap space
	* 256G - 512G RAM : at least 32G swap space


Common filesystem utilities:

* The `df` command reports the system's disk space usage. 
* The `du` command displays the estimated amount of space being used by files in a directory, displaying the disk usage of each subdirectory. The last line in the output of du shows the total disk usage of the directory; to see only the total disk usage of a directory in human-readable format, use `du -hs`
* The `ls` lists the directory content.
* The `touch` changes file timestamp.
* The `find` command search for a file in a directory hierarchy.
* Other common text file utilities include: `cat`, `tac`, `grep`, `sed`, `awk`, `more`, `less`

## Unit 11: Secure File Access

You can limit the files that can be accessed per User or Group.

	# Syntax
	$ chmod [ugoa][+-=]<permissions> filename

Where:

 * First Argument
  * u - User that owns the file
  * g - File's Group members
  * o - Other users not in the file's group
  * a - All users
 * Second Argument
  * `+` - The permission is added
  * `-` - The permission is removed
  * `=` - Overrides existing permissions with the specified permissions

### `chmod` File Permissions

 * r - Read
 * w - Write
 * x - Execute (also gives permission to change into a directory)
 * X - Execute only if it is a directory or has execute permission for some user
 * s - Set user or group ID on execution
 * t - Sticky bit
 * u - Permissions granted to user who owns the file
 * g - Permissions granted to users in the file’s group
 * o - Permissions granted to the owner of the group and the users in the file’s group

### Examples

Gives the user and group read and write permissions

	chmod ug+rw <filename>

Gives the group read permissions for all files in the current directory and any files and directories in the current directory, recursively

	chmod -R g+r *

Does not let users who aren’t the owner or in the group change into the directory

	chmod o-x <directory>

## Unit 12: Configure General Services

### Configure General Services

### `ssh`

 > See Appendix: Securing Remote Logins with OpenSSH

## Unit 13: Install Linux Graphically

 > AS DEMONSTRATED

## Unit 14: Control the Boot Process

General view of the Linux boot process:

* System startup (BIOS/BootMonitor)
* Stage 1 bootloader (MBR)
* Stage 2 bootloader (LILO, GRUB, or in MS parlance, the NTLDR)
* Kernel
* init() - checks for runlevel, check for the filesystem table, star the services,etc

Exercise : how to reset the root password ?

Understanding runlevels.

+   0 - halt
+   1 - Single user mode
+   2 - Multiuser, without NFS or networking
+   3 - Full multiuser mode
+   4 - unused
+   5 - X11
+   6 - reboot

You may also use the graphical utility to manage the services:

> ![Runlevels](/rhel-crash-course/images/runleveles-1.png)

> ![Runlevels](/rhel-crash-course/images/runlevels-2.png)


## Unit 15: Intermediate Command-Line Tools

### `system-config-*`

> ![system-config-](/rhel-crash-course/images/system-config-.png)

	$ system-config-#tab

> ![system-config-time](/rhel-crash-course/images/system-config-time.png)

	$ system-config-time

## Unit 16: Regular Expressions, Pipelines, and I/O Redirection

### Regular Expressions

Commands can be executed using `grep` via the command line. The literature of Regular Expressions is not covered in this discussion, however regular expression patterns shall be discussed briefly.

 > *See __Cheatsheet__ attached*.

## Unit 17: Network Configuration and Troubleshooting

Common network configuration tools:

* iproute2
* classic route
* ifconfig
* service network

## Unit 18: Analyzing and Storing Logs

Logs are located in /var/ filesystem. Common logs that we usually check are:

* /var/log/boot.log
* /var/log/httpd
* /var/log/maillog
* /var/log/message
* /var/log/secure

Useful tools include:

+ 	dmesg
+ 	lastlog
+ 	history
+ 	logrotate
+ 	redhat-logviewer (or Panel -> System Tools -> System Logs)

## Unit 19: Managing Processes

Common utlities to manage process:

* Terminators (kill, killall)
* Display (ps, pstree, top)
* Setting priority (nice, renice)

In Linux we can set guidelines for the CPU to follow when it is looking at all the tasks it has to do. These guidelines are called niceness or nice value. The Linux niceness scale goes from -20 to 19. The lower the number the more priority that task gets. If the niceness value is high number like 19 the task will be set to the lowest priority and the CPU will process it whenever it gets a chance. The default nice value is zero.

---

# MySQL Crash Course

## Selecting a database

	mysql> USE database;

## Listing databases

	mysql> SHOW DATABASES;

## Listing tables in a db

	mysql> SHOW TABLES;

## Describing the format of a table

	mysql> DESCRIBE table;

## Creating a database

	mysql> CREATE DATABASE db_name;

## Creating a table

Syntax:

	mysql> CREATE TABLE table_name
		(field1_name TYPE(SIZE), field2_name TYPE(SIZE));

Example:

	mysql> CREATE TABLE pet (
		name VARCHAR(20),
		sex CHAR(1),
		birth DATE
		);

## Load tab-delimited data into a table

	mysql> LOAD DATA LOCAL INFILE "infile.txt" INTO TABLE table_name;

## Inserting one row at a time:

	mysql> INSERT INTO table_name
	VALUES ('MyName', 'MyOwner', '2002-08-31');
	# (Use NULL for NULL)

## Retrieving information (general):

Syntax:
	
	mysql> SELECT from_columns FROM table WHERE conditions;

All values:

	SELECT * FROM table;

Some values:

	SELECT * FROM table WHERE rec_name = "value";
	
Multiple critera:

	SELECT * FROM TABLE WHERE rec1 = "value1" AND rec2 = "value2";

## Reloading a new data set into existing table:

	mysql> SET AUTOCOMMIT=1; # used for quick recreation of table
	mysql> DELETE FROM pet;
	mysql> LOAD DATA LOCAL INFILE "infile.txt" INTO TABLE table;

## Fixing all records with a certain value:

	mysql> UPDATE table SET
		column_name = "new_value"
		WHERE record_name = "value";

## Selecting specific columns:

	mysql> SELECT column_name FROM table;

## Retrieving unique output records

	mysql> SELECT DISTINCT column_name FROM table;

## Sorting

	mysql> SELECT col1, col2 FROM table ORDER BY col2;
	# Backwards:
	mysql> SELECT col1, col2 FROM table ORDER BY col2 DESC;

## Date calculations

	# Syntax
	mysql> SELECT
		CURRENT_DATE,
		(YEAR(CURRENT_DATE)-YEAR(date_col)) AS time_diff
		[FROM table];
	# MONTH(some_date) extracts the month
	# 	value and DAYOFMONTH() extracts day.

## Pattern Matching

	mysql> SELECT * FROM table WHERE rec LIKE "blah%";
	# (% is wildcard - arbitrary # of chars)

Find 5-char values:

	SELECT * FROM table WHERE rec like "_____";
	# (_ is any single character)

## Extended Regular Expression Matching

	mysql> SELECT * FROM table WHERE rec RLIKE "^b$";
	# (. for char, [...] for char class, * for 0 or more instances
	# ^ for beginning, {n} for repeat n times, and $ for end)
	# (RLIKE or REGEXP)

##### To force case-sensitivity, use "REGEXP BINARY"

## Counting Rows:

	mysql> SELECT COUNT(*) FROM table;

## Grouping with Counting:

	mysql> SELECT owner, COUNT(*) FROM table GROUP BY owner;
	# (GROUP BY groups together all records for each 'owner')

## Selecting from multiple tables:

	# Example
	mysql> SELECT
		pet.name,
		comment FROM pet, event
		WHERE pet.name = event.name;
	# You can join a table to itself to compare by using 'AS'

## Currently selected database

	mysql> SELECT DATABASE();

## Maximum value:

	mysql> SELECT MAX(col_name) AS label FROM table;

## Auto-incrementing rows:

	mysql> CREATE TABLE table (
		number INT NOT NULL AUTO_INCREMENT,
		name CHAR(10) NOT NULL);
	mysql> INSERT INTO table (name)
		VALUES ("tom"),("dick"),("harry");

## Adding a column to an already-created table:

	# Syntax
	mysql> ALTER TABLE tbl
		ADD COLUMN [column_create syntax]
		AFTER col_name;

## Removing a column:

	mysql> ALTER TABLE tbl DROP COLUMN col;
	# Full ALTER TABLE syntax available at mysql.com

## Batch mode (feeding in a script):

	mysql -u user -p < batch_file
	# Use -t for nice table layout and -vvv for command echoing.

Alternatively
	
	mysql> source batch_file;

## Backing up a database with `mysqldump`

	mysqldump
		--opt
		-u username
		-p database > database_backup.sql
	# Use `mysqldump --opt --all-databases > all_backup.sql`
	# to backup everything.
	#
	# More info at MySQL's docs.

---

# The End

Thanks!
