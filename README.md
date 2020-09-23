# koth-healthcheck
This is a repo for scripts/bins for KoTH-staff to easily do healthcheck on King of the Hill machines.
You need to have a root shell on machine to try the following codes.


```sh
which ls chattr ls echo printf chmod ps systemctl base64 cd cat | while read line; do echo -n "$line  "; stat -c "%a" $line; done
```  

`
