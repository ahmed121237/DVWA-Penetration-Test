DVWA Penetration Testing — Practice Project

This repository documents a hands-on penetration testing exercise I performed against DVWA (Damn Vulnerable Web Application) as part of my self-learning journey in web application security.


Note: DVWA is an intentionally vulnerable application built for training purposes. This project was done in a local lab environment for learning and portfolio purposes — not a real client engagement.




🎯 Purpose

I built this project to practice the full penetration testing workflow — from finding a vulnerability to writing it up properly — instead of just running automated scanners. My goal was to understand why each vulnerability happens and how to explain it clearly, the way it would be documented in a real assessment.


🧪 What I Tested

I focused on 4 vulnerability categories from the OWASP Top 10:

VulnerabilityOWASP CategoryInsecure Direct Object Reference (IDOR)A01:2021 – Broken Access ControlSQL InjectionA03:2021 – InjectionCross-Site Scripting (XSS)A03:2021 – InjectionBroken AuthenticationA07:2021 – Identification & Authentication Failures


🛠️ Methodology

I followed a simplified version of the OWASP Web Security Testing Guide (WSTG):


Recon — explored the app manually to understand its structure and inputs
Testing — manually tried payloads on each module using Burp Suite
Exploitation — confirmed each vulnerability was real and exploitable, not just theoretical
Documentation — wrote each finding with steps, impact, and a suggested fix



🔍 Findings Summary

1. IDOR

Changed an ID value in the URL and was able to view data belonging to another user, without any authorization check on the server side.

2. SQL Injection

Found that the id parameter was inserted directly into a SQL query. Used a UNION-based payload to extract usernames and password hashes from the database.

3. Cross-Site Scripting (XSS)

Injected a simple <script> payload into an input field and confirmed it executed in the browser — meaning an attacker could steal session cookies this way.

4. Broken Authentication

Tested the login form with repeated failed attempts and found no rate limiting or account lockout, meaning brute-forcing credentials would be possible.

Full details with proof-of-concept steps and remediation notes are in report.md / report.pdf.


🧰 Tools Used


Burp Suite Community
OWASP ZAP
sqlmap (for verification)



📚 What I Learned


Most of these vulnerabilities come from the same root cause: trusting user input without validating it server-side.
Finding a bug is one thing — explaining it clearly with impact and a fix is a different (and important) skill.
Manual testing taught me more than running an automated scanner, because I had to actually understand why the payload worked.



📄 Full Report

A more detailed write-up (with proof-of-concept commands and remediation steps for each finding) is available here:


report.md
report.pdf



⚠️ Disclaimer

This testing was performed against DVWA in a local, isolated lab environment for educational purposes only. No real systems or user data were involved.
