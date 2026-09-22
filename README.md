# Ethical-Hacking_Password-Cracking-Password-Security
Password hacking w/ Hash Deciphering Tools

Pentester Name: Donald Mason

Program/Batch: B083-Networkwalks

Date: 22 September 2026

Modules Completed: W3-PM1 – Password Cracking with JTR; W3-PM2 – Password Cracking with Networkwalks Tools

Target: My Locked PDF1-3.pdf in the assigned educational lab environment

Permission: Yes: I performed these activities as part of the authorized Networkwalks cybersecurity training lab.

# **1. Introduction**

During Week 3 of my Networkwalks Cybersecurity Internship, I completed two hands-on password-security projects. The first project, W3-PM1 – Password Cracking with JTR, introduced me to John the Ripper and its graphical interface, Johnny. The second project, W3-PM2 – Password Cracking with Networkwalks Tools, allowed me to perform the same general password-recovery process using browser-based tools.

The purpose of these exercises was to demonstrate how password-protected files can be evaluated by extracting a password hash and attempting to recover the original password. The W3-PM1 lab explains that John the Ripper can be used to test password strength and work with password-protected files such as PDFs, ZIP files, and Office documents.

W3-PM2 used a different approach. Instead of installing a password-cracking application, I used the Networkwalks Hash Calculator to extract the PDF hash and the Networkwalks Password Cracker to attempt password recovery through a web browser.

These two projects allowed me to compare a locally configured password-cracking workflow with a browser-based password-recovery workflow.

# **2. Tools Used**

| Tool / Technology               | Purpose                                                                                                                              | Command / Method                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------- |
| Windows 11 VM                   | I used Windows 11 as the primary environment for the password-cracking exercises.                                                    | N/A                                            |
| John the Ripper 1.9.0 Jumbo     | I used JTR to perform password-recovery testing against the extracted PDF hash.                                                      | `john.exe`                                     |
| Johnny                          | I used Johnny as the graphical interface for John the Ripper.                                                                        | GUI                                            |
| John executable                 | I configured Johnny to use the main JTR executable.                                                                                  | `C:\JtR\john-1.9.0-jumbo-1-win64\run\john.exe` |
| PDF Hash Extractor              | I used the PDF hash extractor described by the W3-PM1 lab to extract the password hash from the protected PDF.                       | Browser-based                                  |
| Networkwalks Hash Calculator    | I used the Networkwalks tool to extract the `$pdf$...` hash from the protected PDF.                                                  | Browser-based                                  |
| Networkwalks Password Cracker   | I used the browser-based password-cracking tool to test the extracted hash.                                                          | Browser-based                                  |
| Notepad                         | I used Notepad to save the extracted hash as a text file.                                                                            | `hash1.txt`                                    |
| `JtR_default_password` wordlist | I uploaded this additional wordlist after the first Networkwalks Password Cracker attempt did not successfully recover the password. | Uploaded through the Password Cracker          |


The W3-PM1 requires John the Ripper, Johnny, extraction of the PDF hash, saving the hash as hash1.txt, and loading the hash into Johnny.

The W3-PM2 uses the Networkwalks Hash Calculator followed by the Password Cracker.

# **3. W3-PM1 — Password Cracking with JTR**
## 3.1 John the Ripper Installation

I began by downloading the Windows x64 version of John the Ripper 1.9.0 Jumbo. I extracted the complete JTR directory and located the run folder containing the John executables.

The lab specifically instructs users to locate john.exe inside the run directory when configuring Johnny.

I configured Johnny to use:
```
C:\JtR\john-1.9.0-jumbo-1-win64\run\john.exe
```
Johnny successfully detected the installed John the Ripper Jumbo version, confirming that the graphical interface was communicating with the JTR executable correctly.

## 3.2 PDF Hash Extraction

The next step was to obtain the password hash from the protected PDF. The W3-PM1 instructions direct the user to upload the encrypted PDF to the PDF hash-extraction service and copy the resulting hash beginning with $pdf$.

<img width="2008" height="596" alt="image" src="https://github.com/user-attachments/assets/c746b7c8-85a5-49b7-9215-9e362e2e77a3" />

The lab requires the extracted hash to be saved as a .txt text file before loading it into Johnny.
```
hash1.txt
```
I completed these steps for all locked PDFs provided.

## 3.3 Johnny Attack

I opened Johnny, selected Open password file, and loaded hash1.txt. I then used Start new attack to begin the password-recovery process. The lab explains that the time required can vary based on computer performance and password complexity.

This exercise gave me hands-on experience with the relationship between an encrypted PDF, its extracted hash, a password dictionary, and the cracking process.

<img width="2296" height="1364" alt="image" src="https://github.com/user-attachments/assets/2c7baf8d-745b-4f3c-9c0d-062bbfa97b11" />





