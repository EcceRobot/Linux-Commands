# Linux-Commands

## System

### Users
Add user to sudo group and let him use "sudo"
> sudo adduser _user_name_ sudo

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
 
### Services with _service_ command (Debian 8 Jessie)
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

### Services with _systemd_ command (Debian 9 Stretch)

The most notable distribution using systemd is Fedora. Though it is used by many others. Additionally, with Debian having chosen to go with systemd over upstart, it will become the defacto upstart system for most distributions (ubuntu has already announced they will be dropping upstart for systemd).
List services:
> systemctl list-unit-files

Start service:
> systemctl start _name_of_the_service_

Stop service:
> systemctl stop _name_of_the_service_

Enable service (at startup)
> systemctl enable _name_of_the_service_

Disable service
> systemctl disable _name_of_the_service_


### fonts

Install a font manually by downloading the appropriate .ttf or otf files and placing them into _/usr/local/share/fonts_.

These files should have the permission 644 (-rw-r--r--), otherwise they may not be usable. 

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

### rmdir 

Remove a folder
```
rmdir <directoryname>
```

### rm -rf

Remove a folder and all content

```
rm -rf <directoryname>
```
## find a biggest files in /

```
sudo du -a / 2>/dev/null | sort -n -r | head -n 20
```


### chmod
Permission to read, write, & execute for owner, group and others, recursive
> sudo chmod -R 777 _folder_name_

### find
Cercare file per nome, non case sensitive
> find / -iname "_nome_file_"

Cercare file per nome, case sensitive
> find / -name "_nome_file_"

Cercare file con nome contenente una parte indicata
> find / -iname "*.csv"

Cercare file per dimensione
Il comendo seguente trova tutti i file, con qualunque nome, che abbiano dimensioni maggiori di 1000M
> find / -size +1000M -iname "*"

Cerca file contenti la stringa indicata nel percorso indicato
> grep -Iri 'cane' /home


## Terminal management
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

### IP assignment
Go in _/etc/network/interfaces_ configuration file

> sudo nano /etc/network/interfaces

#### DHCP
_auto eth0_

_allow-hotplug eth0_

_iface eth0 inet dhcp_

#### static IP
_auto eth0_

_iface eth0 inet static_

_address 192.0.2.7_

_netmask 255.255.255.0_

_gateway 192.0.2.254_

and then assign the **DNS** in _/etc/resolv.conf_ configuration file
> nameserver 8.8.8.8

after the setting restart the service
> systemctl restart networking


#### static IP without internet
_auto eth0_

_iface eth0 inet static_

_address 192.0.2.7_

_netmask 255.255.255.0_



    auto eth0

    iface eth0 inet static

       address 192.0.2.7

       netmask 255.255.255.0

       gateway 192.0.2.254



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

### client
> sudo ssh -p _port_number_ _ip_address_ -l _user_name_

### server
You need a SSH server installed
> $ sudo apt-get install openssh-server

On Debian, the default behavior of OpenSSH server is that it will start automatically as soon as it is installed. 

You can also check whether OpenSSH server is running on it with the following command:
> $ sudo systemctl status ssh

## Running Linux in Virtualbox 
### Shared folder permissions
> sudo adduser _user_name_ vboxsf

## Java
Check if Java is already installed:
> java -version

If Java is not currently installed, you'll see the following output:
> -bash: java: command not found

Execute the following command to install OpenJDK:
> sudo apt install default-jre

This command will install the Java Runtime Environment (JRE). This will allow you to run almost all Java software.
Verify the installation again.

You may need the Java Development Kit (JDK) in addition to the JRE in order to compile and run some specific Java-based software. 

To install the JDK, execute the following command, which will also install the JRE:
> sudo apt install default-jdk

Verify that the JDK is installed by checking the version of javac, the Java compiler:
> javac -version

## Solve backlight issue

Create file /usr/share/X11/xorg.conf.d/20-intel.conf

and write:

```
Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    Option       "Backlight" "intel_backlight"
EndSection
```
and then reboot the system.


## Others

It might be useful to execute the script in the background by using the option "nohup"
```
sudo nohup eclipse
```
and so you can close terminal without closing eclipse.

## Processing Headless

https://github.com/processing/processing/wiki/Running-without-a-Display

You need to install
```
sudo apt-get install xvfb libxrender1 libxtst6 libxi6 
```
and then you can launch the exported application
```
xvfb-run ./my-processing-application
```
if running on a servcer it could be useful to execute in the background
```
nohup xvfb-run ./my-processing-application
```


## Understanding where a command is located
```
which python3
```
would return
```
/usr/bin/python3
```

## Command at startup

Devo lanciare il comando
```
export VISUAL=nano; crontab -e
```   
che mi permette di aprire il file di crontab da nano e non da vim come sarebbe di default, e poi dentro inserisco la voce:
```   
@reboot <mycommand>
```   
altrimento posso creare uno script al cui interno inserisco:
```
#write out current crontab
crontab -l > temp_mycron.txt
#echo new cron into cron file
echo "@reboot <mycommand>" >> temp_mycron.txt
#install new cron file
crontab temp_mycron.txt
rm temp_mycron.txt
```




Learn markdown syntax at https://guides.github.com/features/mastering-markdown/
