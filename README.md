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
Cracked Passwords from Hash File

<img width="745" height="914" alt="Screenshot 2025-09-27 164813" src="https://github.com/user-attachments/assets/8f7d3322-f29b-48fb-9380-f5a1789af28b" />

<img width="757" height="925" alt="Screenshot 2025-09-27 164918" src="https://github.com/user-attachments/assets/0863467c-a89c-46b6-856b-2ce5eb5b3530" />

<img width="646" height="293" alt="Screenshot 2025-09-27 164945" src="https://github.com/user-attachments/assets/3d61ea29-353a-4eb4-a051-b498c786c826" />

<img width="642" height="327" alt="Screenshot 2025-09-27 165007" src="https://github.com/user-attachments/assets/45cd76fa-44b6-4d62-836c-92e72b96f345" />

<img width="677" height="811" alt="Screenshot 2025-09-27 165206" src="https://github.com/user-attachments/assets/4a623c52-335a-46d4-a893-7997fe49a55b" />

<img width="749" height="786" alt="Screenshot 2025-09-27 165434" src="https://github.com/user-attachments/assets/1c868826-d2a1-404e-828f-fd7137e1ab93" />

<img width="628" height="666" alt="Screenshot 2025-09-27 165651" src="https://github.com/user-attachments/assets/235df163-341c-4db5-89c2-4f67901a0401" />

<img width="541" height="473" alt="Screenshot 2025-09-27 165703" src="https://github.com/user-attachments/assets/ccd69f37-d5e9-4728-be6c-1bf4a8eab5a2" />


## RESULT:
The password hashes were successfully cracked using John the Ripper.

