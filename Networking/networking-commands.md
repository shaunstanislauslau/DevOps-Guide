# Networking Commands

## List of Linux networking tools

### netstat (ss)

- Displays contents of /proc/net files. It works with the Linux Network Subsystem, it will tell you what the status of ports are ie. open, closed, waiting, masquerade connections. It will also display various other things. It has many different options.
- Netstat (Network Statistic) command display connection info, routing table information etc. To displays routing table information use option as -r.

- Sample output:

```bash
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)    
tcp4       0      0  127.0.0.1.62132        127.0.0.1.http        ESTABLISHED
tcp4       0      0  127.0.0.1.http         *                     LISTEN
```

### tcpdump
This is a sniffer, a program that captures packets off a network interface and interprets them for you. It understands all basic internet protocols, and can be used to save entire packets for later inspection.

### ping
The ping command (named after the sound of an active sonar system) sends echo requests to the host you specify on the command line, and lists the responses received their round trip time. PING (Packet INternet Groper) command is the best way to test connectivity between two nodes. Whether it is Local Area Network (LAN) or Wide Area Network (WAN). Ping use ICMP (Internet Control Message Protocol) to communicate to other devices. You can ping host name of ip address using below command.
```
$ ping google.com
PING google.com (216.58.198.78): 56 data bytes
64 bytes from 216.58.198.78: icmp_seq=0 ttl=46 time=6.108 ms
64 bytes from 216.58.198.78: icmp_seq=1 ttl=46 time=6.222 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 6.108/6.165/6.222/0.057 ms
```

### traceroute
traceroute will show the route of a packet. It attempts to list the series of hosts through which your packets travel on their way to a given destination. Also have a look at xtraceroute (one of several graphical equivalents of this program). traceroute is a network troubleshooting utility which shows number of hops taken to reach destination also determine packets traveling path. Below we are tracing route to global DNS server IP Address and able to reach destination also shows path of that packet is traveling.
```
$ traceroute -I google.com
traceroute to google.com (216.58.198.78), 128 hops max, 72 byte packets
1  52.93.7.1 (52.93.7.1)  6.361 ms  6.229 ms  6.106 ms
2  72.14.215.85 (72.14.215.85)  5.939 ms  5.460 ms  5.914 ms
3  209.85.252.198 (209.85.252.198)  6.012 ms  5.694 ms  5.761 ms
4  64.233.174.27 (64.233.174.27)  5.079 ms  4.776 ms  4.662 ms
5  dub08s02-in-f78.1e100.net (216.58.198.78)  6.650 ms  5.509 ms  5.596 ms
```

### tracepath
tracepath performs a very simlar function to traceroute the main difference is that tracepath doesn't take complicated options.

### nmap
“ network exploration tool and security scanner”. nmap is a very advanced network tool used to query machines (local or remote) as to whether they are up and what ports are open on these machines.


### dig
Dig (domain information groper) query DNS related information like A Record, CNAME, MX Record etc. This command mainly use to troubleshoot DNS related query.
```
$ dig amazon.com

; <<>> DiG 9.8.3-P1 <<>> amazon.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30832
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;amazon.com.			IN	A

;; ANSWER SECTION:
amazon.com.		17	IN	A	54.239.25.200
amazon.com.		17	IN	A	54.239.25.208
amazon.com.		17	IN	A	54.239.26.128
amazon.com.		17	IN	A	54.239.17.6
amazon.com.		17	IN	A	54.239.17.7
amazon.com.		17	IN	A	54.239.25.192

;; Query time: 3 msec
;; SERVER: 10.78.97.142#53(10.78.97.142)
;; WHEN: Thu Dec 29 13:56:22 2016
;; MSG SIZE  rcvd: 124

```


### nslookup
nslookup command also use to find out DNS related query. The following examples shows A Record (IP Address) of tecmint.com.
```
nslookup amazon.com
Server:		10.78.97.142
Address:	10.78.97.142#53

Non-authoritative answer:
Name:	amazon.com
Address: 54.239.25.192
Name:	amazon.com
Address: 54.239.25.200
Name:	amazon.com
Address: 54.239.25.208
Name:	amazon.com
Address: 54.239.26.128
Name:	amazon.com
Address: 54.239.17.6
Name:	amazon.com
Address: 54.239.17.7
```

