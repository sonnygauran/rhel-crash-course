# Red Hat Crash Course
This training module contains minimal literature to get started and be comfortable with Red Hat Linux and MySQL.

### Gnome Terminal
To start a terminal (Gnome Terminal), start the Run dialog.
And then type the following command to run the terminal.

	# Hit `Ctrl+F2`, the type
	gnome-terminal

> ![Run Dialog](/images/run-dialog.png)
	
or run the terminal through the main menu

> ![Gnome-terminal icon](/images/main-menu-gnome-terminal.png)
> ![Gnome-terminal](/images/gnome-terminal.png)

## Unit 1: Getting Started with the GNOME Graphical Desktop
There are many available graphical applications to the gnome desktop.
Here are the what you'll need to get familiar with:

* Terminal
* Text Editor
* File browser

### Gedit (Gnome Edit)
To start the gnome text editor

	$ gedit

or supply the file(s) after the command. This filenames can be
existing files or files that will be created after *Save* or hiting `Ctrl+S`

	$ gedit file.txt
	
The gnome editor is also accessible via the Main Menu.

> ![Gnome Edit Menu](/images/main-menu-gedit.png)
> ![Gnome Edit](/images/gedit.png)

## Unit 2: Manage Files Graphically with Nautilus
To start the file browser, you can execute the following command.

	$ nautilus

Or just click on the Home icon.

> ![Home icon](/images/home-icon.png)
> ![Nautilus](/images/nautilus.png)


## Unit 3: Configure Local Services
Here, we configure show how to configure the clock and view running processes.

Right-click the Clock on the upper-right corner
	
> ![Home icon](/images/local-services-clock.png)

## Unit 5: Manage System Resources
What to monitor:

* CPU power
* Bandwidth
* Memory
* Storage


1. free. The free command displays system memory utilization. 

> ![free](/images/unit_5-free.png)

2. top. The top command displays pretty much everything. CPU utilization, process statistics, memory utilization — top monitors it all. In addition, unlike the free command, top's default behavior is to run continuously; there is no need to use the watch command.

> ![top](/images/unit_5_1.png)

3. The GNOME System Monitor. If you are more comfortable with graphical user interfaces, the GNOME System Monitor may be more to your liking. Like top, the GNOME System Monitor displays information related to overall system status, process counts, memory and swap utilization, and process-level statistics.

However, the GNOME System Monitor goes a step further by also including graphical representations of CPU, memory, and swap utilization, along with a tabular disk space utilization listing.

> ![GNOME System Monitor](/images/unit_5-gnome_system_monitor2.png)

4. df and du. The df command reports filesystem disk usage. du estimates the filesystem usage.

> ![top](/images/unit_5-df.png)
> ![top](/images/unit_5-du1.png)

	
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

2. To install new package,

    $ rpm -i packagename.rpm
    $ rpm -iv packagename.rpm
    $ rpm -hiv packagename.rpm



# The End

Thanks!
