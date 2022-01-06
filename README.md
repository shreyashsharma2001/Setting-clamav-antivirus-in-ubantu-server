# Setting up Clam-av antivirus in Ubuntu-Server-20.04

1) Installing Antivirus

First install clamav on your ubantu server by
sudo apt install clamav
sudo apt install clamav-daemon

which will include 

clamav - command-line interface

clamav-base - base package

clamav-daemon - scanner daemon

clamav-docs - documentation

clamav-freshclam - virus database update utility

clamav-milter - sendmail integration

clamav-testfiles - test files

libclamav-dev - development files

libclamav9 - library

libclamunrar9 - unrar support


once you have installed the following pacakages you need to check some conf files to make sure everything is fine
cd etc/clamav
there you will see some conf files
1.freshclam.conf
Fresh clam is a tool to update database it can be configured to run when you type command or in background forever
To run it in background make sure to visit

/var/log/clamav/freshclam.log

just to make sure that 'freshclam.log' exists if it's not there 

touch freshclam.log

then check /etc/clamav/freshclam.log you will see something like this

DatabaseOwner STRING
When started by root, drop privileges to a specified user.
Default:

AllowSupplementaryGroups BOOL

Initialize supplementary group access (freshclam must be started by root).

Default: disabled

DatabaseDirectory STRING

Path to a directory containing database files.

Default: /var/lib/clamav

Checks NUMBER

Number of database checks per day.

Default: 12

UpdateLogFile STRING

Enable logging to a specified file. Highly recommended.

Default: disabled.

LogSyslog BOOL

Enable logging to Syslog. May be used in combination with UpdateLogFile.

Default: disabled.

LogFacility STRING

Specify the type of syslog messages - please refer to 'man syslog' for facility names.

Default: LOG_LOCAL6
PidFile STRING

This option allows you to save the process identifier of the daemon to a file specified in the argument.

Default: disabled

LogVerbose BOOL

Enable verbose logging.

Default: disabled


check the 'UpdateLogFile' make sure it points to /var/log/clamav/freshclam.log

then just simply type 

freshclam -d 

to run this service in background

Refer https://linux.die.net/man/5/freshclam.conf to know more about freshclam.conf
