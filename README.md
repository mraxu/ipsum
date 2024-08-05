![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2024-08-05)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
194.50.16.221|-|10
194.169.175.36|-|10
194.169.175.35|-|10
95.214.27.253|-|10
218.92.0.34|-|9
218.92.0.31|-|9
61.177.172.160|-|9
212.113.102.66|cozy-baseball.aeza.network|9
218.92.0.112|-|9
218.92.0.113|-|9
218.92.0.118|-|9
180.101.88.197|-|9
180.101.88.196|-|9
212.113.102.130|server2.aeza.network|9
61.177.172.179|-|9
218.92.0.107|-|9
83.222.191.62|-|9
218.92.0.56|-|9
61.177.172.140|-|9
218.92.0.29|-|9
218.92.0.22|-|9
218.92.0.24|-|9
218.92.0.27|-|9
180.101.88.205|-|9
85.209.11.254|-|9
80.82.77.33|sky.census.shodan.io|8
212.76.27.39|-|8
218.92.0.76|-|8
23.95.248.83|23-95-248-83-host.colocrossing.com|8
61.177.172.136|-|8
212.113.102.128|server3.aeza.network|8
92.118.39.133|-|8
85.209.11.27|-|8
221.222.184.230|-|8
45.148.10.251|-|8
207.90.244.4|-|8
164.92.255.241|-|7
111.59.56.6|-|7
43.156.143.216|-|7
72.24.32.60|72-24-32-60.cpe.sparklight.net|7
200.105.183.118|static-200-105-183-118.acelerate.net|7
211.224.41.185|-|7
147.185.132.147|-|7
41.138.54.13|-|7
213.109.202.127|-|7
178.128.161.183|-|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
66.66.116.251|syn-066-066-116-251.res.spectrum.com|7
85.209.11.227|-|7
92.118.39.120|-|7
80.82.70.133|rnd.group-ib.com|7
54.37.10.124|vps-1e3810b9.vps.ovh.net|7
222.102.214.75|-|7
101.43.73.205|-|7
207.90.244.14|-|7
80.82.77.202|rnd.group-ib.com|7
134.209.168.219|-|7
192.42.116.208|11.tor-exit.nothingtohide.nl|7
185.129.62.62|tor01.zencurity.com|7
193.32.162.83|-|7
122.166.156.246|abts-kk-static-246.156.166.122.airtelbroadband.in|7
211.253.10.96|-|7
14.53.134.163|-|7
89.234.157.254|marylou.nos-oignons.net|7
193.32.162.79|-|7
82.137.193.252|-|7
1.12.52.98|-|7
185.220.101.1|berlin01.tor-exit.artikel10.org|7
80.82.77.139|dojo.census.shodan.io|7
125.133.0.85|-|7
183.81.169.238|-|7
165.22.16.134|-|7
103.142.86.221|-|7
207.90.244.2|-|7
65.181.73.155|65-181-73-155.static.imsbiz.com|7
45.148.10.202|-|7
202.51.82.167|-|7
199.45.154.125|-|7
103.56.61.130|-|7
82.151.65.155|-|7
103.46.186.148|-|7
