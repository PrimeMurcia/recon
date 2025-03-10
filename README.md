# Penetration Testing Reconnaissance Guide

## Introduction
This guide provides a structured approach to gathering intelligence on a target system before launching a penetration test. It covers domain and IP information gathering, web technologies detection, employee reconnaissance, subdomain enumeration, port scanning, and vulnerability scanning using various tools.

---

## 1. Gathering Domain & IP/DNS Information

### **Host Utility**
- `host example.com` - Get IP address of a domain

### **Nslookup**
- `nslookup example.com` - Query domain name system (DNS) information

### **DNSRecon**
- `dnsrecon -d example.com` - Perform DNS enumeration

### **Dig**
- `dig example.com ANY +noall +answer` - Retrieve all available DNS records

### **WAF Detection (Wafw00f)**
- `wafw00f -a example.com` - Detect Web Application Firewall

---

## 2. Gathering Domain/Website Information

### **Discovering Web Technologies (WhatWeb)**
- `whatweb example.com` - Identify web technologies used

### **Gathering Employee Information**
- `theHarvester -d example.com -b linkedin` - Collect employee details from LinkedIn

### **Gathering Employee Emails**
- `theHarvester -d example.com -b google` - Extract email addresses

---

## 3. Passive Subdomain Enumeration

### **With Sublist3r**
- `sublist3r -d example.com -v -t 100` - Find subdomains passively

### **With Google Dorks**
- `site:example.com -www` - Discover hidden subdomains

---

## 4. Active Recon Techniques

### **DNS Zone Transfers**
#### **With DNSRecon**
- `dnsrecon -d example.com -t axfr` - Attempt a zone transfer

#### **With Fierce**
- `fierce -dns example.com` - Discover subdomains via DNS brute-force

### **Subdomain Brute-force**
#### **With Knockpy**
- `knockpy example.com` - Brute-force subdomains

---

## 5. Port Scanning

### **With Nmap**
- `nmap -p- example.com` - Scan all 65535 ports

### **Nmap Script Scan**
- `nmap -sC -sV -T4 example.com` - Run scripts for version detection

---

## 6. Directory Brute-Force

### **Tools:**
- **Gobuster**: `gobuster dir -u http://example.com -w wordlist.txt`
- **Dirb**: `dirb http://example.com wordlist.txt`
- **Dirbuster**: GUI-based tool for directory enumeration

---

## 7. Website Vulnerability Scanning

### **With Nikto**
- `nikto -h http://example.com` - Scan for web vulnerabilities

### **CMS Vulnerability Scanning**
#### **CMSMap**
- `cmsmap http://example.com` - Scan CMS for vulnerabilities
#### **WPScan (WordPress)**
- `wpscan --url http://example.com --enumerate u` - WordPress user enumeration
#### **JoomScan (Joomla)**
- `joomscan -u http://example.com` - Scan Joomla websites

---

## 8. Automated Recon Frameworks

### **Sn1per**
- `git clone https://github.com/1N3/Sn1per`
- `cd Sn1per`
- `bash install.sh`

#### **Automating Passive Recon**
- `sniper -t example.com`

#### **Automating Active Recon**
- `sniper -t example.com -m active`

### **OWASP Amass**
- `amass enum -passive -d example.com` - Passive subdomain enumeration
- `amass enum -active -d example.com` - Active subdomain enumeration

---

## Conclusion
This guide serves as a comprehensive reference for reconnaissance during penetration testing. Always ensure you have permission before scanning any system.

