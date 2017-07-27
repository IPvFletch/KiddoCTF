# KiddoCTF

## Introduction & Audience

This CTF is aimed at students ages 12-15 (Middle School). These challenges are meant as more of a pre-cursor for PicoCTF, EasyCTF, HSCTF, and the like.

Since this CTF is based on Docker, some assistance is required by a mentor or teacher to help the student get the Docker Linux container instance up and running.

To submit answers, have the students write it down on paper or on their computer using an app like notepad or notes.

Some of the challenges have extra practice commands to help the student learn more

Spoil Alert: The flags are all in the Dockerfile so don't let the student see that first!


## DOCKER LINUX CTF

#### 01 linux i
* find a file that is the flag
* use `cd` and `ls` to reveal file flag
* practice: try `ls -l /home`

#### 02 linux ii
* cd ~/ (homedir)
* use `ls --help` to find the hidden .dir directory(s)
* `cat file` reveals the flag
* practice: try `cat /etc/passwd` or `cat /etc/shadow`

#### 03 linux iii
* run cat` or `strings` on /tmp/.flag3
* pipe the output (`|`) to grep, ex. `cat file | grep FLAG`
* practice: try `cat /var/log/yum.log` to see what apps have been erased/installed

#### 04 base64 encoded string
* Base64 decode the file /tmp/.flag4
* use `base64 --help`
* practice: try `echo YOURNAME | base64 | base64 -d`

#### 05 linux iv
* find flag on local port
* use nc to connect to google.com 80
* use curl to connect to google.com:80
* find the flag on localhost:80 to get the challenge
* you need to base64 decode this string to get the flag
* pipe the output to base64
* or echo it and pipe to base64

#### 06 linux v find a user id
* use `ps --help` to find the user of the `webserver` process
* using `id`, find the uid of user
* flag is the other user who belongs to that same group
* hint: look at /etc/group

#### 07 linux vi
* look in the www user's files to find the flag
* use `ls -l` to see dir/file permissions
```
    drwxr-xr-x => r = read, w = write, x = exec/cd
    the first 1 bit is for if it's a directory
    the next 3 bits are the owner's permissions
    the next 3 bits are the group's permissions
    the last 3 bits are everyone else's permissions
```

#### 08 networking
* find the routing table
* the flag is the default route for destination 0.0.0.0
* netstat --help

#### 09 visit a web service
* `curl localhost:8080`
* find an HTML comment containing the flag

#### 10 web site
* `curl localhost:8080`
* `curl --help` to find out how to display "headers"
* look at the "cookies" being set by the server
* b64 decoder reveals flag

#### 11 run a python script
* run python
* paste the below script line by line and let it run
* find the `json` variable's `type` to reveal the flag
```
list = []
list.append('a')
list.append('b')
json = {'a': 'ayyy', 'b': 'be cool man'}
print json['a'] + ' ' + json['b']
print type(list)
print list[1]
print len(json)
print type(json)
```

#### 12 unknown filetype
* find out what kind of filetype `oddfile` is
* `head -1 oddfile`
* http://www.garykessler.net/library/file_sigs.html
* or `file <file>`
* unzip it to reveal the flag

#### 13 nmap to find a [local] hidden port
* `nmap localhost`
* flag is the service name for the listener port beginning with 3

#### 14 analyze a tcpdump
* examine the TCP Dump (Packet Capture) and find the flag
* `tcpdump -r flag.dmp`
* use the `-n` flag to not resolve hostnames
* use `-A` to display the data trasnferred
* look for the flag data being sent > 216.58.218.142.80

# END


### Related
* https://`thub.com/EasyCTF/writeups-2014/blob/master/045-linux-basics-4.md
* https://jacobedelman.gitbooks.io/hsctf-3-practice-problems/content/

