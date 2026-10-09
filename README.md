# Simple Python Intrusion Detection System (IDS)

**Author:** Nikolas Ordonez  
**Project Type:** Python Security Automation  
**Purpose:** Educational cybersecurity project

## 1. Project Overview

This project is a Python-based Intrusion Detection System (IDS) designed to analyze authentication log files and detect repeated failed login attempts from the same source IP address. The program reviews log entries, identifies failed password events, and tracks how often each IP address attempts to authenticate within a defined time window.

The goal is to demonstrate how a simple Python script can automate basic security monitoring. This project is intentionally lightweight and educational, making it useful for learning about log analysis, regular expressions, data collection, and threshold-based detection logic.

## 2. Project Objectives

The objectives of this project are to:

- Develop a beginner-friendly intrusion detection system using Python.
- Analyze authentication log files for failed login attempts.
- Extract source IP addresses associated with suspicious activity.
- Track repeated failed login attempts over time.
- Detect patterns that exceed a configured threshold.
- Generate an alert when suspicious behavior is identified.
- Demonstrate practical cybersecurity concepts with a simple implementation.
- Apply Python programming fundamentals to a real-world security monitoring scenario.

## 3. Key Features

### Authentication Log Analysis
The program reads a log file line by line and searches for entries that indicate failed login attempts.

### IP Address Extraction
A regular expression identifies failed login entries and extracts the source IP address associated with each event.

### Failed Login Tracking
The system stores failed login timestamps for each IP address using Python's `defaultdict` collection, making it easy to track retry patterns.

### Time-Based Detection
The IDS removes older attempts outside the configured time window so the detection logic focuses on recent activity.

### Threshold-Based Alerts
An alert is raised when an IP address exceeds a defined number of failed login attempts within a set time period.

### Simulated Real-Time Processing
The script introduces a short delay between log entries to simulate real-time monitoring for demonstration purposes. It reads from an existing log file rather than continuously following new events.

## 4. Technologies and Dependencies

This project uses:

- **Python 3:** The primary programming language used to build the IDS.
- **`time`:** Used to track timestamps and delay processing between log entries.
- **`re`:** Used to search log entries and extract relevant information.
- **`collections.defaultdict`:** Used to store failed login attempts by source IP address.

All required dependencies are part of Python's standard library, so no third-party packages are necessary.

## 5. Prerequisites

Before running the program, ensure that you have:

- Python 3 installed on your system.
- A Python source file named `ids.py`.
- An authentication log file named `Auth.Log`.
- Log entries formatted consistently with the pattern expected by the script.

The Python file and log file should be located in the same directory.

## 6. Installation and Setup

### Step 1: Install Python

Download and install Python 3 from the official Python website:

https://www.python.org/downloads/

Verify the installation by opening a terminal or command prompt and running:

```bash
python --version
```

If your system uses `python3` instead of `python`, run:

```bash
python3 --version
```

### Step 2: Download the Project

Clone the repository from GitHub using Git:

```bash
git clone https://github.com/YOUR-USERNAME/simple-python-ids.git
```

Replace `YOUR-USERNAME` with the appropriate repository owner or username.

Then navigate to the project directory:

```bash
cd simple-python-ids
```

### Step 3: Prepare the Log File

Create a file named `Auth.Log` in the same directory as `ids.py`.

For testing, you may use fictional log entries like the following:

```text
Failed password for guest from 192.168.1.25
Failed password for guest from 192.168.1.25
Failed password for guest from 192.168.1.25
```

These entries demonstrate how the IDS identifies repeated failed login attempts from the same source IP address.

Use only authorized or fictional data when testing the program.

## 7. How to Run the Program

Open a terminal in the project directory and run:

```bash
python ids.py
```

If your environment requires `python3`, use:

```bash
python3 ids.py
```

The program will display a startup message and begin processing the log file.

Example startup output:

```text
[*] simulated IDS monitoring Auth.Log for failed login attempts.
```

When an IP address reaches the configured threshold, the script generates an alert similar to:

```text
ALERT: 192.168.1.25 has exceeded the failed login threshold.
```

The actual output depends on the contents of the log file and the timing of the entries.

## 8. How the IDS Works

