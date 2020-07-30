# LinEnum

Enumeration plays a key role while doing privilege escation on target system and performing the enumeration manually require time and effort.
To minimise the time and effort during the penetration test automated enumeration scripts can be used, which checks for very known misconfigurations of files and version details about programs & services running on system which could result in privilege escalation.

LinEnum is one of the available script from different options which can be used for enumeration.
When executed this script run on the context on currently logged in user and gives the output accordingly.
Below is the explanation of script which will be helpful in understanding the scripts output.

## Usage
Download the script using wget or curl.  
`$ wget http://192.168.43.197:8000/LinEnum.sh`  

Change the persmission to executable.  
`$ chmod +x LinEnum.sh`  

Execute the script.  
`$ ./LinEnum.sh`  

## System information:  
This output gives the information about operating system flavour, kernel version, architecture which is helpful while selecting kernel exploits.
Although LinEnum gives first information about system kernel but using kernel exploit should always be the last choise since it can crash the target system.  
![Image](/Img/1.png)

## LoggedIn Users:  
Output shows the current and previoulsy logged in user with time. Later files can be searched which are modified by that specific user around the timeframe which could be helpful in privilege escalation.  
![Image](/Img/2.png)

## passwd file:  
Content of passwd file is helpful for enumerating the list of users avaliable in the system.  
![Image](/Img/4.png)

## Sudo:  
Information regarding sudo shows that which programs can be run as root by current user. It can all program like this case or it can be limited no of command.  
![Image](/Img/6.png)

## Available shells:  
Information of different shell can help for switching to another shell in case if any restricted shell is allocated to user.  
![Image](/Img/7.png)

## Cron jobs:  
Many times systems users have schedules the script which executes as a root user after every specified interval of time. If user is having write permission to these scheduled scripts then it can be modified to execute script of users choice with elevated privileges leading to privilege escation.  
![Image](/Img/8.png)
![Image](/Img/8.2.png)

## Network information:  
Network and IP information gives details about the network interfaces attached to system and ip address of each interface. Systems having multiple interfaces can be connected to another isolated network which cannot be access directly but through pivoting and tunneling through current compromised system.  
![Image](/Img/9.png)

## Running process/services:  
Enumeraing running services can be helpful since if current user is having permission to particular service then abusing those binary can lead to a privilege escalation.  
![Image](/Img/10.png)

## Interesting files:  
List of utilies which can be helpfull for downloading files and compiling programs on target system.  
![Image](/Img/12.png)

## Permissions of sensitive files:  
Output shows the sensitive files to which current user is having read or write access. These misconfigured files can be helpful in escalating privileges, like /etc/shadow file is readable therefore password hash can be grabbed and cracked to obtain root account password.  
![Image](/Img/13.png)
![Image](/Img/5.png)

## SUID files:  
Pragrams with SUID bit set can be executed as root user without root password therefore looking for misconfigured SUID on files could give a root shell.  
![Image](/Img/14.png)

## NFS share:  
NFS shares can be mounted on the system and according to the rights provided changes can be made to system or configuration files for gaining root shell. examples can be writing your own sudoers files, setting SUID permission on binary.  
![Image](/Img/15.png)

## History files:  
History files can give information about the command executed by the user, which could reveal the root password.  
![Image](/Img/16.png)

## Backup files:  
Reading content of backup files could reveal the sensitve information like credentials for accounts and services.  
![Image](/Img/17.png)
