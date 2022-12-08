# Exam_2420
## Part 1:
```
sudo apt update
sudo apt upgrade
```
## Part 2:

for the single character changes. I used `R` command to replace the existing character to the new one
for changing "numbs" to ":digits:" I used `I`
![](vim1.PNG)

## Part 3:
The code is:
```
journalctl -b -p warning -o json
```
To find the options to put I used `/` to search through the man pages. Keywords I searched are 'logs', 'priority', and 'output'
![](Part3-1.PNG)
![](Part3-2.PNG)
![](Part3-3.PNG)

## Part 4:
```
#!/bin/bash

_l="/etc/login.defs"
_p="/etc/passwd"

## get mini UID limit ##
l=$(grep "^UID_MIN" $_l)

## get max UID limit ##
l1=$(grep "^UID_MAX" $_l)

## use awk to print if UID >= $MIN and UID <= $MAX and shell is not /sbin/nologin   ##
awk -F':' -v "min=${l##UID_MIN}" -v "max=${l1##UID_MAX}" '{ if ( $3 >= min && $3 <= max  && $7 != "/sbin/nologin" ) "$_p" /etc/motd
```

## Part 5:
```
[Unit]
Description=run the test_file with the exam script

[Service]
Type=oneshot
ExecStart=/bin/bash /home/vagrant/test_file

[Install]
WantedBy=multi-user.target
```

added the service file to /etc/systemd/system/

## Part 6:
```
[Unit]
Description=Timer to start the test_file.service script

[Timer]
Unit=test_file.service
OnBootSec=60s
Persistent=true

[Install]
WantedBy=multi-user.target
```
