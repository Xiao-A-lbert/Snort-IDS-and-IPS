# Snort IDS and IPS Rules

<h2>Description</h2>
In this task, I wrote rules in snort for ids and ips mode. 


<h2>Languages and Utilities Used</h2>

- <b>snort</b>
- <b>linux CLI</b>


<h2>Environments Used </h2>

- <b>Unbuntu</b> 

<br />
<br />
Changed directory tp /etc/snort/rules and sudo nano local.rules.

![2) going into local rules](https://github.com/user-attachments/assets/eccfead3-0955-4a63-98d5-6fbfbf3e4872)

<br />
<br />
First snort rule to alert for any icmp traffic to 8.8.8.8

![1) first snort alert icmp](https://github.com/user-attachments/assets/f3388012-428f-4406-aef7-5287c62cd3dc)

<br />
<br />  
Pinging 8.8.8.8 while the snort rule is active shows the icmp alerts. I ran snort with: sudo snort -A console -l /var/log/snort -i enp0s3 /etc/snort/snort.conf -q .
-A console: Sets the alert mode to "console", which displays alerts directly in the terminal.
-l /var/log/snort: Specifies the directory where Snort will save its log files.
-i enp0s3: Designates the network interface (enp0s3) that Snort will monitor.
/etc/snort/snort.conf: Specifies the path to the Snort configuration file1.
-q: Runs Snort in "quiet" mode, suppressing startup banner and initialization.

![3) initializing snort with -A console -l log -i interface -c snortconf -q quiet mode](https://github.com/user-attachments/assets/2f95cd71-e3a6-4567-a93b-c94080c05da1)

<br />
<br />
Writing a snort rule for any tcp traffic to port 4444 which is a common port for malicious traffic like trojans.

![4) snort tcp port 4444 alert](https://github.com/user-attachments/assets/d02e9d26-c53e-422d-b0c4-69e280c8ca1d)

<br />
<br />
Using hping3 to ping example.com on port 4444 triggered the tcp alert. 

![5) tcpo alert to port 4444 hping3 example](https://github.com/user-attachments/assets/dcd695a3-9d29-4018-9c89-8c215da450a4)
c
<br />
<br />
Using hping3 to ping example.com while running snort in fast mode to log the traffic in /var/log/snort creates a log file named "alert" with all of the port 4444 ping traffic. 

![6) snort fast alerts logging for siem processing](https://github.com/user-attachments/assets/d2eb16eb-d3a5-4b64-86fd-863f018d6528)

<br />
<br />
Configuring a snort rule to drop any tcp traffic to and from port 21 in IPS mode.

![7) snort in ips drop mode snort rule](https://github.com/user-attachments/assets/f08b7441-e07f-408e-9321-0c7608e323cb)

<br />
<br />  
