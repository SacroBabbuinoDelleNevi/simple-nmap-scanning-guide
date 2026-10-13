First thing to do when scanning for vulnerabilities, is identifying the targets. We might not have the freedom to scan all the machines in a network, or we might not even know how many machines are up and running in said network. To do so, we begin the first phase of scanning: **host discovery**
#### Host discovery
A simple way to discover hosts is by pinging a number of IPs/MACs and look at the output. We can do an ARP ping in a local network or an ICMP echo request if the targets are remote and maybe both, just to make sure.
- If we see an "host unreachable" message, we know the route to that network is not set, so we either got something wrong or a firewall is blocking it. 
- If we don't get anything back after a few seconds, then probably the packets are just being dropped: the host is either down or behind a blocking firewall
- If we get a reply then the host is up  
One thing to note is that host discovery is the first automated step in _every_ nmap scan type, so if we already know the host is up we can usually disable the host discovery phase: it can break some (extremely) weak firewall's pattern or simply speed up our scans, since nmap usually skips the scan entirely if no ICMP/ARP replies are received.
If our target sits in the local network, nmap will send both the ICMP and the ARP ping, otherwise only the echo request is sent.

A typical nmap command is written like this:
```sh
nmap -options <target_ip_range>/<subnet_mask>
```

#### Simple host discovery scan
To simply scan a network for active addresses, we can use the option `-sn`: no port scan. 
Since host discovery is the very first phase of every scan, what we're telling nmap here is that we want just that, no further investigation needed.
To launch our first scan, we do
```sh
nmap -sn 192.168.1.0/24
```
... And after some short time we should get a list of all the active devices on the network
> [!Note]
> Running nmap without sudo privileges is limiting: because it uses raw packet crafting, root privileges are mandatory to send crafted data and perform some elevated actions. The output can vary widely based on permissions given

**Next**: [3 - TCP port scanning](https://github.com/SacroBabbuinodelleNevi/simple-nmap-scanning-guide/blob/main/course/3%20-%20TCP%20port%20scanning.md)
