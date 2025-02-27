# ilSpy With My Little Eye CTF Challenge Writeup

## Problem
Oh no! You've been hit by a new strain of ransomware called SharpRansom that is encrypting all of your files. It wants you to pay 5 Bitcoins in order to decrypt them!?! No way. Fortunately, you have a copy of the malware, and it's up to you to analyze `SharpRansom.exe` to recover a valid decryption password. This cyber criminal isn't that great of a programmer, so I bet you'll C# the flag quickly!

## Overview
A malicious ransomware called SharpRansom is demanding 5 bitcoins to decrypt files. Instead of paying, we'll analyze the executable to find the decryption key.

## Tools Used
- **dnSpy** - A .NET decompiler and debugger for analyzing C# executables  
  [dnSpy GitHub Repository](https://github.com/dnSpy/dnSpy)

## Analysis Process

### 1. Initial Static Analysis
- Downloaded and installed dnSpy from GitHub.
- Loaded `SharpRansom.exe` into dnSpy for safe analysis without execution.

  ![dnSpy_Ui1Z4BKQdw](https://github.com/user-attachments/assets/a489ee6b-c5b2-43a2-a46c-1dec2d3c9f3f)

### 2. Metadata Examination
- Found interesting metadata also examining the executable using Notepad++:
  - **Description** contains hidden message: `"bonus: criminals_leave_metadata_behind_too"`

    ![notepad++_GFcRMNGlAF](https://github.com/user-attachments/assets/f4c3c535-dbad-47b6-9a89-1ae2eebd3968)

### 3. Code Analysis
- Located the main `SharpRansom` class in dnSpy.
- Identified critical `Button1_Click_1` event handler containing decryption logic.
- Found hardcoded decryption key: `"i_spy_with_my_little_eye_an_aspiring_reverse_engineer"`

  ![dnSpy_uoN955tTL1](https://github.com/user-attachments/assets/be4d1863-fe49-40fe-af4d-3ca7ee814d07)

### 4. UI Analysis
The ransomware presents a simple Windows Forms interface with:
- Warning message about encrypted files.
- Input field for decryption code.
- Decrypt button to verify the entered code.

  ![dnSpy_WAqhw3TvzO](https://github.com/user-attachments/assets/55165333-13f6-47a3-a2de-b210d268cfe0)

## Solution
The flag is: `i_spy_with_my_little_eye_an_aspiring_reverse_engineer`

## Key Takeaways
This challenge demonstrates:
- Importance of static analysis in malware investigation.
- Value of examining metadata in compiled executables.
- Basic techniques for .NET reverse engineering.
- Common practices of storing sensitive information in code.

---

## Mitigation Strategies for Ransomware Attacks

### Mitigation Strategies
- **Regular Backups:**
  - Maintain frequent backups of important data.
  - Store backups offline or in a secure cloud environment.
  - Regularly test backup restoration processes.

- **Security Software:**
  - Use reputable antivirus and anti-malware solutions.
  - Keep security software updated to protect against the latest threats.

- **Patch Management:**
  - Regularly update operating systems and applications to fix vulnerabilities.
  - Implement automated patch management where possible.

- **User Training:**
  - Conduct cybersecurity awareness training for employees.
  - Educate users on recognizing phishing attempts and suspicious links.

- **Access Controls:**
  - Limit user permissions to only what is necessary for their roles.
  - Implement the principle of least privilege.

- **Network Segmentation:**
  - Segment networks to limit the spread of ransomware.
  - Isolate critical systems and sensitive data from the rest of the network.

- **Email Filtering:**
  - Use email filtering solutions to detect and block malicious attachments or links.
  - Scan emails for malware before they reach users' inboxes.

- **Multi-Factor Authentication (MFA):**
  - Implement MFA for all critical systems to enhance security.
  - Require multiple forms of verification before granting access.

### Best Practices During an Attack
- **Isolate Infected Systems:**
  - Disconnect affected machines from the network immediately to prevent further spread.
  - Identify and contain the extent of the infection.

- **Avoid Paying Ransom:**
  - Do not pay the ransom, as it does not guarantee data recovery and encourages further attacks.
  - Report the incident to law enforcement.

- **Assess Damage:**
  - Determine which files and systems are affected.
  - Analyze the type of ransomware involved for potential decryption solutions.

- **Incident Response Plan:**
  - Activate your incident response plan, involving IT and cybersecurity teams.
  - Document actions taken during the response for future reference.

- **Restore from Backups:**
  - If backups are available, restore affected systems from a clean backup.
  - Ensure that backups are free of ransomware before restoration.

- **Communication:**
  - Communicate with stakeholders and affected users about the situation and recovery efforts.
  - Provide updates regarding recovery status.

- **Post-Incident Analysis:**
  - Conduct a thorough investigation post-attack to identify how the breach occurred.
  - Implement lessons learned into future prevention strategies.

By following these mitigation strategies and best practices, organizations can reduce the risk of ransomware attacks and effectively respond if an incident occurs.
