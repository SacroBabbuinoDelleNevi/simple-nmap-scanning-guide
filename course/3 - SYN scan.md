##### How to get information from a simple SYN scan
Before we dive into nmap itself, we should look at some basic TCP/IP networking.
When trying to connect to an open service hosted on a machine using TCP, we typically send a SYN packet, the server responds SYN+ACK, then we send ACK and the connection is opened. To close one such connection, we send a FIN, the server responds FIN+ACK, we send ACK and connection closed. If some problem occurs,a RST packet is sent, signaling that the sender of this packet will stop listening for more packets.

![[Pasted image 20260914093615.png|334]]
source: [velog](https://velog.velcdn.com/images/xx0hn/post/b8c269b8-760a-4d5a-9b87-ba0dbe9d0c62/what-is-a-tcp-3-way-handshake-process-three-way-handshaking-establishing-connection-6a724e77ba96e241.jpeg)

![[Pasted image 20260914093345.png|336]]
source: [geeksforgeeks.org](https://media.geeksforgeeks.org/wp-content/uploads/20251106163448590456/initiator.webp)

But what can we get out of this?
When trying to identify all the exposed services, first thing to do is to try and send a SYN packet to all the ports available (65 535) and wait for a response.

| Response    | Meaning                                         |
| ----------- | ----------------------------------------------- |
| SYN+ACK     | Port is open and accepts connection. Good!      |
| RST         | Port is closed or it doesn't accept connections |
| No response | Probably blocked by firewall                    |
We can also get additional information and we might want to use other scanning methods, but we will discuss that in later chapters