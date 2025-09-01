# Brute-Force-Detection-Splunk
Detect SSH brute force attempts using Splunk (SOC Analyst Project)

# 🔐 Brute Force Attack Detection using Splunk  

## 📖 Project Overview  
This project demonstrates detection of **SSH Brute Force Attacks** using Splunk.  
As part of my SOC Analyst learning, I built a small lab environment, simulated brute force attempts, and created dashboards & alerts to monitor suspicious login activity.  

---

## 🖥️ Technologies Used  
- Splunk Enterprise (Free Trial)  
- Ubuntu Linux (Target & Attacker)  
- Windows + VirtualBox (Host)  
- OpenSSH (SSH Service)  
- Syslog / Log Forwarding  

---

## ⚙️ Lab Setup  
- **Host Machine**: Windows (VirtualBox)  
- **VM 1**: Ubuntu (Attacker)  
- **VM 2**: Ubuntu (Target with SSH enabled)  
- **Tool**: Splunk Enterprise  

---

## 🛠️ Steps Performed  
1. **Lab Setup**  
   - Installed Ubuntu VM with SSH service enabled  
   - Installed Splunk on monitoring system  

2. **Log Collection**  
   - Forwarded SSH authentication logs (`/var/log/auth.log`) into Splunk  

3. **Simulated Attack**  
   - Performed multiple failed SSH login attempts to generate brute force logs  

4. **Dashboard Creation**  
   - Visualized failed login attempts by IP in Splunk dashboard  

5. **Alert Configuration**  
   - Configured real-time alert for brute force attempts  

---

## 🔍 Detection Logic  
Splunk SPL query used to detect brute force attempts:  
```spl
index=soclab sourcetype=linux:auth "Failed password"

## 📜 License  
This project is licensed under the MIT License.

| stats count by src_ip
| where count > 10
