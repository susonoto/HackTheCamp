# Cybersecurity Starter Lab 🛡️

A beginner-friendly roadmap and workspace for learning cybersecurity, with an initial focus on **networking, Linux, web application security, API testing, and penetration-testing fundamentals**.

This repository organizes learning resources, tools, lab notes, and small projects so that progress is repeatable and easy to review.

> **Safety first:** Only test systems you own or have explicit permission to assess. Use the designated targets and scope provided by training platforms. Keep intentionally vulnerable applications isolated and never expose them to the public internet.

---

## Table of Contents

- [Goals](#goals)
- [Learning Roadmap](#learning-roadmap)
- [Core Tools](#core-tools)
- [Learning Platforms](#learning-platforms)
- [Environment Setup](#environment-setup)
- [Burp Suite Setup](#burp-suite-setup)
- [Postman API Practice](#postman-api-practice)
- [Local Practice Labs](#local-practice-labs)
- [Suggested Repository Structure](#suggested-repository-structure)
- [12-Week Learning Plan](#12-week-learning-plan)
- [Daily Study Routine](#daily-study-routine)
- [Lab Notes Template](#lab-notes-template)
- [Portfolio Projects](#portfolio-projects)
- [Safety and Ethics](#safety-and-ethics)
- [Progress Checklist](#progress-checklist)
- [Official Resources](#official-resources)

---

## Goals

By working through this repository, you will aim to:

- Understand networking, DNS, TCP/IP, HTTP, and HTTPS.
- Become comfortable with Linux command-line basics.
- Inspect web requests and responses using browser developer tools and Burp Suite.
- Use Postman to send requests and organize API tests.
- Learn common web vulnerabilities and their mitigations.
- Practice in authorized, intentionally vulnerable labs.
- Build a portfolio of notes, small projects, and responsible security reports.

**Recommended approach:** Learn one concept, practice it in a safe lab, document what happened, and explain how the issue could be prevented.

## Learning Roadmap

1. **Fundamentals:** Linux, networking, DNS, ports, HTTP, and HTTPS.
2. **Web basics:** HTML and JavaScript fundamentals, cookies, sessions, requests, and responses.
3. **Tooling:** Firefox Developer Tools, Burp Suite, Postman, curl, and Wireshark.
4. **Web security:** SQL injection, cross-site scripting (XSS), authentication, access control, path traversal, and SSRF.
5. **API security:** REST, JSON, authentication, authorization, and Broken Object Level Authorization (BOLA).
6. **Penetration-testing workflow:** Scope, enumeration, validation, evidence, reporting, and remediation.
7. **Portfolio:** Publish original projects and permitted lab write-ups without secrets or sensitive data.

---

## Core Tools

Install only what you need at first. Add more tools when a learning objective calls for them.

| Tool | Purpose | Official link |
|---|---|---|
| Firefox | Browser for web testing | https://www.mozilla.org/firefox/new/ |
| Burp Suite Community Edition | Inspect, intercept, and replay HTTP requests in authorized labs | https://portswigger.net/burp/communitydownload |
| Postman | Build and test HTTP/API requests | https://www.postman.com/downloads/ |
| Python 3 | Scripting and automation | https://www.python.org/downloads/ |
| Git | Version control | https://git-scm.com/downloads |
| VS Code | Code and notes editor | https://code.visualstudio.com/ |
| curl | Make HTTP requests from the command line | https://curl.se/ |
| Nmap | Discover services on authorized targets | https://nmap.org/download.html |
| Wireshark | Inspect network traffic | https://www.wireshark.org/download.html |
| jq | Format and process JSON | https://jqlang.org/ |
| Docker | Run isolated local practice services | https://www.docker.com/get-started/ |

### Optional operating-system choices

- **Ubuntu or another Linux distribution:** A convenient everyday development environment.
- **Kali Linux in a virtual machine:** A dedicated security-testing environment.
- **Windows with WSL2:** A way to use Linux tools alongside Windows.
- **macOS:** Can run many of the same web and development tools.

Official links:
- Ubuntu: https://ubuntu.com/download/desktop
- Kali Linux: https://www.kali.org/get-kali/
- WSL installation: https://learn.microsoft.com/en-us/windows/wsl/install

You do **not** need Kali Linux to use Burp Suite, Postman, or PortSwigger Academy.

---

## Learning Platforms

| Platform | Best use | Link |
|---|---|---|
| TryHackMe (THM) | Guided cybersecurity fundamentals and hands-on rooms | https://tryhackme.com/ |
| Hack The Box Academy (HTB Academy) | Structured technical training | https://academy.hackthebox.com/ |
| Hack The Box Labs | Practice with vulnerable machines | https://www.hackthebox.com/ |
| PortSwigger Web Security Academy | Web application security lessons and interactive labs | https://portswigger.net/web-security |
| OverTheWire Bandit | Linux command-line practice | https://overthewire.org/wargames/bandit/ |
| OWASP | Security projects, guidance, and references | https://owasp.org/ |
| OWASP API Security | API security guidance | https://owasp.org/www-project-api-security/ |

**Suggested order:** TryHackMe and Bandit for foundations; start PortSwigger early for web security; add HTB Academy for structured training; then use HTB Labs when you're comfortable with Linux, networking, and enumeration.

Platform content and subscription features can change. Check each official site for current paths and availability.

---

## Environment Setup

### 1. Create the workspace

Create a folder named `cybersecurity-lab`. You can create it in your file manager or use:

```bash
mkdir -p cybersecurity-lab
cd cybersecurity-lab
```

Use the repository structure shown below as your notes and project library.

### 2. Check installed tools

Run the commands relevant to your operating system:

```bash
python3 --version
git --version
curl --version
```

If a command is missing, install it using the official instructions for your OS.

### 3. Learn basic Linux commands

Practice these in your own environment or a training VM:

```bash
pwd
ls -la
cd
cat
less
grep
find
chmod
whoami
id
ip addr
ss -tuln
```

Understand what each command does before using it on unfamiliar systems.

### 4. Make a first HTTP request

```bash
curl -i https://example.com
```

This displays the HTTP response headers and body. Use authorized destinations when experimenting with security-testing techniques.

### 5. Practice basic service discovery safely

For a simple local check:

```bash
nmap -sV 127.0.0.1
```

This checks the local machine for accessible TCP services and attempts service-version detection. Scan only systems you own or are explicitly authorized to test.

---

## Burp Suite Setup

Official download and documentation:

- Download: https://portswigger.net/burp/communitydownload
- Documentation: https://portswigger.net/burp/documentation

### First-session workflow

1. Install and launch Burp Suite Community Edition.
2. Open Burp's built-in browser.
3. Visit a designated practice lab or application you own.
4. Open **Proxy → HTTP history**.
5. Select a request and inspect its method, path, headers, cookies, and body.
6. Send a request to **Repeater**.
7. Change a harmless parameter and resend it.
8. Compare the responses and document what changed.

### Features to learn

- **Proxy / HTTP history:** View browser requests and responses.
- **Repeater:** Modify and resend requests manually.
- **Decoder:** Encode and decode common data formats.
- **Comparer:** Compare requests or responses.
- **Intruder:** Learn controlled request manipulation and the Community Edition's limitations.

### HTTPS certificates

Burp's built-in browser is the simplest starting point. If configuring an external browser, follow PortSwigger's official guidance:

https://portswigger.net/burp/documentation/desktop/external-browser-config

Only configure interception for your own applications and authorized labs. Avoid installing a testing certificate authority system-wide unless you understand the implications.

---

## Postman API Practice

Official download and learning resources:

- Download: https://www.postman.com/downloads/
- Echo API documentation: https://learning.postman.com/docs/developer/echo-api/

### Create your first collection

Name it **Cybersecurity - HTTP Fundamentals**.

Add requests that demonstrate:

- GET requests and query parameters
- POST requests with JSON bodies
- Custom request headers
- Status codes and response headers
- Environment variables
- Basic response validation

### Example JSON POST request

**Method:** `POST`  
**URL:** `https://postman-echo.com/post`  
**Body:** select **raw → JSON**

```json
{
  "username": "testuser",
  "role": "learner",
  "topic": "api-security"
}
```

Send the request and inspect the status code and JSON response. This is a basic request/response exercise, not a vulnerability test.

### Topics to learn next

1. HTTP methods and status codes
2. Headers, cookies, and sessions
3. JSON and request bodies
4. Authentication versus authorization
5. REST API conventions
6. Object-level authorization
7. Input validation and error handling
8. Rate limiting and safe test design

---

## Local Practice Labs

Start with online labs. Add a local vulnerable application only when you're ready to manage an isolated environment.

| Application | Purpose | Official link |
|---|---|---|
| OWASP Juice Shop | Broad web security practice | https://owasp.org/www-project-juice-shop/ |
| DVWA | Common web vulnerabilities in a deliberately vulnerable app | https://github.com/digininja/DVWA |
| OWASP WebGoat | Guided web security lessons | https://owasp.org/www-project-webgoat/ |

### Optional: Run OWASP Juice Shop locally with Docker

Install Docker first, then run:

```bash
docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

Open `http://127.0.0.1:3000` in your browser.

The port is bound to the local loopback interface, rather than all network interfaces. Keep the lab isolated and do not expose it through a public IP, reverse proxy, or other network configuration. Stop the container with `Ctrl+C` in the terminal where it is running.

---

## Suggested Repository Structure

```text
cybersecurity-lab/
├── README.md
├── 01-fundamentals/
│   ├── networking.md
│   ├── linux.md
│   ├── windows.md
│   └── http-basics.md
├── 02-web-security/
│   ├── xss.md
│   ├── sql-injection.md
│   ├── authentication.md
│   ├── access-control.md
│   └── ssrf.md
├── 03-api-security/
│   ├── api-fundamentals.md
│   ├── authentication.md
│   ├── authorization.md
│   └── testing-notes.md
├── 04-tools/
│   ├── burp-suite.md
│   ├── postman.md
│   ├── nmap.md
│   └── wireshark.md
├── 05-labs/
│   ├── tryhackme/
│   ├── hackthebox/
│   └── portswigger/
├── 06-projects/
│   ├── http-inspector/
│   └── api-test-suite/
└── 07-reports/
    └── report-template.md
```

---

## 12-Week Learning Plan

This is a flexible starting plan, not a deadline for becoming job-ready. Aim for roughly 1–2 hours per day, five or six days per week, and adjust the pace to your needs.

| Week | Focus | Practice and outcome |
|---|---|---|
| 1 | Linux and networking basics | Bandit; learn files, permissions, IPs, and DNS |
| 2 | TCP/UDP, ports, HTTP/HTTPS, Windows basics | TryHackMe, Wireshark, and curl |
| 3 | HTML/JavaScript basics and HTTP | Firefox Developer Tools and Postman |
| 4 | Proxying and request analysis | Burp Suite and beginner PortSwigger labs |
| 5 | SQL injection and XSS concepts | PortSwigger labs; learn prevention |
| 6 | Authentication, sessions, and access control | PortSwigger labs and clear notes |
| 7 | Path traversal, file uploads, SSRF, misconfiguration | Authorized guided labs |
| 8 | REST, JSON, API authentication and authorization | Build a Postman collection |
| 9 | API security and BOLA | OWASP API Security guidance and authorized labs |
| 10 | Scope, enumeration, and service discovery | HTB Academy and Starting Point |
| 11 | Methodical lab practice and reporting | Complete a guided lab without relying entirely on a walkthrough |
| 12 | Portfolio and review | Finish a small script, API collection, and report |

### Suggested weekly routine

- **20 minutes:** Read or watch a lesson.
- **40 minutes:** Follow a guided exercise.
- **40 minutes:** Practice in an authorized lab.
- **15 minutes:** Write notes and record evidence.
- **5 minutes:** Plan the next session.

---

## Lab Notes Template

Create a Markdown file for each lab and fill in this template:

```markdown
# Lab Name

## Platform
TryHackMe / HTB / PortSwigger / Local lab

## Topic
Example: Access control

## Learning objectives
- Objective 1
- Objective 2

## Scope and environment
Describe the authorized training target.

## Method
Summarize the steps you performed.

## Observations
Record relevant requests, responses, status codes, and behavior.
Do not store real passwords, tokens, or session cookies.

## Finding / root cause
Explain the issue, if one was demonstrated.

## Impact
Explain what could happen and under what conditions.

## Remediation
Describe how a developer or administrator could fix it.

## What I learned
Summarize the key lessons.

## References
- Official documentation or learning resources
```

Follow each platform's rules about publishing solutions and walkthroughs. Never include sensitive information in public notes.

---

## Portfolio Projects

Build these after learning the relevant fundamentals.

### Project 1: HTTP Inspector

Write a Python program that accepts a URL and reports:

- HTTP status code
- Selected response headers
- Response time
- Final URL after redirects

Include input validation, error handling, a README, and safe usage guidance.

### Project 2: API Test Collection

Create a Postman collection that:

- Uses a public test API or your own local API
- Checks expected status codes
- Validates JSON fields
- Documents test cases and results
- Avoids hard-coded secrets

### Project 3: Web Security Assessment Report

Use an authorized training lab and document:

- Executive summary
- Scope and environment
- Finding and severity rationale
- Reproduction steps
- Evidence
- Impact
- Remediation

Only publish write-ups when the platform's rules allow it.

---

## Safety and Ethics

- Test only systems you own or have explicit authorization to assess.
- Follow the stated scope and rules of each lab or program.
- Keep intentionally vulnerable services isolated.
- Do not run automated scans against public systems without permission.
- Never commit passwords, API tokens, private keys, `.env` files, or session credentials.
- Distinguish suspected issues from validated findings.
- Document evidence responsibly and recommend mitigations.
- Follow coordinated disclosure requirements when applicable.

Cybersecurity skills include responsible judgment, clear documentation, and remediation—not just exploitation.

---

## Progress Checklist

### Fundamentals
- [ ] I can navigate directories and inspect files in Linux.
- [ ] I understand IP addresses, DNS, ports, and TCP versus UDP.
- [ ] I can explain a basic HTTP request and response.
- [ ] I understand the purpose of HTTPS.

### Tools
- [ ] I can inspect traffic in Firefox Developer Tools.
- [ ] I can locate requests in Burp Suite HTTP history.
- [ ] I can resend and compare requests in Repeater.
- [ ] I can build a basic Postman collection.
- [ ] I can make a simple request with curl.
- [ ] I understand what Nmap and Wireshark are used for.

### Web and API security
- [ ] I can explain SQL injection and XSS at a conceptual level.
- [ ] I understand authentication versus authorization.
- [ ] I can explain sessions and cookies.
- [ ] I understand the idea behind BOLA.
- [ ] I can describe mitigations for common web vulnerabilities.

### Practice and portfolio
- [ ] I have completed beginner labs on at least one platform.
- [ ] I write notes after each lab.
- [ ] I have created a small Python or API testing project.
- [ ] I have written a clear report for an authorized lab.
- [ ] I have checked my repository for secrets before publishing it.

---

## Official Resources

- TryHackMe: https://tryhackme.com/
- HTB Academy: https://academy.hackthebox.com/
- HTB Labs: https://www.hackthebox.com/
- PortSwigger Web Security Academy: https://portswigger.net/web-security
- Burp Suite documentation: https://portswigger.net/burp/documentation
- Postman learning center: https://learning.postman.com/
- OverTheWire Bandit: https://overthewire.org/wargames/bandit/
- OWASP: https://owasp.org/
- OWASP API Security: https://owasp.org/www-project-api-security/
- Nmap: https://nmap.org/
- Wireshark: https://www.wireshark.org/
- Python: https://www.python.org/
- Git: https://git-scm.com/

---

## License and Disclaimer

This repository is intended for education and authorized security testing. You are responsible for following applicable laws, platform rules, and the scope of any assessment. Nothing in this repository grants permission to test third-party systems.
