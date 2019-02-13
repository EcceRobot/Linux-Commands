# Linux-Commands

## System
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
> df -h

_-h, --human-readable  print sizes in powers of 1024 (e.g., 1023M)_

### free
With the free command, admins can see the total amount of free and used physical memory and swap space in the system, as well as the buffers and cache used by the kernel.
### top
top is a set of protocols for networks that performs distributed information processing and displays the tasks on the system that take up the most memory. 

TOP can sort tasks by CPU usage, memory usage and runtime.

### htop
An __interactive__ system-monitor process-viewer and process-manager. It is designed as an alternative to the Unix program top.


### service
Check the status of the running precess (quit with ctrl+z) 
> sudo service --status-all

> sudo service --status-all | more

> sudo service --status-all | less

Check the status of a defined service
> sudo service _name_of_the_service_ status

Start, Stop and Restart
> sudo service _name_of_the_service_ start
> sudo service _name_of_the_service_ stop
> sudo service _name_of_the_service_ restart

## Packages
### apt
> sudo apt update

> sudo apt upgrade

> sudo apt install _package_name_

> sudo apt remove _package_name_

> sudo apt purge _package_name_

> sudo apt autoremove

> sudo apt clean

### dpkg
> sudo dpkg -i _package_name_.deb

## File
### chmod
Permission to read, write, & execute for owner, group and others, recursive
> sudo chmod -R 777 _folder_name_

### find
Cercare file per nome, non case sensitive
> find / -iname _nome_file_

Cercare file per nome, case sensitive
> find / -name _nome_file_

Cercare file con nome contenente una parte indicata
> find / -iname "*.csv"

Cercare file per dimensione
Il comendo seguente trova tutti i file, con qualunque nome, che abbiano dimensioni maggiori di 1000M
> find / -size +1000M -iname "*"

Cerca file contenti la stringa indicata nel percorso indicato
> grep -Iri 'cane' /home


## Terminal
### pwd
The print working directory command displays the name of the current working directory.
### history
The history function shows all the commands used since the start of the current session.
### clear
The terminal screen gets cleared.

## User management
### passwd
Admins use passwd to update a user's current password.
> sudo passwd _new_user_name_

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

and then just 
> $ speedtest-cli

## Log
### > and >>
If you want to store the output of a cli command into a file you can use >.

> speedtest-cli --csv > _name_of_the_file_.txt

will store the results into the file.

The command >> will append the result, without deleting the previuos content of the file.


> speedtest-cli --csv >> _name_of_the_file_.txt

## SSH
> sudo ssh -p _port_number_ _ip_address_ -l _user_name_



## Running Linux in Virtualbox 
### Shared folder permissions
> sudo adduser _user_name_ vboxsf



##

Learn markdown syntax at https://guides.github.com/features/mastering-markdown/
