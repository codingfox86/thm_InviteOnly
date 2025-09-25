## Another walkthrough for the TryHackme room [Invite Only](https://tryhackme.com/room/invite-only) <br>

 <img width="150" height="150" alt="Detecting Web DDos" src="https://tryhackme-images.s3.amazonaws.com/room-icons/5fc2847e1bbebc03aa89fbf2-1757474827465" /> <br>

 ### 1 Invite only <br>

You are an SOC analyst on the SOC team at Managed Server Provider TrySecureMe. Today, you are supporting an L3 analyst in investigating flagged IPs, hashes, URLs, or domains as part of IR activities. One of the L1 analysts flagged two suspicious findings early in the morning and escalated them. Your task is to analyse these findings further and distil the information into usable threat intelligence. <br>

Flagged IP: 101[.]99[.]76[.]120<br>
Flagged SHA256 hash: 5d0509f68a9b7c415a726be75a078180e3f02e59866f193b0a99eee8e39c874f<br>

We recently purchased a new threat intelligence search application called TryDetectThis2.0. You can use this application to gather information on the indicators above.<br>

Connecting To The Machine<br>
Just start the Virtual Machine by clicking “Start Virtual Machine.” Once the VM is booted up, double-click the launcher on the desktop to start the TryDetectThis2.0 application.<br>

Ok folks, let's dive in and start their own [Virus Total Version](https://www.virustotal.com/) you see on the desktop of your VM and running on localhost. <br>
<br>
Put in the given hash and you'll find the answers for Question 1 and 2. 
<img src="https://github.com/codingfox86/thm_InviteOnly/blob/main/q1.png" /> <br>
__Question 1: What is the name of the file identified with the flagged SHA256 hash? <br>
syshelpers.exe__ <br>
__Question 2: What is the file type associated with the flagged SHA256 hash? <br>
WIN32 EXE__ <br>
<br>
For question 3 and 4 click on Relations! And don't forget to copy the hashes :) <br>
<img src="https://github.com/codingfox86/thm_InviteOnly/blob/main/q3.png" /> <br>
__Question 3: What are the execution parents of the flagged hash? List the names chronologically, using a comma as a separator. Note down the hashes for later use.<br>
361GJX7J,installer.exe__ <br>
__Question 4: What is the name of the file being dropped? Note down the hash value for later use. <br>
Aclient.exe__ <br>
<br>
For question 5, copy the second hash of question 3 into the search bar and go to Relations again. There you'll find 20 dropped files and 4 of them are malicious ones and the answer! <br>
<img src="https://github.com/codingfox86/thm_InviteOnly/blob/main/q5.png" /> <br>
__Question 5: Research the second hash in question 3 and list the four malicious dropped files in the order they appear (from up to down), separated by commas. <br>
searchhost.exe,syshelpers.exe,nat.vbs,runsys.vbs__ <br>
<br>
Next question was really tricky for me because I am not yet familiar with the different malware family names. So I found it on the original VirusTotal Website. Go there and put the flagged IP into the search bar. In the Relations Tab you'll find Communication Files. I chose one of them and bam! <br>
<img src="https://github.com/codingfox86/thm_InviteOnly/blob/main/q6.png" /> <br>
__Question 6: Analyse the files related to the flagged IP. What is the malware family that links these files? <br>
asyncrat__ 
