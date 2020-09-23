# koth-healthcheck
This is a repo for scripts/bins for KoTH-staff to easily do healthcheck on King of the Hill machines.
You need to have a root shell on machine to try the following codes.


```sh
which chattr ls nc curl wget scp cp mv echo printf chmod ps systemctl base64 cat | while read line; do echo -n "$line  "; stat -c "%a" $line; done
```  
(Feel free to add more binaries to it, I think I've missed a lot.)
Expected Output:  
```log
/usr/bin/chattr  755
/usr/bin/ls  755
/usr/bin/nc  777
/usr/bin/curl  755
/usr/bin/wget  755
/usr/bin/scp  755
/usr/bin/cp  755
/usr/bin/mv  755
/usr/bin/echo  755
/usr/bin/printf  755
/usr/bin/chmod  755
/usr/bin/ps  755
/usr/bin/systemctl  755
/usr/bin/base64  755
/usr/bin/cat  755
```
Any error in above output grants a reset. And someone messed up out of scope.

### In Case of King file/service issues/complains:
```sh
ls -la /root/king.txt
lsattr /root/king.txt
```
There should be a king.txt and with no symlinks/alt names.  
List attribute can result following most probable outputs:
```log
--------------e----- king.txt
----ia--------e----- king.txt
-----a--------e----- king.txt
----i---------e----- king.txt
```
All of these are normal.   
Simple restart of king.service should fix most of the king issues. Anything that is persistent after that grants a reset.  
```sh
systemctl restart king
```
