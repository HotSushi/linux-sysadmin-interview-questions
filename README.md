Linux System Administrator/DevOps Interview Questions
====================================================

A collection of linux sysadmin/devops interview questions. Feel free to contribute via pull requests, issues or email messages.


## <a name='toc'>Table of Contents</a>

  1. [Contributors](#contributors)
  1. [General Questions](#general)
  1. [Simple Linux Questions](#simple)
  1. [Medium Linux Questions](#medium)
  1. [Hard Linux Questions](#hard)
  1. [Expert Linux Questions](#expert)
  1. [Networking Questions](#network)
  1. [MySQL Questions](#mysql)
  1. [DevOps Questions](#devop)
  1. [Fun Questions](#fun)
  1. [Demo Time](#demo)
  1. [Other Great References](#references)


#### [[⬆]](#toc) <a name='contributors'>Contributors:</a>

* [moregeek](https://github.com/moregeek)
* [typhonius](https://github.com/typhonius)
* [schumar](https://github.com/schumar)
* [negesti](https://github.com/negesti)
* peter
* [andreashappe](https://github.com/andreashappe)
* [quatrix](https://github.com/quatrix)
* [biyanisuraj](https://github.com/biyanisuraj)
* [pedroguima](https://github.com/pedroguima)
* Ben
* [bharatnc](https://github.com/bharatnc)


#### [[⬆]](#toc) <a name='general'>General Questions:</a>

* What did you learn yesterday/this week?
* Talk about your preferred development/administration environment. (OS, Editor, Browsers, Tools etc.)
* Tell me about the last major Linux project you finished.
* Tell me about the biggest mistake you've made in [some recent time period] and how you would do it differently today. What did you learn from this experience?
* Why we must choose you?
* What function does DNS play on a network?
> https://www.thegeekstuff.com/2013/12/dns-basics/
> https://opensource.com/article/17/4/introduction-domain-name-system-dns
* What is HTTP?
> https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview
* What is an HTTP proxy and how does it work?
* Describe briefly how HTTPS works.
> https://robertheaton.com/2014/03/27/how-does-https-actually-work/
> https://ssl.trustwave.com/support/support-how-ssl-works.php
* What is SMTP? Give the basic scenario of how a mail message is delivered via SMTP.
* What is RAID? What is RAID0, RAID1, RAID5, RAID10?
> https://superuser.com/questions/287680/how-does-parity-work-on-a-raid-5-array
> https://www.thegeekstuff.com/2010/08/raid-levels-tutorial
* What is a level 0 backup? What is an incremental backup?
* Describe the general file system hierarchy of a Linux system.
* What happens when booting
> 1. BIOS is hardware chip. Checks if all hw components are ok.And then loads certain portion (bootloader) from first sector of hard disk into memory. 2.Bootloader like grub gives user the option to select os 3.bootloader gives control to kernel 4. kernel checks if all hw is ok and starts init  5. init starts all system daemons like to serve network and devices 6. Starts XServer which is graphics daemon 7. user see login


#### [[⬆]](#toc) <a name='simple'>Simple Linux Questions:</a>

* What is the name and the UID of the administrator user?
```
$ whoami
$ id -u username
```
* How to list all files, including hidden ones, in a directory?
> $ ls -l
* What is the Unix/Linux command to remove a directory and its contents?
> $ rm -rf /dir
* Which command will show you free/used memory? Does free memory exist on Linux?
* How to search for the string "my konfi is the best" in files of a directory recursively?
> https://www.ibm.com/developerworks/community/blogs/58e72888-6340-46ac-b488-d31aa4058e9c/entry/search_patterns_in_files_using_linux_grep_command6?lang=en <br>
> $ grep -i[ignore case] -r[recursivelydir] "String\*WithWild" /dir/loc
* How to connect to a remote server or what is SSH?
> https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work <br>
> https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process <br>
> steps 1) TCP 2) Secure Channel 3) User Authorization
* How to get all environment variables and how can you use them?
> Environmental variables are variables that are defined for the current shell and are inherited by any child shells or processes. Environmental variables are used to pass information into processes that are spawned from the shell.
> https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-a-linux-vps <br>
> $ printenv [environment name optional/ all] <br>
> $ env EDITOR=vim xterm <br>
> $ export PATH=$PATH:/home/my_user/bin
* I get "command not found" when I run ```ifconfig -a```. What can be wrong?
> PATH environment may not be containing ifconfig program binary
* What happens if I type TAB-TAB?
> lists possible completions, often directory listings and binary completions
* What command will show the available disk space on the Unix/Linux system?
> $ df -h[human readable in MBs] 
* What commands do you know that can be used to check DNS records?
* What Unix/Linux commands will alter a files ownership, files permissions?
> $ chown username filename.txt  #for a single file owner will be username <br>
> $ chown -R username dir/  <br>
> $ chgrp groupname filename.txt <br>
> $ chown username:groupname filename.txt  #change both
* What does ```chmod +x FILENAME```do?
> file has 3X3 permissions, Read, write, executable permissions for user, group, others <br>
> chmod 644 filename (give read, write (4+2 = 6) to user and read (4) to group and others.) <br>
> chmod u+r,g+x filename <br>
> chmod o-rw filename <br>
> chmod +x filename (all groups get +x)
* How does umask work?
> The mask is applied whenever a file is created. If the mask has a bit set to "1", that means the corresponding file permission will always be disabled when files are subsequently created. A bit set to "0" in the mask means that the corresponding permission will be determined by the requesting process <br>
> umask is always applied after any chmod/ file creation. default: 002, no file will ever have write acces for others.
> https://www.computerhope.com/unix/uumask.htm
* What does the permission 0750 on a file mean?
> 0-111-101-000 = --rwx-r-x---- -> user can r,w,x, group can r,x, others cant do anything 
* What does the permission 0750 on a directory mean?
> initial 0 has no effect in both file and directory. same as above.<br>
> read => ls
> write => touch
> executable => cd
* How to create and delete Users and make them sudo?
> $ adduser usr (both need sudo permission) <br>
> $ deluser usr <br>
> add the user to the file /etc/sudoers
* How to add a new system user without login permissions?
> $ adduser [-m for home dir] usr <br>
> $ usermod -L usr <br>
> to List all users see /etc/passwd
* How to add/remove a group from a user?
> https://www.howtogeek.com/50787/add-a-user-to-a-group-or-second-group-on-linux/ <br>
> $ groupadd GG <br>
> $ usermod -g primarygroupname usr <br>
> $ usermod -a[append for secondary groups] -G[secondary groups] groupname1,groupname2 username <br>
> a user can belong to a single primary group, for secondary groups use -a
> $ groups # list groups current user belongs to 
> $ gpasswd -d user group
* What is a bash alias?
> A Bash alias is essentially nothing more than a keyboard shortcut
> $ alias rm="rm -i"
> $ unalias rm
* What does CTRL-c do?
> sends SIGINT interrupt to the program <br>
> https://stackoverflow.com/questions/4042201/how-does-sigint-relate-to-the-other-termination-signals
* What is in /etc/services?
> https://www.lifewire.com/what-is-etc-services-2196940 <br>
> some port no are reserved, this file shows \< service, port no, TCP/UDP \> <br>
>  programs can do a getportbyname() sockets call in their code in order to understand what port they should use
* How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)
> $ command > out 2>error  // stdout default is program > output , 2 gives error output <br>
> $ command &> out    // >> is append > is start afresh
* What is the difference between UNIX and Linux.
> https://superuser.com/questions/43149/what-is-the-difference-between-unix-and-linux <br>
> different from scratch, proprietary, POSIX compliant
* What is the difference between Telnet and SSH?
> I use telnet (port 23) to check if port is open, you can form HTTP get requests too.Telnet has no encryption.<br>
> $ telnet localhost 80
> Historically it used to allow shell access, now it doesnt
* Explain the three load averages and what do they indicate. What command can be used to view the load averages?
> $ uptime <br>
> https://www.howtogeek.com/194642/understanding-the-load-average-on-linux-and-other-unix-like-systems/
* What is a Linux kernel module?
* Walk me through the steps in booting into single user mode to troubleshoot a problem.
* Walk me through the steps you'd take to troubleshoot a 404 error on a web application you administer.

#### [[⬆]](#toc) <a name='medium'>Medium Linux Questions:</a>

* What do the following commands do and how would you use them?
 * ```tee```
> input from standard input and output to standard output and to file
 * ```awk```
> https://www.digitalocean.com/community/tutorials/how-to-use-the-awk-language-to-manipulate-text-in-linux
 * ```tr```
> https://www.thegeekstuff.com/2012/12/linux-tr-command
 * ```cut```
> https://www.thegeekstuff.com/2013/06/cut-command-examples/
 * ```tac```
 * ```curl```
 * ```wget```
 * ```watch```
 * ```head```
 * ```tail```
* What does an ```&``` after a command do?
> If a command is terminated by the control operator &, the shell executes the command in the background in a subshell. The shell does not wait for the command to finish, and the return status is 0. 
* What does ```& disown``` after a command do?
> src: https://www.digitalocean.com/community/tutorials/how-to-use-bash-s-job-control-to-manage-foreground-and-background-processes <br>
> $ jobs # displays background processes either running or stopped <br>
> $ bg %i # starts ith background process <br>
> $ fg %i # brings ith background process to front <br>
> $ ping google.com &  # starts process in bg <br>
> $ ping google.com  # running CTR+Z stops process in background <br>
> $ kill -STOP %i # suspends background processs <br>
> $ disown %i # removes process i from job list and will continue working even if terminal closed (ignores SIGHUP) <br>
> $ nohup ping google.com & # same as above
* What is a packet filter and how does it work?
> https://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-3.html <br>
>A packet filter is a piece of software which looks at the header of packets as they pass through, and decides the fate of the entire packet. It might decide to DROP/ACCEPT the packet. https://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-6.html. Has 3 in-built chains(Firewalls), INPUT, OUTPUT (for packets destined for this box), FORWARD (for other box). Possible to create our own chain. And link it to existing chains. Possible to modify each chain. Each chain entry is a rule which has action ACCEPT/ DROP.<br>
> $ iptables -L # List all rules
> $ iptables -I INPUT -s 10.10.10.10 -j DROP # blocks ip
* What is Virtual Memory?
> BLOG
* What is swap and what is it used for?
> BLOG (swap is used for swapping memory frames out to hard disk)
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
>Split-Brain DNS, Split-Horizon DNS, or Split DNS are terms used to describe when two zones for the same domain are created, one to be used by the internal network, the other used by the external network (usually the Internet). A Split DNS infrastructure is used to direct internal hosts to an internal domain name server for name resolution and external hosts to an external domain name server for name resolution. https://www.youtube.com/watch?v=yPH02ZcfFtc <br>
> Some internal resources can be made private by only listing them in intranet dns server <br>
> example staging.housing.com
* What is the sticky bit?
> $ chmod +t /opt/dump/ <br>
> $ chmod 1757 /opt/dump/ <br>
> Sticky Bit is mainly used on folders in order to avoid deletion of a folder and it’s content by other users though they having write permissions on the folder contents.If Sticky bit is enabled on a folder, the folder contents are deleted by only owner who created them and the root user.<br>
> $ ls -l => -rwxr-xrwt  t-> others have executable permission, if T -> others dont have exe permission
* What does the immutable bit do to a file?
> Prevents a file from accidental changes, like automatic software update changing configuration. cant be modified, deleted, removed, no linking allowed
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
> https://stackoverflow.com/questions/185899/what-is-the-difference-between-a-symbolic-link-and-a-hard-link
* What is an inode and what fields are stored in an inode?
> inode is a filesystem object that can represent a file or directory. Identified by integer called inode-number. max no is fixed. `ls -i` prints inode no.  info stored -> deviceid, link count(hardlinks), ownership(userid, groupid), size, timestamps,no of IO blocks, pointer to blocks. There is a table which maps inode no to respective inodes. 2nd column in ls tells no of links.<br>
> $ stat a #tells the inode details
* What is SNMP and what is it used for?
> BLOG
* What is SSH port forwarding?
> BLOG
* What is the difference between local and remote port forwarding?
> BLOG and Stack overflow 
* What are the steps to add a user to a system without using useradd/adduser?
> change relevant files `/etc/passwd` `/etc/group`
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
> inodes are full
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
> inode data is not cleared yet, because its being used by some process
* Describe how 'ps' works.
> Reads contents of /proc/\*
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
> Linux takes care. init waits for its children.
* Explain briefly each one of the process states.
* How to know which process listens on a specific port?
> $ sudo netstat -nlp | grep :80 # n-> show names of hosts, ports l-> listening, p-> show pid <br>
> `lsof` can also be used, lsof lists all open file handles, netstat all open network connections
* What is a zombie process and what could be the cause of it?
> https://github.com/angrave/SystemProgramming/wiki/Forking,-Part-2:-Fork,-Exec,-Wait <br>
> **A good parent waits for its children**
> A child process after finishing execution becomes zombie. Linux does this so that the parent process can know the status of its child. Zombies are light weight, but if too many, no more new processes can be created. How to kill zombie? `wait for it`. When parent waits for child, child (even if zombie) will return status and die, no residues. What if you dont wait? Linux has your back.. the supreme parent process `init` waits for all of its children, so if the parent process dies without waiting for children, all the children will get reassigned to init and then die. MORE: https://github.com/angrave/SystemProgramming/wiki/Forking,-Part-2:-Fork,-Exec,-Wait
* You run a bash script and you want to see its output on your terminal and save it to a file at the same time. How could you do it?
> use tee
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.
> enables ip_forwarding
> So, let's say you have two NICs, one (NIC 1) is at address 192.168.2.1/24, and the other (NIC 2) is 192.168.3.1/24. If forwarding is enabled, and a packet comes in on NIC 1 with a "destination address" of 192.168.3.8, the router will resend that packet out of the NIC 2.
* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* What is a wildcard certificate?
> A single wildcard certificate for \*.example.com, will secure all these domains:[2]
> payment.example.com
> contact.example.com
> login-secure.example.com
* Which Linux file types do you know?
>- : regular file
>d : directory
>c : character device file
>b : block device file
>s : local socket file
>p : named pipe
>l : symbolic link 
> https://linuxconfig.org/identifying-file-types-in-linux
* What is the difference between a process and a thread? 
* And parent and child processes after a fork system call?
> Different return value, pids, program counter, data is copied 
* What is the difference between exec and fork?
> fork creates a duplicate child process and start executing where it left off. return value is 0 for child, pid for parent. The exec call is a way to basically replace the entire current process with a new program. There is pattern fork, exec, wait which bash uses (see diagram here https://stackoverflow.com/questions/1653340/differences-between-fork-and-exec). Note Forking creates zombies.
* How to create a cronjob?
> crontab -e
* What is "nohup" used for?
> It tells the new process to ignore SIGHUP. It is the signal sent by the kernel when the parent shell is closed.
* What is the difference between these two commands?
 * ```myvar=hello```
 > creates a shell variable, can be printed with $myvar,  to pass environment variables to a process<br>
 > $ env GREP_OPTIONS='-v' grep one test.txt
 * ```export myvar=hello```
 > creates environment variable
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you limit process memory usage?
> $ ulimit -d 10000 -m 10000 -v 10000 #-d data segment size -m max memory size-v virtual memory size
* Do you know of any alternative shells? If so, have you used any?
> I've used zsh, but i did it just for the themes. It allows me to select suggestions for ls.
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
* How can you tell if the httpd package was already installed?
> $ dpkg -l | grep httpd
* How can you determine which package is better: openssh-server-5.3p1-118.1.el6_8.x86_64 or openssh-server-6.6p1-1.el6.x86_64 ?
> <foo>_<VersionNumber>-<DebianRevisionNumber>_<DebianArchitecture>.deb
* Can you explain to me the difference between block based, and object based storage?

#### [[⬆]](#toc) <a name='network'>Networking Questions:</a>
http://www.bogotobogo.com/DevOps/DevOps-Sys-Admin-Interview-Questions-Networks.php
* What is net Masking?
> https://www.netfilter.org/documentation/HOWTO/networking-concepts-HOWTO-4.html
* What is localhost and why would ```ping localhost``` fail?
> if there is a DROP rule in iptables
* What is the similarity between "ping" & "traceroute" ? How is traceroute able to find the hops.
> traceroute incrementally changes TTL and returns with the information
* What is the command used to show all open ports and/or socket connections on a machine?
> netstat
* Is 300.168.0.123 a valid IPv4 address?
> no
* Which IP ranges/subnets are "private" or "non-routable" (RFC 1918)?
* What is http proxy? forward and reverse
> proxy is a computer acting on your behalf. X, Y, Z -> Forward proxy,
* What is a VLAN?
* What is ARP and what is it used for?
* What is the difference between TCP and UDP?
* What is the purpose of a default gateway?
* What is command used to show the routing table on a Linux box?
> $ sudo route
* A TCP connection on a network can be uniquely defined by 4 things. What are those things?
> (remote-ip-address, remote-port, source-ip-address, source-port)
* When a client running a web browser connects to a web server, what is the source port and what is the destination port of the connection?
* How do you add an IPv6 address to a specific interface?
* You have added an IPv4 and IPv6 address to interface eth0. A ping to the v4 address is working but a ping to the v6 address gives yout the response ```sendmsg: operation not permitted```. What could be wrong?
* What is SNAT and when should it be used?
* Explain how could you ssh login into a Linux system that DROPs all new incoming packets using a SSH tunnel.
* How do you stop a DDoS attack?
* How can you see content of an ip packet?
* What is IPoAC (RFC 1149)?


#### [[⬆]](#toc) <a name='hard'>Hard Linux Questions:</a>
* What is bash quick substitution/caret replace(^x^y)?
* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?* How can you get Host, Channel, ID, LUN of SCSI disk?
* What is a tunnel and how you can bypass a http proxy?
* What is the difference between IDS and IPS?
* What shortcuts do you use on a regular basis?
* What is the Linux Standard Base?
* What is an atomic operation?
* Your freshly configured http server is not running after a restart, what can you do?
* What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?
* Can you have several HTTPS virtual hosts sharing the same IP?
* I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?
* Did you ever create RPM's, DEB's or solaris pkg's?
* Describe the mknod command and when you'd use it.
* What does ```:(){ :|:& };:``` do on your system?
* How do you catch a Linux signal on a script?
* Can you catch a SIGKILL?
* What is MAJOR and MINOR numbers of special files?
* What's happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?
* How to force/trigger a file system check on next reboot?
* Describe the linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt.
* How can you list the contents of a package?
* What's a chroot jail?
* What is a runlevel and how to get the current runlevel?
* When trying to umount a directory it says it's busy, how to find out which PID holds the directory?
* What's LD_PRELOAD and when it's used?
* You ran a binary and nothing happened. How would you debug this?
* What are cgroups? Can you specify a scenario where you could use them?
* How can you remove/delete a file with file-name consisting of only non-printable/non-type-able characters?
* How can you increase or decrease the priority of a process in Linux?
* What are run-levels in Linux?


#### [[⬆]](#toc) <a name='expert'>Expert Linux Questions:</a>

* A running process gets ```EAGAIN: Resource temporarily unavailable``` on reading a socket. How can you close this bad socket/file descriptor without killing the process?




#### [[⬆]](#toc) <a name='mysql'>MySQL questions:</a>

* How do you create a user?
* How do you provide privileges to a user?
* What is the difference between a "left" and a "right" join?
* Explain briefly the differences between InnoDB and MyISAM.
* Describe briefly the steps you need to follow in order to create a simple master/slave cluster.
* Why should you run "mysql_secure_installation" after installing MySQL?
* How do you check which jobs are running?
* How would you take a backup of a MySQL database?

#### [[⬆]](#toc) <a name='devop'>DevOps Questions:</a>

* Can you describe your workflow when you create a script?
* What is GIT?
* What is a dynamically/statically linked file?
* What does "./configure && make && make install" do?
* What is puppet/chef/ansible used for?
* What is Nagios/Zenoss/NewRelic used for?
* What is Jenkins/TeamCity/GoCI used for?
* What is the difference between Containers and VMs?
* How do you create a new postgres user?
* What is a virtual IP address? What is a cluster?
* How do you print all strings of printable characters present in a file?
* How do you find shared library dependencies?
* What is Automake and Autoconf?
* ./configure shows an error that libfoobar is missing on your system, how could you fix this, what could be wrong?
* What are the advantages/disadvantages of script vs compiled program?
* What's the relationship between continuous delivery and DevOps?
* What are the important aspects of a system of continuous integration and deployment?
* How would you enable network file sharing within AWS that would allow EC2 instances in multiple availability zones to share data?

#### [[⬆]](#toc) <a name='fun'>Fun Questions:</a>

* A careless sysadmin executes the following command: ```chmod 444 /bin/chmod ``` - what do you do to fix this?
* I've lost my root password, what can I do?
* I've rebooted a remote server but after 10 minutes I'm still not able to ssh into it, what can be wrong?
* If you were stuck on a desert island with only 5 command-line utilities, which would you choose?
* You come across a random computer and it appears to be a command console for the universe. What is the first thing you type?
* Tell me about a creative way that you've used SSH?
* You have deleted by error a running script, what could you do to restore it?
* What will happen on 19 January 2038?
* How to reboot server when reboot command is not responding?


#### [[⬆]](#toc) <a name='demo'>Demo Time:</a>

* Unpack test.tar.gz without man pages or google.
> tar zcvf fred.tar.gz fred # z-> use gzip, c-> compress, v->verbose, f-> filename
> tar zxvf fred 
* Remove all "*.pyc" files from testdir recursively?
> rm -rf # not work, f is to force (dont ask ex. for write protected files) r is to delete directory
> find . -type f -name '*.sh' -exec rm {} +
* Search for "my konfu is the best" in all *.py files.
> find . -type f -name "*.py" -exec grep -i "my konfu is the best" {} +
* Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files.
> sed -i -e 's/mkitb/ialjm/g' hello.txt
* Test if port 443 on a machine with IP address X.X.X.X is reachable.
> telnet host port #connection established -> OK #connection timeout -> Firewall blockng # connection refused -> not listening
* Get http://myinternal.webserver.local/test.html via telnet.
* How to send an email without a mail client, just on the command line?
* Write a ```get_prim``` method in python/perl/bash/pseudo.
* Find all files which have been accessed within the last 30 days.
* Explain the following command ```(date ; ps -ef | awk '{print $1}' | sort | uniq | wc -l ) >> Activity.log```
* Write a script to list all the differences between two directories.
* In a log file with contents as ```<TIME> : [MESSAGE] : [ERROR_NO] - Human readable text``` display summary/count of specific error numbers that occurred every hour or a specific hour.


#### [[⬆]](#toc) <a name='references'>Other Great References:</a>

Some questions are 'borrowed' from other great references like:

* https://github.com/darcyclarke/Front-end-Developer-Interview-Questions
* https://github.com/kylejohnson/linux-sysadmin-interview-questions/blob/master/test.md
* http://slideshare.net/kavyasri790693/linux-admin-interview-questions
