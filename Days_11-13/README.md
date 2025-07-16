## 📆 Days 11–13: Brute Force Detection & Log Ingestion

## Day 11: Brute Force Attacks & Detection Basics

### 🔍 What is a Brute Force Attack?

A brute force attack is a trial-and-error method to guess login credentials. It’s repetitive, often automated, and one of the most common threats SOC analysts must detect.

### 🧱 Common Types:
- **Classic Brute Force** – Tries all possible combinations
- **Dictionary Attack** – Uses common passwords
- **Credential Stuffing** – Tries previously leaked login pairs
- **Hybrid Attack** – Combines dictionary + complexity

### 🧰 Tools Used:
- **Hydra**
- **John the Ripper**
- **Hashcat**

### 📌 Key Takeaway:
Brute force attacks are basic but persistent. Understanding their behavior is essential for defenders to build solid detection logic.

---

## 🧾 Day 12: Ubuntu SSH Log Activity

I deployed a new Ubuntu Server 24.04 on Vultr and exposed SSH to observe brute force activity in real time.

After a few hours of idling, I explored the logs:

```bash
cd /var/log
grep -i failed auth.log
