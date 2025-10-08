# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
<img width="649" height="514" alt="Screenshot 2025-10-08 082359" src="https://github.com/user-attachments/assets/c643073a-2fc7-44ac-9a41-d08e14715d17" />

<img width="564" height="695" alt="Screenshot 2025-10-08 083108" src="https://github.com/user-attachments/assets/43925fad-d3ad-4230-b6bf-eb1201c0d548" />

<img width="1673" height="887" alt="Screenshot 2025-10-06 202023" src="https://github.com/user-attachments/assets/ac0c1c67-9fa9-4a7a-b260-19b0e5146a27" />

<img width="1917" height="1071" alt="Screenshot 2025-10-06 202212" src="https://github.com/user-attachments/assets/4f27e353-4f25-40db-ba4a-394bdf824fad" />

<img width="1680" height="906" alt="Screenshot 2025-10-06 202252" src="https://github.com/user-attachments/assets/028a97ab-1b44-428a-8266-71c209a17430" />

<img width="1683" height="889" alt="Screenshot 2025-10-06 202946" src="https://github.com/user-attachments/assets/289e3628-f622-4662-9b7d-faa5269b5887" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

