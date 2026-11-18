# NETWORKWALKS-B084D-WK3-PMs-PASSWORD-CRACKING-WITH-JTR-AND-NW-TOOLS

## Objective
Recover the password of password-protected PDF files to understand how
password cracking works, how hashes are extracted from locked files, and
why weak passwords are a security risk.

## Modules Completed
- W3-PM1: Password Cracking with JTR (John the Ripper)
- W3-PM2: Password Cracking with Networkwalks Tools (Hash Calculator + Password Cracker)

## Tools Used
- Kali Linux (VirtualBox)
- John the Ripper (`pdf2john`, `john`)
- Networkwalks Hash Calculator (https://networkwalks.com/hash-calculator/)
- Networkwalks Password Cracker (https://networkwalks.com/password-cracker/)

----
## Module 1: Password Cracking with JTR
### Approach
I originally attempted using John the Ripper and Johnny GUI on Windows, but
ran into repeated issues (incorrect executable paths, Johnny crashing).
Switched to Kali Linux's pre-installed John the Ripper, which the project
brief notes is also an acceptable method.

### Steps
1. Transferred the locked PDF files into Kali.
2. Extracted the crackable hash using `pdf2john`:

pdf2john “My Locked PDF1.pdf” > hash1.txt

3. Ran John the Ripper against the hash:

john hash1.txt

4. Retrieved the cracked password:

john --show hash1.txt

5. Opened each PDF using the recovered password.

### Files Cracked
| File | Password |
|---|---|
| My Locked PDF1.pdf | good-luck |
| My Locked PDF2.pdf | [password1 |
| My Locked PDF3.pdf | 1qaz2wsx |

### Troubleshooting Notes
Documented a few real issues along the way: VirtualBox "inaccessible"
VM error from opening the VM straight out of a .7z archive, and Johnny GUI being
unstable on Windows, which is why the Kali CLI method was used instead.

---
## Module 2: Password Cracking with Networkwalks Tools

### Approach
Used Networkwalks' own browser-based tools, no installation required.

### Steps
1. Uploaded the locked PDF to the Hash Calculator
   (https://networkwalks.com/hash-calculator/) to extract the `$pdf$...` hash.
2. Copied the full hash value.
3. Pasted it into the Password Cracker
   (https://networkwalks.com/password-cracker/).
4. Ran the dictionary attack using the built-in wordlist.
5. Tool returned the cracked password, which matched the one found with JTR. Did same for Locked PDFs 2 &3

## Comparison of Methods

| | JTR (Kali) | Networkwalks Tools |
|---|---|---|
| Installation needed | Pre-installed on Kali | None, browser only |
| Where it runs | Locally | Locally in-browser (hash never uploaded) |
| Attack type | Dictionary/wordlist | Dictionary/wordlist |
| Result | password1 | password1 |

## What I Learned
- Weak, short, common passwords (like `password1`) can be cracked almost
  instantly with a basic dictionary attack.
- The hash itself isn't the password, it's a one-way scrambled
  representation, so cracking tools work by testing guesses against it
  rather than reversing it.
- Having a command-line and a GUI/browser-based option is useful: the
  browser tool is faster for quick checks, while JTR offers more control
  and works offline.

## Files in this folder
- [JTR hash files](hash1.txt), [hash2.txt](hash2.txt), [hash3.txt](hash3.txt)
- Screenshots 
