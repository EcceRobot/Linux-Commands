# Linux-Commands

## Status
### Check OS version
Several modes:
> lsb_release -a

> cat /etc/os-release

> hostnamectl

### Check kernel version
> uname -r

### df
This command displays the amount of disk space available on the file system containing each file name argument. 

With no file name, the df command shows the available space on all the currently mounted file systems.
### free
With the free command, admins can see the total amount of free and used physical memory and swap space in the system, as well as the buffers and cache used by the kernel.
### top
top is a set of protocols for networks that performs distributed information processing and displays the tasks on the system that take up the most memory. 

TOP can sort tasks by CPU usage, memory usage and runtime.

### htop
An interactive system-monitor process-viewer and process-manager. It is designed as an alternative to the Unix program top.


### service
Check the status of the running precess 
> sudo service --status-all

> sudo service --status-all | more

> sudo service --status-all | less

(quit with ctrl+z)


Check the status of a defined service
> sudo service name-of_the_service status


## File system
### pwd
The print working directory command displays the name of the current working directory.
### history
The history function shows all the commands used since the start of the current session.

## User management
### passwd
Admins use passwd to update a user's current password.
> sudo passwd new-user

### w
Provides a quick summary of every user logged into a computer, what each user is currently doing, and what load all the activity is imposing on the computer itself.

## Networking
### traceroute
The traceroute function determines and records a route through the internet between two computers and is useful for troubleshooting network/router issues. 

If the domain does not work or is not available, admins can use traceroute to track the IP.
### ifconfig
The iconfig command configures kernel-resident network interfaces at boot time. 

It is usually only needed when debugging or during system tuning.
### nslookup
A user can enter a host name and find the corresponding IP address with nslookup. 

It can also help find the host name.
### speedtest-cli
Command line interface for testing internet bandwidth
First install with
> sudo apt install speedtest-cli


## Log
### > and >>
If you want to store the output of a cli command into a file you can use >.

> speedtest-cli --csv > speedtest-cli-log.txt

will store the results into the file.

The command >> will append the result, without deleting the previuos content of the file.

> speedtest-cli --csv >> speedtest-cli-log.txt


Learn markdown syntax at https://guides.github.com/features/mastering-markdown/
