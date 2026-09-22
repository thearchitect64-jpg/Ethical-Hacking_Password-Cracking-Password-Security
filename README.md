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
<img width="824" height="154" alt="image" src="https://github.com/user-attachments/assets/7fd0dff5-914f-41bb-8663-f3ec54738615" />
<img width="986" height="74" alt="image" src="https://github.com/user-attachments/assets/2e7676d2-408a-43bf-806e-2b1beb189038" />
<img width="658" height="52" alt="image" src="https://github.com/user-attachments/assets/1cb114bd-789c-44af-9d81-573f9e3ab7b0" />


# **4. W3-PM2 — Password Cracking with Networkwalks Tools**

For the second module, I used the browser-based Networkwalks tools instead of the locally installed JTR/Johnny workflow.

## 4.1 Hash Calculator

I opened the Networkwalks Hash Calculator and uploaded My Locked PDF1.pdf.

<img width="1816" height="322" alt="image" src="https://github.com/user-attachments/assets/0e1012be-e5a2-46ff-8ab2-0544477c9986" />

The lab explains that the Hash Calculator extracts a PDF-compatible hash beginning with:
```
$pdf$
```

## 4.2 Networkwalks Password Cracker

I then opened the Networkwalks Password Cracker and pasted the extracted PDF hash. The lab instructs the user to start the attack and allow the tool to try different passwords until a match is identified.

<img width="1776" height="1026" alt="image" src="https://github.com/user-attachments/assets/2f448d16-c35a-4691-9cf0-3a33354c7d80" />

### Password Cracker Issue 🛑

During my attempt, the Networkwalks Password Cracker had difficulty recovering the password from the first locked PDF hash. The initial cracking attempt did not successfully complete the password recovery.

Rather than treating the unsuccessful attempt as the end of the exercise, I reviewed the available cracking options and changed the dictionary being used.
I uploaded a new wordlist:
```
JtR_default_password
```
I then used the new wordlist with the extracted hash and restarted the password-cracking process.

This gave me practical experience with an important troubleshooting concept: the result of a password-cracking attempt can depend heavily on the quality and coverage of the wordlist being used. A failed dictionary attack does not necessarily indicate that the password is strong; it can also indicate that the password is not contained in the selected dictionary.

The Networkwalks lab similarly demonstrates the use of a password dictionary and explains that the cracking process continues until a matching password is found. The uploaded wordlist contained 3550+ words; the password cracker stopped at ~3450 once the password was found.

<img width="1634" height="1306" alt="image" src="https://github.com/user-attachments/assets/f07510c3-871f-498f-b4c4-da71a4b20072" />


# **5.  Activities Performed**

| Activity                      | What I Did                                               | Result / Observation                                                             |
| ----------------------------- | -------------------------------------------------------- | -------------------------------------------------------------------------------- |
| JTR installation              | I downloaded and extracted John the Ripper 1.9.0 Jumbo.  | JTR files were available in the `run` directory.                                 |
| Johnny installation           | I installed the Johnny GUI.                              | Johnny opened successfully.                                                      |
| JTR configuration             | I configured Johnny to use `john.exe`.                   | Johnny detected the JTR Jumbo installation.                                      |
| PDF hash extraction           | I extracted the password hash from `My Locked PDF1.pdf`. | A `$pdf$` formatted hash was produced.                                           |
| Hash file creation            | I saved the extracted hash as `hash1.txt`.               | Hash was prepared for use by Johnny.                                             |
| Johnny attack                 | I loaded `hash1.txt` and started a new attack.           | I performed the JTR password-recovery process.                                   |
| Networkwalks Hash Calculator  | I uploaded the protected PDF.                            | The tool generated a PDF password hash.                                          |
| Networkwalks Password Cracker | I pasted the hash and started the attack.                | The first attempt had difficulty recovering the password.                        |
| Wordlist troubleshooting      | I uploaded `JtR_default_password`.                       | I changed the dictionary used by the Password Cracker and restarted the process. |
| PDF verification              | I used the recovered password to test the protected PDF. | This provided final confirmation of the password-recovery process.               |


# **6. Risk Analysis / Impact**

| Finding / Observation                                                  | Evidence From My Project                                                                                                                       | Potential Security Impact                                                                                                                                | Risk Level |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| Password-protected PDF could be subjected to offline password recovery | I extracted a `$pdf$` hash and tested it using password-cracking tools.                                                                        | If an attacker obtains a password hash, they may attempt offline password recovery without repeatedly interacting with the original application or file. | Medium     |
| Dictionary attacks can recover weak or commonly used passwords         | The Networkwalks Password Cracker uses a password dictionary, and I was able to change the wordlist when the initial attempt was unsuccessful. | Weak passwords that appear in common dictionaries may be recovered more easily.                                                                          | High       |
| Wordlist selection affects cracking results                            | The first Password Cracker attempt had difficulty with the original hash; I then uploaded `JtR_default_password` as an additional wordlist.    | A password may resist one dictionary while being discovered by another dictionary with better coverage.                                                  | Medium     |
| Password hashes should be protected                                    | I was able to extract a PDF password hash for testing.                                                                                         | Anyone who obtains an applicable password hash may attempt offline cracking.                                                                             | High       |
| Short or predictable passwords increase exposure                       | The lab explains that short or common passwords can be recovered more quickly.                                                                 | Weak passwords can reduce the protection provided by password-based encryption.                                                                          | High       |
| Browser-based tools reduce setup requirements                          | W3-PM2 allowed me to perform the activity without installing cracking software.                                                                | Security personnel should understand that password-recovery capabilities can be accessible without a complex local toolset.                              | Low        |


### Risk Analysis Narrative

I did not treat the password-cracking exercise itself as evidence that the PDF encryption was defective. Instead, I used the exercise to evaluate how password selection affects the practical resistance of a protected file.

The most important observation from my work was that wordlist selection matters. My initial attempt with the Networkwalks Password Cracker did not successfully recover the password from the first PDF hash. I responded by uploading the JtR_default_password wordlist and repeating the process. This demonstrated that password recovery can depend on both the cracking method and the contents of the dictionary being used.

The W3-PM2 lab explains that password cracking attempts different words until a matching value is found and that the time required depends on password complexity.


# **7. Recommendations**

Based on what I learned during these exercises, I would recommend using long, unique passwords instead of short or predictable passwords.

I would also recommend avoiding passwords that are likely to appear in common password dictionaries. My experience with the JtR_default_password wordlist demonstrated how changing the dictionary can change the results of a cracking attempt.

Organizations should also protect password hashes and encrypted files because possession of a hash can provide an opportunity for offline password-recovery attempts.

For sensitive documents, I would combine strong passwords with appropriate encryption and access controls rather than relying on a password that is easy to guess.

Finally, password-recovery testing should only be performed against files and systems for which authorization has been provided. My activities were completed using the assigned Networkwalks educational material.

# **8. Takeaways**

The biggest lesson I took from these projects was that password security depends on more than simply encrypting a file. The strength and predictability of the password, along with the ability to obtain and test a password hash, can significantly affect the practical security of protected information.

These exercises strengthened my understanding of password hashes, dictionary attacks, wordlists, password recovery, and security testing while giving me additional hands-on experience with tools used in cybersecurity.