### host
host command to find name to IP or IP to name in IPv4 or IPv6 and also query DNS records.
```
$ host amazon.com
amazon.com has address 54.239.17.6
amazon.com has address 54.239.17.7
amazon.com has address 54.239.25.192
amazon.com has address 54.239.25.200
amazon.com has address 54.239.25.208
amazon.com has address 54.239.26.128
amazon.com mail is handled by 10 amazon-smtp.amazon.com.
```

### hostname
hostname is to identify in a network. Execute hostname command to see the hostname of your box. You can set hostname permanently in /etc/sysconfig/network. Need to reboot box once set a proper hostname.
```
$ hostname -f
miglen.development.box
```

### arp
ARP (Address Resolution Protocol) is useful to view / add the contents of the kernel’s ARP tables. To see default table use the command as.

## Configuration




### ifconfig
This command is used to configure network interfaces, or to display their current configuration. In addition to activating and deactivating interfaces with the “up” and “down” settings, this command is necessary for setting an interface's address information if you don't have the ifcfg script.

* ifup - Use ifup device-name to bring an interface up by following a script (which will contain your default networking settings). Simply type ifup and you will get help on using the script.
* ifdown - Use ifdown device-name to bring an interface down using a script (which will contain your default network settings). Simply type ifdown and you will get help on using the script.
* ifcfg - Use ifcfg to configure a particular interface. Simply type ifcfg to get help on using this script.

