<h1> 🛡️ Cloud SIEM Deployment – Microsoft Sentinel (Azure)</h1>

 

<h2>Description</h2>
Deployed a cloud-based SIEM using Microsoft Sentinel and Log Analytics Workspace. Provisioned a Windows VM in Azure, configured it as a honeypot by disabling its firewall, and collected security telemetry to simulate real-world attack behavior. Analyzed events using KQL and built alert rules for threat detection and response.
<br />


<h2>Utilities Used</h2>

- <b>Microsoft Sentinel</b> 
- <b>Log Analytics Workspace</b>

<h2>Environments Used </h2>

- <b>Microsoft Azure</b> 

<h2>Project Documentation & Walkthrough:</h2>




<p align="center">
Go over to Microsoft Azure and create an account. After that, we will have to create a Virtual Machine to act as our honeypot <br/>
<img src="https://i.imgur.com/D9BQNsS.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
While we are creating the VM, we want to create a custom security rule, where we allow all inboud traffic  <br/>
<img src="https://i.imgur.com/PCBx0Qe.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we head over to Log Analytics Workspace and deploy it to the workspace that the VM is a part of <br/>
<img src="https://i.imgur.com/vBem7t9.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Head over to Microsoft Defender for Cloud, and select the Environment Settings tab  <br/>
<img src="https://i.imgur.com/LPy1NfO.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the Environment Settings tab, click on the honeypot workspace to open the settings tab, then select Data Collection and allow All Events   <br/>
<img src="https://i.imgur.com/JbXR88Q.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we need to turn on the VM. Head over to the Virtual Machine tab and click Connect  <br/>
<img src="https://i.imgur.com/XNY037O.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we will connect to the VM using RDP port 3389 by using the public ip address of the VM & the set of credentials we chose  <br/>
<img src="https://i.imgur.com/4RUYXdo.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set up the profile inside the VM <br/>
<img src="https://i.imgur.com/bE1mmgC.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Inside the VM, we can head over to Event Viewer. We can already see that some security logs are present  <br/>
<img src="https://i.imgur.com/t65hGTc.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In order to turn this into a real honeypot, we are going to disable the firewall. But first lets check if ICMP is enabled by trying ping  <br/>
<img src="https://i.imgur.com/INvBohD.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Our contact efforts proved futile 😔 so now we head to Windows Defender to turn off the firewalls <br/>
<img src="https://i.imgur.com/ZrLNvxA.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lets give ICMP one more try... Yay we got some replies!  <br/>
<img src="https://i.imgur.com/BPoiy9m.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now this is where you shine, use or create a custom log of your choice to aggregate our alerts. I used a bash script that I ran in the VM   <br/>
<img src="https://i.imgur.com/AYQkeei.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Saving the script so we can export the logs later <br/>
<img src="https://i.imgur.com/XyOv06U.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Creating the custom log <br/>
<img src="https://i.imgur.com/ft72G0p.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lets test of our logs are being collected properly, we need to focus on EventID 4625 which alerts us for failed login attempts <br/>
<img src="https://i.imgur.com/GC1QFRM.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now we head over to Microsoft Sentinel to use as our SIEM of choice to aggregate the logs <br/>
<img src="https://i.imgur.com/FT1gkNs.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Look at it go ! So many alerts on our honeypot (none of them are severe, there are many alerts because we allowed all events)  <br/>
<img src="https://i.imgur.com/O1oA1ib.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2> ✅ Conclusion</h2>
This lab provided hands-on experience with deploying and configuring a cloud-native SIEM using Microsoft Sentinel. By leveraging a honeypot VM to generate real-world telemetry, I was able to simulate attacker behavior, analyze security events using KQL, and build actionable detection rules. The project reinforced key concepts in cloud security monitoring, log analytics, and incident detection within modern enterprise environments.
<br />





































<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
