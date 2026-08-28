# networkwalks-B082-week3--Password-Cracking
 In this project, I used JTR johnny and john tools for the first time to crack  password. Here I also used, networkwalks tolls . 

# Week 3 Project Report: Password Cracking with JTR and Networkwalks Tools

**Course:** Cybersecurity & Ethical Hacking — Networkwalks Academy
**Module:** Week 3, Project Modules 1 & 2

## Objective

The objective of this project was to recover the password of a protected PDF file using two different password cracking approaches: John the Ripper (JTR) with its Johnny graphical interface, and Networkwalks' own browser-based Hash Calculator and Password Cracker tools. The exercise demonstrates, hands-on, how password cracking actually works: a locked file does not store its password in plain text but as a hash, and recovering that password means extracting the hash and testing candidate passwords against it until one matches.

All work was carried out in an authorized training environment against a PDF file supplied by the course specifically for this exercise.

## Tools Overview

| Module | Tool | Type | Role in Attack |
|---|---|---|---|
| 1 | John the Ripper (jumbo build) | Desktop, command-line engine | Runs the actual dictionary attack against the hash |
| 1 | Johnny | Desktop GUI | Graphical front end for John the Ripper |
| 2 | Networkwalks Hash Calculator | Browser-based, client-side | Extracts a crackable hash from the locked PDF |
| 2 | Networkwalks Password Cracker | Browser-based, client-side | Runs a dictionary attack against the extracted hash |

## Module 1: Password Cracking with John the Ripper

John the Ripper is an open-source password cracking tool used by security professionals to test password strength. Originally built for Unix systems, it now supports Windows, Linux, and macOS, and can crack many hash types, including those from password-protected PDF, ZIP, and Office files. Johnny is its graphical front end, giving it a point-and-click interface so the tool can be operated without typing raw commands.

| Step | Action |
|---|---|
| 1 | Installed the jumbo build of John the Ripper for Windows from the official Openwall distribution (chosen over core John for broader hash/attack type support, including PDF) |
| 2 | Installed the Johnny GUI and pointed it at the John the Ripper executable via *Settings* |
| 3 | Extracted the PDF's password hash using a pdf2john-style extractor, producing a string in `$pdf$...` format, and saved it to a text file |
| 4 | Loaded the hash file into Johnny via *Open password file* |
| 5 | Ran *Start new attack*, launching a dictionary attack against the hash |
| 6 | Johnny reported the attack complete: `100% (1/1: 1 cracked, 0 left) [format=PDF]` |
| 7 | Opened the locked PDF and entered the recovered password to confirm it unlocked the file |

**Result:**

| Item | Value |
|---|---|
| Tool | John the Ripper 1.9.0-jumbo-1 (Cygwin 64-bit x86_64) via Johnny GUI |
| Attack type | Dictionary attack |
| Cracked password | `good-luck` |
| Flag captured | `nw{cybersecurity_flag_captured_2608}` |

## Module 2: Password Cracking with Networkwalks Tools

The second module repeated the same underlying attack using Networkwalks' own free, browser-based tools rather than a locally installed application — the same principle as John the Ripper, executed entirely client-side with no installation required.

| Step | Action |
|---|---|
| 1 | Opened the Networkwalks Hash Calculator and uploaded the locked PDF under its *PDF* tab |
| 2 | The tool parsed the file locally and returned a crackable hash (`$pdf$...`) along with the PDF's revision, version, and key length |
| 3 | Copied the full hash value |
| 4 | Opened the Networkwalks Password Cracker and pasted the hash in |
| 5 | Started the attack, which hashed each word in a built-in wordlist and compared it to the target hash |
| 6 | Tool reported a match after working through the 100-word built-in list |
| 7 | Opened the locked PDF and entered the recovered password to confirm it unlocked the file |

**Result:**

| Item | Value |
|---|---|
| Tools | Networkwalks Hash Calculator → Networkwalks Password Cracker |
| PDF metadata | Revision R4, Version V4, Key length 128-bit |
| Attack type | Dictionary attack (built-in 100-word list) |
| Cracked password | `password1` |
| Flag captured | `nw{networkwalks_persistence_jtr_270521}` |

## Combined Results Summary

| Module | Tools Used | Attack Type | Password Recovered | Flag Captured |
|---|---|---|---|---|
| 1 — John the Ripper | Johnny + John the Ripper (jumbo) | Dictionary attack | `good-luck` | `nw{cybersecurity_flag_captured_2608}` |
| 2 — Networkwalks Tools | Hash Calculator + Password Cracker | Dictionary attack | `password1` | `nw{networkwalks_persistence_jtr_270521}` |

## Key Concepts

| Concept | Explanation |
|---|---|
| Encryption vs. hashing | Encryption is two-way — data can be decrypted with the correct key. Hashing is one-way — it produces a fixed value used to validate data, not recover it. A protected PDF checks a password by hashing it and comparing to a stored hash, which is why cracking (not decrypting) is required. |
| Dictionary attack | Instead of testing every possible character combination (brute force), a prepared wordlist of likely passwords is hashed and compared to the target hash. Far faster than brute force when the real password is a common word or simple pattern. |
| GUI vs. browser-based tooling | Johnny wraps John the Ripper's command-line engine in a desktop GUI, suited to more serious or repeated testing. The Networkwalks tools reproduce the same workflow entirely in-browser, with no installation and no data leaving the local machine. |

## Evidence

<img width="873" height="687" alt="Screenshot (80)" src="https://github.com/user-attachments/assets/b74d2beb-e3a8-4899-8f97-afad17be34d7" />

<img width="873" height="687" alt="Screenshot (81)" src="https://github.com/user-attachments/assets/2a82b186-2bf5-4a4c-8f9a-96080c4084ca" />

<img width="661" height="871" alt="Screenshot (82)" src="https://github.com/user-attachments/assets/acd8c538-91fd-4021-a2f7-5c97c8653ea0" />

<img width="1147" height="951" alt="Screenshot (83)" src="https://github.com/user-attachments/assets/26aa81e3-1b5f-46b6-bcdf-9dd33982ec6d" />

<img width="1171" height="951" alt="Screenshot (84)" src="https://github.com/user-attachments/assets/19d65739-ad37-4ac3-a75c-4a3a953c6a88" />

<img width="670" height="924" alt="Screenshot (86)" src="https://github.com/user-attachments/assets/d7f60cd2-48b1-4ee4-b63a-16740a3bc23d" />

---

## 👤 Author

**Adib Salman Azam**
Cybersecurity Trainee, Networkwalks Program B082

## 📌 Project Information

**Instructor:** Waqas Karim CCIE |
**Program Name:** Internship program at Networkwalks | **Week:** 03 | **Repository:** GitHub

---

> ⚠️ **Disclaimer:** These materials are for education and research purposes only, performed under written permission on systems the author owns or is authorized to test.




