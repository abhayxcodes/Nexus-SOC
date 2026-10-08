# Nexus-SOC

### Security Operations Center Simulator !

Nexus-SOC is a web-based Security Operations Center (SOC) simulator built with **Python and Flask**. It provides a practical environment for collecting security events, analyzing logs, detecting suspicious activity, tracking Indicators of Compromise (IOCs), generating alerts, and managing security incidents through a SOC-style workflow.

The project is designed as a defensive cybersecurity and SOC learning platform that demonstrates how different security monitoring and incident-handling components can work together.

---

## 🚀 Features

* 🔐 User registration and authentication
* 📥 Security event ingestion
* 🔎 Log analysis and normalization
* 🚨 Rule-based threat detection
* ⚠️ Alert generation and severity classification
* 🎯 IOC extraction and tracking
* 🔗 Event-to-IOC correlation
* 🎫 Security ticket management
* 🛡️ Threat intelligence matching
* 🗺️ MITRE ATT&CK technique mapping
* 📊 SOC monitoring dashboard
* ⚔️ Security event / attack simulator
* 📄 Security ticket PDF generation
* 🔔 Alert notification support
* 🔒 CSRF protection
* 🚦 Rate limiting
* 👤 User-specific data isolation
* 🧪 Automated testing

---

## 🏗️ SOC Workflow

```text
                    Security Event
                          │
                          ▼
                  ┌───────────────┐
                  │ Log Ingestion │
                  └───────┬───────┘
                          │
                          ▼
                ┌───────────────────┐
                │ Log Analysis &    │
                │ Normalization     │
                └─────────┬─────────┘
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
      ┌──────────────┐       ┌─────────────────┐
      │ IOC          │       │ Detection       │
      │ Extraction   │       │ Engine          │
      └──────┬───────┘       └────────┬────────┘
             │                        │
             ▼                        ▼
      ┌──────────────┐       ┌─────────────────┐
      │ IOC Tracking │       │ Threat          │
      │ & Correlation│       │ Intelligence    │
      └──────┬───────┘       └────────┬────────┘
             │                        │
             └───────────┬────────────┘
                         ▼
                 ┌───────────────┐
                 │ Alert         │
                 │ Generation    │
                 └───────┬───────┘
                         │
                         ▼
                 ┌───────────────┐
                 │ SOC Ticket    │
                 │ Management    │
                 └───────┬───────┘
                         │
                         ▼
                 ┌───────────────┐
                 │ SOC Dashboard │
                 └───────────────┘
```

---

## 🧰 Technology Stack

| Technology              | Purpose                   |
| ----------------------- | ------------------------- |
| Python                  | Backend development       |
| Flask                   | Web framework             |
| SQLite                  | Database                  |
| Flask-WTF               | CSRF protection           |
| Flask-Limiter           | Rate limiting             |
| python-dotenv           | Environment configuration |
| ReportLab               | PDF report generation     |
| Pytest                  | Automated testing         |
| HTML / CSS / JavaScript | Frontend                  |

---

## 🗄️ Database

Nexus-SOC uses **SQLite** for persistent application data.

The database is automatically initialized when the application starts.

### Main Tables

```text
users
events
alerts
iocs
ioc_events
tickets
auth_failures
```

### Database Flow

```text
User
 │
 ▼
Security Event
 │
 ├──► Event Database
 │
 ├──► IOC Extraction ──► IOC Database
 │
 └──► Detection Engine
              │
              ▼
            Alert
              │
              ▼
            Ticket
```

---

## 🔍 Detection Capabilities

Nexus-SOC provides detection rules for several types of suspicious activity, including:

* Failed login attempts
* Brute-force activity
* Network port scanning
* Malware-related events
* Unauthorized access
* Exploit activity
* Phishing-related activity
* Suspicious login behavior

Detected events can be assigned severity levels:

```text
LOW
MEDIUM
HIGH
CRITICAL
```

