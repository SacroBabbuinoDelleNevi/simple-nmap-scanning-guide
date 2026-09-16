Whether you're just curious or you're testing the security of your perimeter, scanning is a widely used technique to assess all the services a machine exposes.
#### Don't be in the grey
As I also stated in the README and the intro, scanning a network is **illegal** without explicit proper authorization from the owner of the machines, which is very likely **not** the same guy who owns the website running on it. Furthermore, scanning activities **are** intrusive **even if no exploit is run** and usually they generate a lot of (unusual) traffic, which could lead to your IP being blocked or interfere with the regular business of the network, making certain services slow down or crash. Because of this, scanning activity is usually performed outside peak hours.
You can freely scan (few times a day) [this machine](http://scanme.nmap.org).
That said, let's look at the fun part and understand what a scan actually is ;)

#### What is it and how do I do a scan?
A scan is a series of packets sent to a machine to get information about it. That machine may or may not respond to our packets, and in either case we can deduce something.
You can even perform a scan manually, one host at a time, one port at a time, but obviously that's not efficient and can be automated through programming languages, resulting in the creation of tools such as `nmap`.
Since those tools craft the packets for you, understanding which packets are sent and how should the target behave is crucial to correctly read the output of a scan given that in certain situations some results may cause confusion or false positives, and you should be able to tell each one apart.

**Next**: [[2 - Get your targets]]