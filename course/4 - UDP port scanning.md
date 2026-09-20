UDP's scanning principle is slightly different: since it is a stateless protocol, we can't send SYN packets to guess port status. What we do is send empty or protocol specific UDP packets and wait for a response.  

>[!Note]
>Don't leave UDP scanning out! UDP ports **are** an attack surface, and you may discover vulnerable UDP services!

| Response                           | State                    |
| ---------------------------------- | ------------------------ |
| Sends a packet back (occasionally) | Port is `open`           |
| Nothing                            | Port is `open\|filtered` |
| ICMP port unreachable              | Port is `closed`         |
| ICMP unreachables                  | Port is `filtered`       |
The only thing really different from the output of a SYN scan is that `open|filtered` status you might see. That means the port is not sending anything back, which is either because the service only responds to its specific packets (and not empty ones, sent to the majority of ports) or a firewall drops our packets.
