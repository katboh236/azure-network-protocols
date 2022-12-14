<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource Group in Azure
- Create a Windows 10 Virtual Machine (VM)
- Create a Linux (Ubuntu) VM
- Observe ICMP Traffic
- Observe SSH, DHCP, DNS, RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/jgtDP6h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created Resource Group RG-LAB-02 in Azure, created a Windows 10 and Linux (Ubuntu) Virtual Machines. 
</p>
<br />
<p>
<img src="https://imgur.com/x9gJhRa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/427Lq91.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/nBDC19s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observed ICMP traffic: istalled Wireshark inside VM1, opened Wireshark and filtered for ICMP traffic only - no traffic shown. Retrieved private IP address of the Ubuntu VM2, attempted to ping it from within Windows 10 VM1 in PowerShell and observed ICMP traffic in WireShark.
</p>
<br />

<p>
<img src="https://imgur.com/3FZKVCI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/tyFrqM7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiated a perpetual/non-stop ping from Windows 10 VM1 to Ubuntu VM2. Opened the Network Security Group and disabled incoming (inbound) ICMP traffic for Ubuntu VM2 and observed ICMP traffic in WireShark in the Windows 10 VM1. Re-enabled ICMP traffic for the Network Security Group Ubunntu VM2 was using and observed the ICMP traffic in WireShark back in the Windows 10 VM1 (ping is working).
</p>
<br />
<p>
<img src="https://imgur.com/AMoXgPG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/ihgcQKC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/NaU6ptt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observed SSH traffic: in VM1 (Windows 10) in Wireshark, filtered for SSH only, "SSH into" Ubuntu VM2 (via its private IP address). Typed commands (ls, pwd, etc) into the Linux SSH connection and observed SSH traffic spam in WireShark, exited connection by typing "exit" and pressing [Enter].
</p>
<br />
<p>
<img src="https://imgur.com/UMkY1Ja.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observed DHCP traffic: in WireShark, filtered for DHCP traffic only, from Windows 10 VM1, attempted to issue VM a new IP address from command line (ipconfig /renew) - observed the DHCP traffic appearing in WireShark.
</p>
<br />
<p>
<img src="https://imgur.com/8kPFbOe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/OndU6uh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe DNS traffic: in WireShark, filtered for DNS traffic only, from VM1 (Windows 10) within command line, used "nslookup" to see what google.com and disney.com's IP addresses ae, observed DNS traffic in WireShark.
</p>
<br />
<p>
<img src="https://imgur.com/GISezqH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Obseved RDP traffic: in WireShark, filtered for RDP traffic only (tcp.port ==3389), observed the immediate non-stop spam of traffic. RDP (protocol) is constantly showing a live stream from one computer to another, therefore traffic is always being transmitted.
</p>
<br />
