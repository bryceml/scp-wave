# Introduction #

Use scp-wave to transfer the file test10M in /tmp to /tmp on all the hosts named:
lxb03, lxb04...etc to lxb20 as root user and using the verbose output. Two hosts are off-line in purpose.


# Details #

```
[root@lxb ~]# ./scpWave.py -v -u root /tmp/test10M /tmp/test10M -r lxb[03-20]
transferring /tmp/test10M to 18 host(s)...
root@lxb.cern.ch:/tmp/test10M -> root@lxb04:/tmp/test10M...  success
root@lxb.cern.ch:/tmp/test10M -> root@lxb19:/tmp/test10M...  failed
root@lxb04:/tmp/test10M -> root@lxb12:/tmp/test10M...  success
root@lxb.cern.ch:/tmp/test10M -> root@lxb19:/tmp/test10M...  failed
root@lxb.cern.ch:/tmp/test10M -> root@lxb19:/tmp/test10M...  failed
root@lxb04:/tmp/test10M -> root@lxb15:/tmp/test10M...  success
root@lxb12:/tmp/test10M -> root@lxb08:/tmp/test10M...  success
root@lxb04:/tmp/test10M -> root@lxb11:/tmp/test10M...  success
root@lxb12:/tmp/test10M -> root@lxb09:/tmp/test10M...  success
root@lxb15:/tmp/test10M -> root@lxb05:/tmp/test10M...  success
root@lxb08:/tmp/test10M -> root@lxb18:/tmp/test10M...  success
root@lxb12:/tmp/test10M -> root@lxb17:/tmp/test10M...  failed
root@lxb04:/tmp/test10M -> root@lxb06:/tmp/test10M...  success
root@lxb09:/tmp/test10M -> root@lxb10:/tmp/test10M...  success
root@lxb08:/tmp/test10M -> root@lxb07:/tmp/test10M...  success
root@lxb11:/tmp/test10M -> root@lxb14:/tmp/test10M...  success
root@lxb15:/tmp/test10M -> root@lxb13:/tmp/test10M...  success
root@lxb05:/tmp/test10M -> root@lxb03:/tmp/test10M...  success
root@lxb18:/tmp/test10M -> root@lxb20:/tmp/test10M...  success
root@lxb12:/tmp/test10M -> root@lxb17:/tmp/test10M...  failed
root@lxb04:/tmp/test10M -> root@lxb17:/tmp/test10M...  failed
root@lxb06:/tmp/test10M -> root@lxb16:/tmp/test10M...  success

received by: 14 hosts
file_size: 10MB    
elapsed time: 9.32s
```


We see 3 failed transfer to hosts lxb19 and lxb17, which is normal since these hosts are off-line