---

## 🎯 IOC Tracking

The IOC tracking component can identify and maintain security indicators such as:

```text
IP Addresses
Domains
URLs
Email Addresses
MD5 Hashes
SHA1 Hashes
SHA256 Hashes
```

IOCs can be correlated with the security events in which they appear, allowing analysts to investigate repeated or related activity.

---

## 🎫 SOC Ticket Management

Detected alerts can be converted into security tickets for investigation and tracking.

Example workflow:

```text
Alert Detected
      │
      ▼
Ticket Created
      │
      ▼
Open
      │
      ▼
In Progress
      │
      ▼
Resolved
      │
      ▼
Closed
```

This demonstrates a simplified incident-management workflow commonly used in SOC environments.

---

## 📊 Dashboard

The dashboard provides a centralized view of security activity, including:

* Security events
* Alerts
* Severity levels
* IOC information
* Ticket status
* Detection activity
* Security statistics

---

## ⚔️ Security Event Simulator

Nexus-SOC includes a simulator for generating security-related events in a controlled environment.

This can be used to demonstrate detection scenarios such as:

```text
Failed Login
Brute Force
Port Scan
Suspicious Login
Malware Activity
Exploit Activity
Phishing Activity
```

The generated events pass through the same analysis and detection workflow used by the application.

---

## 📁 Project Structure

```text
Nexus-SOC/
│
├── app/
│   ├── __init__.py
│   ├── auth.py
│   ├── db.py
│   ├── detection.py
│   ├── ioc_tracker.py
│   ├── log_analyzer.py
│   ├── routes.py
│   ├── threat_intel.py
│   └── ticketing.py
│
├── data/
│   └── threat_intel.json
│
├── templates/
│   ├── dashboard.html
│   ├── input.html
│   ├── login.html
│   └── register.html
│
├── tests/
│   ├── test_detection.py
│   ├── test_iocs_tracker.py
│   └── test_log_analyzer.py
│
├── .env.example
├── .gitignore
├── requirements.txt
├── run.py
└── Readme.md
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
cd Nexus-SOC
```

### 2. Create a virtual environment

Windows:

```powershell
python -m venv venv
```

Activate it:

```powershell
venv\Scripts\activate
```

### 3. Install dependencies

```powershell
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file using `.env.example` as a reference.

Example:

```env
SECRET_KEY=replace-with-a-strong-secret-key
FLASK_DEBUG=false
FLASK_HOST=127.0.0.1
FLASK_PORT=5000
```

**Never commit your real `.env` file to GitHub.**

### 5. Run the application

```powershell
python run.py
```

Open:

```text
http://127.0.0.1:5000
```

The SQLite database is initialized automatically.

---

## 🧪 Testing

Run the test suite:

```powershell
pytest
```

---

## 🔐 Security Notes

Nexus-SOC is intended for:

* Educational purposes
* Cybersecurity learning
* SOC workflow demonstrations
* Defensive security experimentation
* Portfolio demonstration

Before deploying the application publicly:

* Use a strong `SECRET_KEY`
* Keep `.env` outside version control
* Disable Flask debug mode
* Use HTTPS
* Review authentication settings
* Protect notification credentials
* Use a production-grade deployment configuration
* Never use real credentials or sensitive production logs for testing

---

## 🎯 Project Objectives

Nexus-SOC demonstrates practical concepts related to:

* Security Operations Center workflows
* Security event monitoring
* Log analysis
* Threat detection
* IOC management
* Incident response
* Threat intelligence
* Alert management
* Security automation
* Flask web application development
* Database-backed security applications

---

## 👨‍💻 Author

**Abhay Soni**

B.Tech CSE student focused on defensive cybersecurity, SOC operations, security monitoring, threat detection, and security automation.

---

## 📌 Disclaimer

Nexus-SOC is intended for educational and defensive security purposes. Security simulations should be performed only in controlled environments and on systems for which you have authorization.
