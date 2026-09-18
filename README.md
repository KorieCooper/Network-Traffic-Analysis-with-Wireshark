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

<b>Step 1:</b> Setting up the segmented lab network with Kali, Ubuntu, and pfSense VMs. <br/>
<img src="step%201.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 1"/>
<br />
<br />

<b>Step 2:</b> Enabling port mirroring on pfSense to capture LAN traffic. <br/>
<img src="Step%202.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 2"/>
<br />
<br />

<b>Step 3:</b> Capturing packets in Wireshark and filtering for ICMP traffic. <br/>
<img src="STEP%203.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 3"/>
<br />
<br />

<b>Step 4:</b> Tracing DNS queries and responses in the capture. <br/>
<img src="STEP%204.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 4"/>
<br />
<br />

<b>Step 5:</b> Reviewing captured traffic for anomalies. <br/>
<img src="STEP%205.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 5"/>
<br />
<br />

<b>Step 6:</b> Confirming visibility into cross-VLAN traffic via the mirrored port. <br/>
<img src="STEP%206.png" height="80%" width="80%" alt="Traffic Analysis Part A Step 6"/>
<br />
<br />

<b>Part B — Step 1:</b> Setting up an FTP session between hosts on the network. <br/>
<img src="PART%20B%20STEP%201.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 1"/>
<br />
<br />

<b>Part B — Step 2:</b> Capturing the FTP session in Wireshark. <br/>
<img src="PART%20B%20STEP%202.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 2"/>
<br />
<br />

<b>Part B — Step 3:</b> Filtering the capture for FTP protocol traffic. <br/>
<img src="PART%20B%20STEP%203.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 3"/>
<br />
<br />

<b>Part B — Step 4:</b> Following the FTP stream to inspect the full session. <br/>
<img src="PART%20B%20STEP%204.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 4"/>
<br />
<br />

<b>Part B — Step 5:</b> Locating the plaintext username in the stream. <br/>
<img src="PART%20B%20STEP%205.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 5"/>
<br />
<br />

<b>Part B — Step 6:</b> Locating the plaintext password in the stream. <br/>
<img src="PART%20B%20STEP%206.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 6"/>
<br />
<br />

<b>Part B — Step 7:</b> Documenting the credential exposure as a finding. <br/>
<img src="PART%20B%20STEP%207.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 7"/>
<br />
<br />

<b>Part B — Step 8:</b> Recommending FTPS/SFTP and segmentation as mitigations. <br/>
<img src="PART%20B%20STEP%208.png" height="80%" width="80%" alt="Traffic Analysis Part B Step 8"/>
<br />
<br />
