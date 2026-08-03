# Cerber-Ransomware-Web-Compromise--Splunk

Executive Summary
This repository contains the threat hunting methodology, Splunk SIEM queries, and SOC investigation workflow used to analyze the Boss of the SOC (BOTS) v1 dataset. The analysis traces a full-spectrum cyberattack from external reconnaissance to credential compromise, payload staging, defense evasion, and Command & Control (C2) beaconing associated with Cerber Ransomware.

Attack Phase,Technique Name,MITRE ATT&CK ID,Indicators of Compromise (IoCs) / Artifacts
Reconnaissance,Active Scanning,T1595.002,Source IP: 40.80.148.42 (Acunetix Scanner)
Initial Access,Password Guessing,T1110.001,"Source IP: 23.22.63.114, Target: /joomla/administrator/index.php"
Execution,Command & Scripting Interpreter,T1059,php-cgi.exe execution via IIS pool (IIS APPPOOL\joomla)
Persistence / Evasion,Masquerading: Match Legitimate Name,T1036.005,osk.exe created in C:\Users\bob.smith...\AppData\Roaming\{GUID}\
Defense Evasion,Process Injection,T1055,osk.exe spawned iexplore.exe -nohome
Defense Evasion,Indicator Removal on Host,T1070.004,Self-deleting dropper: 121214.tmp
Impact / Recovery Inhibiting,Inhibit System Recovery,T1490,"""vssadmin.exe"" delete shadows /all /quiet"
Command & Control,Application Layer Protocol,T1071,Destination: 85.93.31.128:6892 (UDP / 44-byte beacons)