The program follows these steps:

1. **Initialize configuration:** Set the log filename, detection pattern, threshold, and time window.
2. **Read the log file:** Process each line in the authentication log.
3. **Search for failed logins:** Use a regular expression to identify matching authentication events.
4. **Extract the source IP:** Retrieve the IP address from each relevant log entry.
5. **Record timestamps:** Store the time of each failed login attempt.
6. **Filter old attempts:** Remove attempts that fall outside the configured time window.
7. **Check the threshold:** Determine whether the IP address has reached the alert threshold.
8. **Generate an alert:** Print a warning when suspicious activity is detected.
9. **Reset the counter:** Clear the recorded attempts for that IP address after triggering an alert.

This sequence demonstrates the core mechanics of simple event-based intrusion detection and automated alerting.

## 9. Configuration Options

The script uses several variables to control its behavior:

| Variable | Purpose | Default Value |
| --- | --- | --- |
| `LOG_FILE` | Specifies the authentication log filename | `Auth.Log` |
| `FAIL_REGEX` | Matches failed password attempts and extracts username/IP data | Regular expression |
| `THRESHOLD` | Number of failed attempts required to trigger an alert | `3` |
| `TIME_WINDOW` | Time range used to evaluate repeated attempts, in seconds | `60` |
| `FAILED_ATTEMPTS` | Stores timestamps for each source IP address | Empty dictionary |

Changing the threshold or time window allows you to adjust how sensitive the IDS is to repeated login failures.

## 10. Code Documentation and Standards

The Python source code includes comments explaining key configuration settings and detection logic. The functions are organized to separate responsibilities such as reading the log file, checking log entries, and handling failed login detection.

The project uses descriptive names for variables and functions to improve readability and maintainability. Consistent indentation and standard Python naming conventions help make the code easier to understand and modify.

## 11. Security Automation

This project demonstrates how security automation can reduce the manual effort involved in reviewing authentication logs. Instead of scanning logs by hand, the script can quickly identify repeated failed login attempts and highlight suspicious patterns.

Automated log analysis can help security analysts identify possible attacks or misconfiguration issues faster. Although this project implements only basic detection, the same concepts can be extended to larger systems, centralized logging, and security event monitoring.

Possible future enhancements include automatic log collection, event correlation, centralized logging, and integration with Security Information and Event Management (SIEM) systems.

## 12. Limitations

This project is a basic educational IDS and has several limitations:

- It processes an existing log file rather than continuously monitoring new entries.
- It depends on log format consistency and the configured regular expression.
- It uses a simple threshold-based detection method.
- It may generate false positives when legitimate users enter incorrect passwords repeatedly.
- It does not verify whether a login attempt eventually succeeded.
- It does not block IP addresses or automatically respond to suspicious activity.
- It does not provide advanced analytics, centralized alert handling, or long-term logging.

An alert indicates potentially suspicious activity, not definitive proof of an attack.

## 13. Future Improvements

Possible improvements include:

- Continuously monitoring newly added log entries.
- Saving alerts to a separate security log.
- Adding timestamps to alert messages for more detailed investigation.
- Supporting multiple authentication log formats.
- Detecting additional suspicious login patterns.
- Generating summary reports.
- Sending notifications by email or messaging platforms.
- Integrating with SIEM platforms.
- Adding command-line configuration options.

## 14. Ethical and Legal Considerations

This tool should only be used on systems and authentication logs that you own or have explicit permission to monitor.

Do not upload real authentication logs containing sensitive information to a public GitHub repository. Use fictional, sanitized, or clearly authorized test data for demonstrations and learning.

Respect privacy laws, organizational policies, and applicable security regulations when working with logs or monitoring systems.

## 15. Conclusion

The Simple Python Intrusion Detection System demonstrates how Python can be used to analyze authentication logs, track failed login attempts, and generate automated security alerts.

The project provides practical experience with regular expressions, dictionaries, timestamps, file handling, and basic intrusion detection logic. It serves as an introductory example of how programming can support cybersecurity monitoring and alerting in a lightweight, approachable way.

## Author

Nikolas Ordonez

Educational cybersecurity and Python security automation project for CYB333.
