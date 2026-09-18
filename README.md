# Network-Traffic-Analysis-with-Wireshark
Packet capture and analysis lab using Wireshark across a segmented Kali, Ubuntu, and pfSense virtual network. Covers ICMP and DNS traffic tracing, LAN sniffing via port mirroring, and demonstrating plaintext credential exposure over FTP, plus mitigation recommendations such as FTPS, SFTP, and network segmentation.

<h2>Languages and Utilities Used</h2>

- <b>Wireshark</b>
- <b>Bash Shell</b>

<h2>Environments Used</h2>

- <b>Kali Linux VM</b>

<h2>Program walk-through:</h2>

<p align="center">
Full lab report:  <br/>
<a href="Lab%201%20Traffic%20Analysis.pdf">Lab 1 Traffic Analysis.pdf</a>
<br />
<br />
### TODO (Completed)

I followed each step in sequence:

1. Opened Wireshark on **External / Attacker Kali** and listened on interface `eth0`.
2. Kept Wireshark running in the background in **External / Attacker Kali** while performing the subsequent tasks (3 and 4).
3. Opened a new terminal in Attacker Kali, then pinged the Ubuntu VM for 5–10 seconds, stopping the ping with `CTRL + C`.
4. Opened a new web browser in Attacker Kali (even though no webpage was displayed) and kept it open for a couple of seconds.
5. Stopped capturing by clicking the **red button** on the toolbar.
6. Saved the pcap file in the root folder in the External/Attacker Kali.

<b>Step 1:</b> Checked how many packets were captured. <br/>
<img src="step%201.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 1"/>
<br />
<br />

<b>Step 2:</b> Applied an ICMP filter to see how many packets were ICMP. <br/>
<img src="Step%202.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 2"/>
<br />
<br />

<b>Step 3:</b> Selected an ICMP Echo Reply packet to find the source and destination IP. <br/>
<img src="STEP%203.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 3"/>
<br />
<br />

<b>Step 4:</b> Applied a DNS filter to see how many packets were displayed. <br/>
<img src="STEP%204.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 4"/>
<br />
<br />

<b>Step 5:</b> Found a DNS query to Amazon and looked it up in the browser to find the source and destination IP. <br/>
<img src="STEP%205.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 5"/>
<br />
<br />

<b>Step 6:</b> Found a DNS response from Amazon and looked it up in the browser to find the source and destination IP. <br/>
<img src="STEP%206.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 6"/>
<br />
<br />

### Task B – Sniff ICMP Traffic 

a) Connected to the following VMs in Hyper-V Manager:
   - Attacker/External Kali
   - Internal Kali
   - pfSense
   - Ubuntu

b) Launched and ran Wireshark in **Internal Kali**.

c) Opened two terminals on the **External Kali VM** — used one to ping the Ubuntu VM, and the other to ping Internal Kali.

d) Applied a proper display/capture filter in Wireshark on **Internal Kali VM** to show active ICMP traffic.

e) Applied a proper display/capture filter on the Internal Kali VM that ONLY displayed the ICMP request that originated from the External Kali VM and went to the Ubuntu 64-bit VM.


<b>Part B — Step 1:</b> Started packet capture in Internal Kali. <br/>
<img src="PART%20B%20STEP%201.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 1"/>
<br />
<br />

<b>Part B — Step 2:</b> Opened two terminals in External Kali to ping the Ubuntu VM and Internal VM. <br/>
<img src="PART%20B%20STEP%202.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 2"/>
<br />
<br />

<b>Part B — Step 3:</b> Applied an ICMP filter in Wireshark on Internal Kali to show active traffic. <br/>
<img src="PART%20B%20STEP%203.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 3"/>
<br />
<br />

<b>Part B — Step 4:</b> Set a filter to only show traffic from External Kali to the Ubuntu VM. <br/>
<img src="PART%20B%20STEP%204.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 4"/>
<br />
<br />

### Part B — Part 2

Ubuntu VM is also serving as an FTP server inside the LAN network. Now, you need to use External Kali to access this FTP server by using the command:
`ftp [ip_addr of ubuntu VM]`. The username for the FTP server is `student`, and the password is `password`. You can follow the steps below to access the FTP server.

<b>Part B — Step 5:</b> Attempting to log into FTP server. <br/>
<img src="PART%20B%20STEP%205.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 5"/>
<br />
<br />

<b>Part B — Step 6:</b> Locating the plaintext password in the stream. <br/>
<img src="PART%20B%20STEP%206.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 6"/>
<br />
<br />

<b>Part B — Step 7:</b> Signing in with another account to test. <br/>
<img src="PART%20B%20STEP%207.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 7"/>
<br />
<br />

<b>Part B — Step 8:</b> Locating the plaintext password in the stream. <br/>
<img src="PART%20B%20STEP%208.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 8"/>
<br />
<br />
