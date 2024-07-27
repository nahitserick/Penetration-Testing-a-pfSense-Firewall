# Penetration Testing a pfSense Firewall

## Objective
The objective of this lab was to perform a penetration test on a pfSense firewall to identify vulnerabilities and implement measures to mitigate them. The focus was on understanding the steps of penetration testing, including reconnaissance, scanning, vulnerability analysis, exploitation, and post-attack activities.

### Skills Learned
- Understanding the steps of a penetration test.
- Proficiency in using tools like Nessus and OpenVAS for vulnerability scanning.
- Enhanced knowledge of firewall security and network configurations.
- Development of mitigation strategies for identified vulnerabilities.
- Differentiation between white-box, grey-box, and black-box penetration testing.

### Tools Used
- pfSense
- Nessus
- OpenVAS / Greenbone Security Manager (GSM)
- Nmap
- Traceroute
- Kali Linux

## Steps

### Part 1: Examine a pfSense Firewall Configuration

1. **Open pfSense Web GUI:**
   - Open Chrome on the vWorkstation and navigate to `172.30.0.1`.
   - Log in with the credentials `admin` and `pfsense`.
  
2. **Review Virtual IP Addresses:**
   - Navigate to Firewall > Virtual IPs.
   - Review the list of Virtual IP addresses.

3. **Review NAT Rules:**
   - Navigate to Firewall > NAT > Port Forward.
   - Click on the 1:1 tab and review the NAT rules.

4. **Review Firewall Rules:**
   - Navigate to Firewall > Rules.
   - Review both the WAN and LAN rules to understand the traffic allowed through the firewall.

Ref 1: WAN Rules Table

![image](https://github.com/user-attachments/assets/1603e1c8-6e2f-4bd0-a836-e3e99d6ede46)

### Part 2: Conduct a Penetration Test on the Network

1. **Launch Nessus on RemoteWindows01:**
   - Open the Nessus Web Client and log in with `Administrator` and `P@ssw0rd!`.
   - Create a new scan using the Basic Network Scan template.
   - Configure the scan to target IP addresses `202.20.1.1` and `202.20.1.3`.
   - Save and launch the scan.

2. **Review Scan Results:**
   - After the scan completes, review the results for identified vulnerabilities.
   - Capture screenshots of the scan results and detailed vulnerabilities.

Ref 2: Nessus Scan Results

![image](https://github.com/user-attachments/assets/7ee2f4da-5fde-45fb-8f3b-f939e828c7bd)

Ref 3: List of Identified Vulnerabilities

![image](https://github.com/user-attachments/assets/a989bfdc-1ae2-4a5f-8374-dad674c775a8)

3. **Modify Firewall Rules:**
   - On the pfSense Web GUI, delete the permissive rules on both WAN and LAN interfaces.
   - Apply changes to ensure more granular control over traffic.

4. **Rescan with Nessus:**
   - Launch the Nessus scan again to verify that the changes mitigated the vulnerabilities.
   - Capture updated scan results showing the improvements.

Ref 4: Updated Vulnerability Report Summary:

![image](https://github.com/user-attachments/assets/4d761765-f62a-4174-8eb1-ec131242abe2)

### Part 3: Conduct a Black-Box Penetration Test

1. **Perform a Traceroute:**
   - On the AttackLinux01 (Kali Linux), run `traceroute 172.40.0.20` to identify network hops.

Ref 5: TraceRoute Command Results

![image](https://github.com/user-attachments/assets/ad37d9bb-b507-43f0-b74d-0fb9d08645fa)

2. **Conduct a Port Scan with Nmap:**
   - Run `nmap 202.20.1.1` to scan for open ports.
   - Expand the scan with `nmap 202.20.1.1/24` to identify additional hosts.

Ref 6: Nmap scan with OS detection activated

![image](https://github.com/user-attachments/assets/4eb75046-fe68-46d3-a147-b8ae2b2af843)

3. **Advanced Nmap Scanning:**
   - Run `nmap -sV -O 202.20.1.3` to detect services and operating system details on the target.

4. **Use OpenVAS for Vulnerability Scanning:**
   - Access the OpenVAS Web GUI from RemoteWindows01.
   - Create and run a full vulnerability scan on `202.20.1.3`.
   - Review and capture detailed scan results.

Ref 7: OpenVAS Scan Report

![image](https://github.com/user-attachments/assets/b863234b-4807-4362-b43f-8978b43d8ae3)

### Part 4: Independent Challenge

1. **Research DMZ Best Practices:**
   - Research and identify three best practices for DMZ deployment.
   - Identify one potential mistake or vulnerability.

2. **Conduct a DMZ Penetration Test:**
   - Perform Nmap and Nessus/OpenVAS scans on the DMZ firewall interface and web server.
   - Capture scan results showing open ports and vulnerabilities.

Ref 8: Nmap Scan results on web server and DMZ fireawll interface

![image](https://github.com/user-attachments/assets/88f9b09e-4c83-4aa4-8126-9c99e765702e)

Ref 9: OpenVAS Vulnerability Scan Report

![image](https://github.com/user-attachments/assets/9ce495e2-d226-4e3c-b246-429f35f5691f)

3. **Recommend Changes:**
   - After analyzing the results of the OpenVAS vulnerability assesment conducted on the external facing firewall interace and the web server, It is clear that the most significant recommendation is to change the default admin credentials for pfSense and SSH.

## Key Takeaways
This lab provided comprehensive hands-on experience in penetration testing a pfSense firewall. By conducting both white-box and black-box tests, I gained a thorough understanding of identifying and mitigating vulnerabilities. The use of Nessus and OpenVAS highlighted the importance of regular vulnerability assessments. This lab reinforced the critical nature of firewall configurations in network security and provided valuable skills in penetration testing methodologies and tools. The experience gained is crucial for securing any organizational network against potential threats.
