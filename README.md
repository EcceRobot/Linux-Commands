# Linux-Commands

## Status
### df
This command displays the amount of disk space available on the file system containing each file name argument. 
With no file name, the df command shows the available space on all the currently mounted file systems.
### free
With the free command, admins can see the total amount of free and used physical memory and swap space in the system, as well as the buffers and cache used by the kernel.
### top
top is a set of protocols for networks that performs distributed information processing and displays the tasks on the system that take up the most memory. 
TOP can sort tasks by CPU usage, memory usage and runtime.

## File system
### pwd
The print working directory command displays the name of the current working directory.
### history
The history function shows all the commands used since the start of the current session.

## User management
### passwd
Admins use passwd to update a user's current password.
> sudo passwd new-user

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
