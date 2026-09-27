# NETWORKWALKS-SEMILORE-B083-WK3-PM1-2-PASSWORD-CRACKING-WITH-JTR
Isolated virtual lab exercise for cybersecurity testing and penetration testing practicals

<h3 align='center'> Cracking a Password-Protected PDF with John the Ripper </h3>

## Overview
This exercise demonstrates how to recover a password from an encrypted PDF file using John the Ripper, a widely used password-cracking tool. The goal was to understand how PDF encryption can be attacked when weak or common passwords are used, and to practice the full workflow — from hash extraction to verification.

## Tools Used
- **Kali Linux**
- **John the Ripper** (`john`)
- **hash1** (John's PDF hash extraction utility)
- **qpdf** — for decrypting the file once the password was recovered

## Methodology

### 1. Extracting the Hash
PDF files can't be fed directly into John — the encryption metadata first has to be converted into a crackable hash format:

```bash
pdf2john My_Locked_PDF1.pdf > hash1.txt
```

### 2. Running the Dictionary Attack
With the hash extracted, I ran John against it
  
```bash
john hash1.txt
```

### 3. Verifying the Result
Once John found a match, I retrieved the cracked password:

```bash
john --show pdf_hash.txt
```

### 4. Decrypting the File
With the password known, I used `qpdf` to remove the encryption and produce a readable copy:

```bash
qpdf --password=<recovered_password> --decrypt target.pdf decrypted.pdf
```
### 5. Pictures 
<p align='center'>
<img width="574" height="817" alt="Screenshot 2026-09-27 163652" src="https://github.com/user-attachments/assets/6678a3cd-de9b-42bc-9337-2e320d717193" /> 
  
<img width="570" height="805" alt="Screenshot 2026-09-27 163709" src="https://github.com/user-attachments/assets/54d9f839-486f-4441-94e9-692f7788ea64" />

<img width="584" height="753" alt="Screenshot 2026-09-27 163949" src="https://github.com/user-attachments/assets/2129f73d-eef7-4a77-81ca-8edce5977485" />

</p>

## Key Takeaways
- PDF password protection is only as strong as the password itself — dictionary attacks succeed quickly against common or reused passwords.
- Hash extraction (via `pdf2john`) is a necessary intermediate step since John operates on hashes, not files directly.
- This exercise reinforced why organizations should enforce strong, unique passwords even on "static" documents, since PDFs are frequently shared and stored long-term.

## Disclaimer
This exercise was performed in a controlled lab environment on a file I created/own for learning purposes. Attempting to crack passwords on files you do not own or lack authorization to test is illegal.
  

  👤 Author  
Ademuyiwa Oluwasemilore T.  
Cybersecurity Professional B083F  
LinkedIn: https://www.linkedin.com/in/ademuyiwa-o-4904412a2/  
📌 Project Information  
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub  
