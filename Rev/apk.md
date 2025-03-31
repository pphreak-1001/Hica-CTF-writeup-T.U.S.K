
## Challenge Overview
We were provided with an APK file and tasked with extracting a flag from it. This writeup documents the approach taken to analyze and reverse-engineer the APK to retrieve the flag.

## Steps to Solve

### Step 1: Preparing the Environment
To begin, we moved the APK to a working directory and used JADX (a decompiler) to analyze it:
```bash
mv app.apk /usr/share/jadx/bin
cd /usr/share/jadx/bin
jadx app.apk
```
JADX attempted to decompile the APK but reported some errors. Despite this, it still generated output files that we could analyze.

### Step 2: Exploring Decompiled Files
JADX creates two main folders after decompiling:
- `sources/` - Contains decompiled Java source code.
- `resources/` - Contains assets and XML configuration files.

Navigating to the decompiled output directory:
```bash
cd app
ls
```
The presence of `sources` and `resources` suggested that we could perform further analysis.

### Step 3: Searching for the Flag
A common technique in APK reverse engineering is searching for keywords related to flags. We used the `strings` command to scan all files for relevant information:
```bash
find /usr/share/jadx/bin/app/ -type f -exec strings {} + | grep CTF
```
This command revealed multiple references to `CTF_HICA_2025` and a flag format pattern:
```
CTF_HICA_2025
This awesome CTF app
Elite CTF master
Other CTFs
HackFlag CTF - Login>
HackFlag CTF
CTFApp
CTFs are boring
The final flag format is: CTF_HXXA_2YY5
You've completed all challenges! You're a true CTF master!
CTF Challenges - Score:
CTF_HICA_2025
This awesome CTF app2
Elite CTF master
Other CTFs
HackFlag CTF - Login2
HackFlag CTF2
CTFApp
CTFs are boring
The final flag format is: CTF_HXXA_2YY5
You've completed all challenges! You're a true CTF master!
CTF Challenges - Score:
CTF_HICA_2025
This awesome CTF app
Elite CTF master
Other CTFs
HackFlag CTF - Login>
HackFlag CTF
CTFApp
CTFs are boring
The final flag format is: CTF_HXXA_2YY5
You've completed all challenges! You're a true CTF master!
CTF Challenges - Score:
```
Given the repeated occurrences of `CTF_HICA_2025`, it was highly likely to be the flag.

### Step 4: Submitting the Flag
From our findings, the extracted flag was:
```
HICA{CTF_HICA_2025}
```
Submitting this confirmed that it was correct.

---
### Tools Used:
- `jadx` - Java Decompiler for APKs
- `strings` - Extract readable text from binary files
- `grep` - Search for specific patterns within text

