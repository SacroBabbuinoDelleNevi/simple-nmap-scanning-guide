Optimization is an important part of nmap scanning, if only because it could lead to more accurate information.  
An nmap scan sends probes to a target or group of targets, and we can adjust:

`--min/max-parallelism`  
**How many probes are simultaneously sent**
Regulating this to high values is risky due to the possible loss of accuracy. Sending a lot of probes at the same time on a poorly performing network could result in packets being dropped for other reasons than the ones nmap interprets and expects. Besides, this rate is automatically adjusted based on performance: the number starts low but can hit hundreds of probes simultaneously. 

`--initial/min/max-rtt-timeout`  
**How much time to wait for a response between  probes**
This option is also adaptive and usually starts high, but reduces in high latency networks. Don't set the value too low as it might cause the scans to take longer as the response packet could be arriving while the probe is being transmitted.

`--max-retries=10`  
**How many retransmissions for each probe**
The higher the number the greater the accuracy, but the longer the scan. In highly reliable networks the value can be low, even 0 to specify that no retransmissions are allowed. Getting that low is always risky of course.

`--(max-)scan-delay`  
**How much time between each probe**
This is especially useful in rate limited networks. Nmap already tries to adjust the rate, but setting it manually ensures the best performance and accuracy.

### Templates
To help speed up the process, you can use timing templates without tweaking each parameter. There are 6, and each of them is increasingly aggressive. You specify a template via the `-T` flag.

| Level | Description |
| ----- | ----------- |
| T0    | paranoid    |
| T1    | sneaky      |
| T2    | polite      |
| T3    | normal      |
| T4    | aggressive  |
| T5    | insane      |

**Next**: [[6 - Service and version detection]]