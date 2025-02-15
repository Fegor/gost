# gost

```
wget https://github.com/fegor/gost/raw/main/install.sh && bash install.sh
```

## GOST 各协议带宽性能测试

服务器配置 2C2GB 带宽10Gbps


<details><summary>wss</summary><blockquote>

服务端
```
gost -L wss://:8443
```
客户端
```
gost -L tcp://:5201/127.0.0.1:5201 -F wss://gost.brook-5.com:8443 
```
```
[root@gostclient ~]# iperf3 -c 127.0.0.1 -R
Connecting to host 127.0.0.1, port 5201
Reverse mode, remote host 127.0.0.1 is sending
[  4] local 127.0.0.1 port 39190 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec   404 MBytes  3.39 Gbits/sec                  
[  4]   1.00-2.00   sec   383 MBytes  3.21 Gbits/sec                  
[  4]   2.00-3.00   sec   347 MBytes  2.91 Gbits/sec                  
[  4]   3.00-4.00   sec   417 MBytes  3.50 Gbits/sec                  
[  4]   4.00-5.00   sec   355 MBytes  2.97 Gbits/sec                  
[  4]   5.00-6.00   sec   347 MBytes  2.91 Gbits/sec                  
[  4]   6.00-7.00   sec   335 MBytes  2.81 Gbits/sec                  
[  4]   7.00-8.00   sec   355 MBytes  2.97 Gbits/sec                  
[  4]   8.00-9.00   sec   356 MBytes  2.98 Gbits/sec                  
[  4]   9.00-10.00  sec   354 MBytes  2.96 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  3.59 GBytes  3.08 Gbits/sec   17             sender
[  4]   0.00-10.00  sec  3.57 GBytes  3.07 Gbits/sec                  receiver

iperf Done.
```
</blockquote></details>

<details><summary>tls</summary><blockquote>

服务端
```
gost -L tls://:8443
```
客户端
```
gost -L tcp://:5201/127.0.0.1:5201 -F tls://gost.brook-5.com:8443 
```
```
[root@gostclient ~]# iperf3 -c 127.0.0.1 -R
Connecting to host 127.0.0.1, port 5201
Reverse mode, remote host 127.0.0.1 is sending
[  4] local 127.0.0.1 port 39198 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec   443 MBytes  3.72 Gbits/sec                  
[  4]   1.00-2.00   sec   685 MBytes  5.75 Gbits/sec                  
[  4]   2.00-3.00   sec   612 MBytes  5.13 Gbits/sec                  
[  4]   3.00-4.00   sec   573 MBytes  4.81 Gbits/sec                  
[  4]   4.00-5.00   sec   610 MBytes  5.11 Gbits/sec                  
[  4]   5.00-6.00   sec   640 MBytes  5.37 Gbits/sec                  
[  4]   6.00-7.00   sec   590 MBytes  4.95 Gbits/sec                  
[  4]   7.00-8.00   sec   552 MBytes  4.63 Gbits/sec                  
[  4]   8.00-9.00   sec   522 MBytes  4.38 Gbits/sec                  
[  4]   9.00-10.00  sec   580 MBytes  4.86 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  5.68 GBytes  4.88 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  5.67 GBytes  4.87 Gbits/sec                  receiver

iperf Done.
```
</blockquote></details>


<details><summary>http2</summary><blockquote>

