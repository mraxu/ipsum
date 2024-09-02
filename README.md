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

Wall of Shame (2024-09-02)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
159.65.147.193|panel.mydigitalads.in|9
77.91.85.126|chummy-activity.aeza.network|9
218.92.0.31|-|8
106.12.222.76|-|8
61.177.172.172|-|8
61.177.172.179|-|8
218.92.0.76|-|8
35.230.66.101|101.66.230.35.bc.googleusercontent.com|8
61.177.172.136|-|8
61.177.172.161|-|8
61.177.172.160|-|8
61.177.172.168|-|8
218.92.0.112|-|8
218.92.0.113|-|8
218.92.0.118|-|8
180.101.88.197|-|8
85.209.11.27|-|8
218.92.0.107|-|8
218.92.0.56|-|8
152.42.244.23|-|8
185.220.101.24|berlin01.tor-exit.artikel10.org|8
164.90.183.255|flexomatei.ro|8
218.92.0.29|-|8
218.92.0.22|-|8
218.92.0.24|-|8
218.92.0.27|-|8
61.177.172.140|-|8
194.169.175.37|-|8
194.169.175.38|-|8
218.92.0.34|-|8
92.55.190.215|-|8
139.59.92.140|-|8
112.72.235.19|-|8
85.209.11.254|-|8
5.42.84.98|peppy-calculator.aeza.network|8
80.82.77.33|sky.census.shodan.io|7
85.133.247.145|-|7
118.41.204.48|-|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
109.74.204.123|academyforinternetresearch.org|7
5.135.90.165|ip165.ip-5-135-90.eu|7
185.165.191.26|-|7
188.127.40.145|-|7
193.151.155.77|-|7
45.119.212.196|-|7
92.118.39.133|-|7
185.111.244.51|ip-185-111-244-51.muvdns.com|7
83.222.191.62|-|7
91.103.140.42|-|7
94.102.49.193|cloud.census.shodan.io|7
82.200.65.218|gw-bell-xen.ll-nsk.zsttk.ru|7
64.23.244.21|-|7
157.245.195.66|-|7
178.163.244.13|test.tuf.by|7
171.25.193.77|tor-exit-read-me.dfri.se|7
185.220.101.9|berlin01.tor-exit.artikel10.org|7
222.71.223.54|54.223.71.222.broad.xw.sh.dynamic.163data.com.cn|7
139.196.106.195|-|7
141.255.160.234|hostedby.privatelayer.com|7
183.81.169.238|-|7
103.251.167.20|-|7
185.253.54.52|devling.fr|7
207.90.244.4|-|7
93.174.95.106|battery.census.shodan.io|7
109.120.156.102|healthy-story.aeza.network|7
185.196.10.84|-|7
183.99.89.74|-|7
206.238.70.19|-|7
5.42.76.224|resonant-sign.aeza.network|7
190.85.15.251|-|7
185.142.236.36|green.census.shodan.io|7
46.101.1.149|-|7
14.40.8.125|-|7
