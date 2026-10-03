# -NETWORKWALKS-NomanA47-B083-WK4
A Black box penetration testing for the website of Mediroza Hospital
Week 4 — Mediroza General Hospital Penetration Test

NetworkWalks Internship | Batch B083 Target: https://medirozahospital.com Engagement Type: Black-box Penetration Test | 5 Days

This is a controlled, authorized training engagement conducted as part of my NetworkWalks internship. The target is a designated lab environment with written permission for testing. These techniques must never be applied to any system without explicit written authorization.

Overview

This week's project was a full black-box pentest against a training hospital website, structured around four milestones: gaining initial access to retrieve confidential patient data, cracking the encryption on what was retrieved, finding a critical data exposure elsewhere on the server, and writing it all up in a professional report.

I also used this as a chance to run the vulnerability scanner I built for my own PGD Cyber Security project against a live, authorized target — which is where the recon in this repo starts.

Tools Used

whois · nslookup · whatweb · nmap · wafw00f · gobuster · custom WebScan Pro vulnerability scanner (personal PGD project) · sqlmap · Metasploit Framework · John the Ripper / Johnny · NetworkWalks Hash Calculator & Password Cracker · manual SQL injection testing · curl

Summary of Findings
Finding	Risk
SQL injection authentication bypass on the patient portal	Critical
Exposure of 3 encrypted patient pathology reports	Critical
Exposed, unauthenticated database backup (staff + shareholder data)	Critical
Spring4Shell (CVE-2022-22965) flagged by automated scan	Informational — confirmed false positive
Inconsistent/adaptive network-layer filtering	Low
Staff portal login	Informational — tested, not breached

Full details, methodology, and remediation recommendations are in the report.

Repo Contents
Mediroza_Pentest_Report.pdf — full penetration testing report (Executive Summary, Scope & Methodology, Findings, Risk Ratings, Recommendations)
vulnerability_report.pdf — raw output from my own WebScan Pro scanner, the starting point for this engagement's recon
evidence/
Login bypass and portal access screenshots
Password-cracking proof for all 3 patient PDFs
Redacted pathology report screenshots (patient name, ID, DOB, and gender blacked out — test results and lab reference numbers left visible as proof of access)
Redacted SQL backup file (national_id and salary values replaced with [REDACTED])
nmap, wafw00f, whois, nslookup, whatweb recon output
Metasploit Spring4Shell verification attempt (used to confirm the false positive)

Note on redaction: Screenshots and the SQL backup containing real patient and staff personal data (including national ID numbers) have been redacted throughout this report and its evidence, same as how this data would be handled in a real engagement.

Key Takeaway

The most useful lesson this week wasn't the breach itself — it was learning not to trust an automated scanner's severity rating at face value. My scanner flagged Spring4Shell as a CVSS 8.0 finding, but manual verification (checking the actual tech stack, then testing the exploit directly) showed it was a false positive. Meanwhile, a much quieter finding from the same scan — a disallowed path in robots.txt — ended up being the actual thread that led to the real breach. Verifying findings manually instead of taking scan output at face value made all the difference.

Conducted as part of the NetworkWalks internship program. All testing was performed against an authorized training target only.