服务端
```
gost -L http2://:8443
```
客户端
```
gost -L tcp://:5201/127.0.0.1:5201 -F http2://gost.brook-5.com:8443 
```
```
[root@gostclient ~]# iperf3 -c 127.0.0.1 -R
Connecting to host 127.0.0.1, port 5201
Reverse mode, remote host 127.0.0.1 is sending
[  4] local 127.0.0.1 port 39206 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec   237 MBytes  1.99 Gbits/sec                  
[  4]   1.00-2.00   sec   227 MBytes  1.91 Gbits/sec                  
[  4]   2.00-3.00   sec   201 MBytes  1.69 Gbits/sec                  
[  4]   3.00-4.00   sec   190 MBytes  1.59 Gbits/sec                  
[  4]   4.00-5.00   sec   191 MBytes  1.60 Gbits/sec                  
[  4]   5.00-6.00   sec   192 MBytes  1.61 Gbits/sec                  
[  4]   6.00-7.00   sec   183 MBytes  1.53 Gbits/sec                  
[  4]   7.00-8.00   sec   173 MBytes  1.45 Gbits/sec                  
[  4]   8.00-9.00   sec   173 MBytes  1.45 Gbits/sec                  
[  4]   9.00-10.00  sec   182 MBytes  1.52 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.91 GBytes  1.64 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  1.90 GBytes  1.64 Gbits/sec                  receiver

iperf Done.
```
</blockquote></details>

<details><summary>relay</summary><blockquote>

服务端
```
gost -L relay://:8443
```
客户端
```
gost -L tcp://:5201/127.0.0.1:5201 -F relay://gost.brook-5.com:8443 
```
```
[root@gostclient ~]# iperf3 -c 127.0.0.1 -R
Connecting to host 127.0.0.1, port 5201
Reverse mode, remote host 127.0.0.1 is sending
[  4] local 127.0.0.1 port 39280 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec   674 MBytes  5.66 Gbits/sec                  
[  4]   1.00-2.00   sec   846 MBytes  7.10 Gbits/sec                  
[  4]   2.00-3.00   sec   887 MBytes  7.44 Gbits/sec                  
[  4]   3.00-4.00   sec   908 MBytes  7.61 Gbits/sec                  
[  4]   4.00-5.00   sec   910 MBytes  7.63 Gbits/sec                  
[  4]   5.00-6.00   sec   942 MBytes  7.90 Gbits/sec                  
[  4]   6.00-7.00   sec   930 MBytes  7.80 Gbits/sec                  
[  4]   7.00-8.00   sec   917 MBytes  7.69 Gbits/sec                  
[  4]   8.00-9.00   sec   861 MBytes  7.22 Gbits/sec                  
[  4]   9.00-10.00  sec   922 MBytes  7.73 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  8.61 GBytes  7.40 Gbits/sec   20             sender
[  4]   0.00-10.00  sec  8.61 GBytes  7.39 Gbits/sec                  receiver

iperf Done.
```
</blockquote></details>

<details><summary>relay+tls</summary><blockquote>

服务端
```
gost -L relay+tls://:8443
```
客户端
```
gost -L tcp://:5201/127.0.0.1:5201 -F relay+tls://gost.brook-5.com:8443 
```
```
[root@gostclient ~]# iperf3 -c 127.0.0.1 -R
Connecting to host 127.0.0.1, port 5201
Reverse mode, remote host 127.0.0.1 is sending
[  4] local 127.0.0.1 port 39288 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec   526 MBytes  4.41 Gbits/sec                  
[  4]   1.00-2.00   sec   603 MBytes  5.06 Gbits/sec                  
[  4]   2.00-3.00   sec   583 MBytes  4.89 Gbits/sec                  
[  4]   3.00-4.00   sec   552 MBytes  4.63 Gbits/sec                  
[  4]   4.00-5.00   sec   606 MBytes  5.08 Gbits/sec                  
[  4]   5.00-6.00   sec   580 MBytes  4.86 Gbits/sec                  
[  4]   6.00-7.00   sec   602 MBytes  5.05 Gbits/sec                  
[  4]   7.00-8.00   sec   538 MBytes  4.51 Gbits/sec                  
[  4]   8.00-9.00   sec   518 MBytes  4.35 Gbits/sec                  
[  4]   9.00-10.00  sec   508 MBytes  4.26 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  5.49 GBytes  4.72 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  5.49 GBytes  4.71 Gbits/sec                  receiver

iperf Done.
```
</blockquote></details>