### route 
The route command is the tool used to display or modify the routing table. To add a gateway as the default you would type:
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.31.16.1     0.0.0.0         UG    0      0        0 eth0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.31.16.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
```
### iwconfig
iwconfig command in Linux is use to configure a wireless network interface. You can see and set the basic Wi-Fi details like SSID channel and encryption. You can refer man page of iwconfig to know more.

### ip



**************************************



```bash
$ watch ss -tp                               # Network connections
$ netstat -ant                               # Tcp connections -anu=udp
$ netstat -tulpn                             # Connections with PIDs
$ lsof -i                                    # Established connections
$ smb:// ip /share                           # Access windows smb share
$ share user x.x.x.x c$                      # Mount Windows share
$ smbclient -0 user\\\\ ip \\ share          # SMB connect
$ ifconfig eth# ip / cidr                    # Set IP and netmask
$ ifconfig ethO:l ip / cidr                  # Set virtual interface
$ route add default gw gw_ip                 # Set GW
$ ifconfig eth# mtu [size]                   # Change MTU size
$ export MAC=xx: xx: xx: xx: xx: xx          # Change MAC 
$ ifconfig int hw ether MAC                  # Change MAC
$ macchanger -m MAC int                      # Backtrack MAC changer
$ iwlist int scan                            # Built-in wifi scanner
$ dig -x ip                                  # Domain lookup for IP
$ host ip                                    # Domain lookup for IP
$ host -t SRV _ service _tcp.url.com         # Domain SRV lookup
$ dig @ ip domain -t AXFR                    # DNS Zone Xfer
$ host -l domain namesvr                     # DNS Zone Xfer
$ ip xfrm state list                         # Print existing VPN keys
$ ip addr add ip / cidr dev ethO             # Adds 'hidden' interface
$ /var/log/messages | grep DHCP              # List DHCP assignments
$ tcpkill host ip and port port              # Block ip:port
$ echo "1" /proc/sys/net/ipv4/ip_forward     # Turn on IP Forwarding
$ echo "nameserver x.x.x.x" /etc/resolv.conf # Add DNS Server
```


- ```arpwatch``` – Ethernet Activity Monitor.
- ``` bmon``` – bandwidth monitor and rate estimator.
- ```bwm-ng```– live network bandwidth monitor.
- ```curl``` – transferring data with URLs. (or try httpie)
- ```darkstat``` – captures network traffic, usage statistics.
- ```dhclient``` – Dynamic Host Configuration Protocol Client
- ```dig``` – query DNS servers for information.
- ```dstat``` – replacement for vmstat, iostat, mpstat, netstat and ifstat.
- ```ethtool``` – utility for controlling network drivers and hardware.
- ```gated``` – gateway routing daemon.
- ```host``` – DNS lookup utility.
- ```hping``` – TCP/IP packet assembler/analyzer.
- ```ibmonitor``` – shows bandwidth and total data transferred.
- ```ifstat``` –  report network interfaces bandwidth.
- ```iftop``` – display bandwidth usage.
- ```ip ```– a command with more features that ifconfig (net-tools).
- ```iperf3``` – network bandwidth measurement tool. (above screenshot Stacklinux VPS)
- ```iproute2``` – collection of utilities for controlling TCP/IP.
- ```iptables``` – take control of network traffic.
- ```IPTraf``` – An IP Network Monitor.
- ```iputils``` – set of small useful utilities for Linux networking.
- ```iw``` – a new nl80211 based CLI configuration utility for wireless devices.
- ```jwhois (whois)``` – client for the whois service.
- ```“lsof -i”``` – reveal information about your network sockets.
    mtr – network diagnostic tool.
    net-tools – utilities include: arp, hostname, ifconfig, netstat, rarp, route, plipconfig, slattach, mii-tool, iptunnel and ipmaddr.
    ncat – improved re-implementation of the venerable netcat.
    netcat – networking utility for reading/writing network connections.
    nethogs – a small ‘net top’ tool.
    Netperf – Network bandwidth Testing.
    netsniff-ng – Swiss army knife for daily Linux network plumbing.
    netstat – Print network connections, routing tables, statistics, etc.
    netwatch – monitoring Network Connections.
    ngrep – grep applied to the network layer.
    nload – display network usage.
    nmap – network discovery and security auditing.
    nmcli – a command-line tool for controlling NetworkManager and reporting network status.
    nmtui – provides a text interface to configure networking by controlling NetworkManager.
    nslookup – query Internet name servers interactively.
    ping – send icmp echo_request to network hosts.
    route – show / manipulate the IP routing table.
    slurm – network load monitor.
    snort – Network Intrusion Detection and Prevention System.
    smokeping –  keeps track of your network latency.
    socat – establishes two bidirectional byte streams and transfers data between them.
    speedometer – Measure and display the rate of data across a network.
    speedtest-cli – test internet bandwidth using speedtest.net
    ss – utility to investigate sockets.
    ssh –  secure system administration and file transfers over insecure networks.
    tcpdump – command-line packet analyzer.
    tcptrack – Displays information about tcp connections on a network interface.
    telnet – user interface to the TELNET protocol.
    tracepath – very similar function to traceroute.
    traceroute – print the route packets trace to network host.
    vnStat – network traffic monitor.
    websocat – Connection forwarder from/to web sockets to/from usual sockets, in style of socat.
    wget –  retrieving files using HTTP, HTTPS, FTP and FTPS.
    Wireless Tools for Linux – includes iwconfig, iwlist, iwspy, iwpriv and ifrename.
    Wireshark – network protocol analyzer.


- ```watch ss -tp ``` --  Network Connec­tions

- ```netstat -ant ``` --  TCP connec­tions

- ```netstat -anu``` -- UDP Connec­tions

- ```netstat -tulpn``` -- Connec­tions with PIDs

- ```lsof -i``` -- Establ­ished Connec­tions

- ```smb:/­/<I­P>/­<SH­ARE­NAM­E> ``` -- Access Windows SMB Share

- ```share <US­ERN­AME> <IP> c$``` --  Mount Windows Share

- ```ifconfig <IN­TER­FAC­E> <IP­/CI­DR>``` -- Set IP and netmask

- ```ifconfig eth0:1 <IP­/CI­DR>``` --	Set virtual interface

- ```route add default gw <IP­>``` -- Set Default Gateway

- ```ifconfig <IN­TER­FAC­E> mtu <SI­ZE>``` -- Change MTU size

- ```export MAC=<M­ACA­DDR­ESS­> ``` -- Change MAC Address

- ```ifconfig int hw ether <MA­CAD­DRE­SS> ``` --  Change MAC Address

- ``` dig -x <IP­> ``` --  Domain Lookup IP

- ```host <IP­> ``` -- Domain Lookup IP

- ```dig@<­IP> <DO­MAI­N> -t AXFR``` -- DNS Zone Transfer

- ```host -l <DO­MAI­N> <NA­MES­ERV­ER>``` -- DNS Zone Transfer

- ```echo "­1" > /proc/­sys­/ne­t/i­pv4/ip forward``` --  Enable IP Forwarding

- ``` echo <"NA­MES­ERV­ER"> > /etc/r­eso­lv.c­onf``` -- Add DNS Server