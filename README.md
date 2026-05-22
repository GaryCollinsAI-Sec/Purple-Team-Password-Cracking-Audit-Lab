# Purple Team Password & Audit Lab

## Overview

This project demonstrates a controlled purple team exercise focused on password security analysis and defensive log visibility within a Linux environment.

The lab simulates:
- Password hash generation
- Offline password cracking attempts
- System log analysis for authentication activity
- Identification of detection opportunities using native Linux logging

All testing was performed in a local, isolated environment using synthetic credentials.

---

## Objectives

- Simulate credential access using password hash cracking techniques
- Evaluate password strength using dictionary-based attacks
- Analyze authentication activity using native Linux logging tools
- Identify detection opportunities from system-generated logs
- Demonstrate purple team methodology (attack and defense lifecycle)

---

## Tools Used

- Kali Linux
- OpenSSL
- John the Ripper
- systemd journal (`journalctl`)

---

## Lab Workflow

### 1. Password Hash Generation
Mock credentials were generated using OpenSSL SHA-512 crypt hashing.

### 2. Password Cracking Simulation
Offline password cracking was performed using John the Ripper with a dictionary-based attack using a standard wordlist.

### 3. Defensive Log Analysis
System authentication logs were analyzed using `journalctl` to identify login activity, authentication failures, and privilege escalation indicators.

---

## Screenshots

<img width="630" height="61" alt="Screenshot From 2026-05-21 22-20-07" src="https://github.com/user-attachments/assets/35a2106f-765e-4d02-89c1-7b93afd219c2" />

<img width="640" height="128" alt="Screenshot From 2026-05-21 22-19-47" src="https://github.com/user-attachments/assets/34d150ac-3ffa-44f7-840e-1cf5baa878e8" />

<img width="629" height="214" alt="Screenshot From 2026-05-21 22-38-14" src="https://github.com/user-attachments/assets/1ce43a8d-8d03-4f79-b583-a6f8c896f143" />

<img width="809" height="343" alt="Screenshot From 2026-05-21 22-52-26" src="https://github.com/user-attachments/assets/4115db6f-55f2-4a03-8106-ae14bd94a295" />


<img width="809" height="220" alt="Screenshot From 2026-05-21 22-55-00" src="https://github.com/user-attachments/assets/81dd2604-2cbd-4e76-9389-9e738d463732" />

<img width="818" height="291" alt="Screenshot From 2026-05-21 22-56-17" src="https://github.com/user-attachments/assets/8f9f9d30-0fda-446a-91d8-70f46ffeb868" />

---

## Key Findings

- Weak passwords are highly susceptible to dictionary-based attacks
- Password complexity significantly impacts cracking success
- Native Linux logging provides useful visibility into authentication behavior
- System logs can support basic detection of suspicious authentication patterns

---

## 🔐 Hardening Security

Based on findings from this exercise, the following security hardening measures were identified to improve password security and system visibility:

### Password Policy Hardening
- Enforce minimum password length of 12–14 characters
- Require complexity (uppercase, lowercase, numbers, symbols)
- Prevent reuse of previously used passwords
- Block common and dictionary-based passwords
- Promote passphrase-based authentication

### Authentication Security Enhancements
- Enable multi-factor authentication (MFA) for privileged accounts
- Disable direct root login via SSH where applicable
- Implement account lockout policies after repeated failed login attempts
- Apply least privilege principles for administrative access

### Logging & Monitoring Improvements
- Monitor authentication failures using system logs (`journalctl`)
- Track sudo usage and privilege escalation attempts
- Establish alert thresholds for repeated authentication failures
- Centralize logs into a SIEM platform for correlation and analysis

### System Hardening
- Regularly update and patch the operating system and packages
- Disable unnecessary services to reduce attack surface
- Restrict access to sensitive files such as `/etc/shadow`
- Monitor access to credential-related system files

### Detection Engineering Improvements
- Detect repeated authentication failures within short time windows
- Identify abnormal sudo command usage patterns
- Monitor unauthorized access attempts to sensitive files
- Map detections to MITRE ATT&CK techniques:
  - Credential Access (T1110)
  - Brute Force (T1110.001 / T1110.003)
  - Valid Accounts (T1078)

---

## Security Considerations

- No real credentials or systems were used
- All hashes were synthetically generated
- Testing was performed in an isolated local environment

---

## Disclaimer

This project was conducted in a fully isolated lab environment using synthetic credentials for educational and defensive security purposes only.

No real systems or credentials were targeted.
