# Simple Python Intrusion Detection System (IDS)

**Author:** Nikolas Ordonez
**Project Type:** Python Security Automation
**Purpose:** Educational cybersecurity project

## 1. Project Overview

This project is a Python-based Intrusion Detection System (IDS) that analyzes authentication log files to identify repeated failed login attempts. The program tracks failed login attempts by source IP address and generates a security alert when an IP address reaches a specified threshold within a defined time window.

The project demonstrates how Python can automate basic security monitoring tasks and help identify potentially suspicious login activity. It is designed for educational purposes and provides a foundation for understanding log analysis, intrusion detection, and security automation.

## 2. Project Objectives

The objectives of this project are to:

- Develop a basic intrusion detection system using Python.
- Analyze authentication logs for failed login attempts.
- Identify and track IP addresses associated with failed logins.
- Detect repeated failed login attempts within a specific time window.
- Generate alerts when suspicious activity reaches a defined threshold.
- Demonstrate how Python can automate basic cybersecurity monitoring.
- Apply Python programming concepts to a practical security scenario.

## 3. Key Features

### Authentication Log Analysis

The program reads an authentication log file line by line and searches for entries containing failed password attempts.

### IP Address Extraction

A regular expression identifies failed login entries and extracts the source IP address associated with each attempt.

### Failed Login Tracking

The program maintains a record of failed login timestamps for each source IP address using Python's `defaultdict` collection.

### Time-Based Detection

The IDS removes attempts that fall outside the configured time window. This helps the program focus on recent activity rather than older failed logins.

### Threshold-Based Alerts

The program generates an alert when an IP address reaches three failed login attempts within 60 seconds.

### Simulated Real-Time Processing

A short delay between log entries simulates real-time processing for demonstration purposes. The program processes an existing log file rather than continuously following new log entries.

## 4. Technologies and Dependencies

This project uses:

- **Python 3:** Programming language used to develop the IDS.
- **`time`:** Retrieves timestamps and adds delays between log entries.
- **`re`:** Searches authentication log entries using regular expressions.
- **`collections.defaultdict`:** Stores failed login timestamps for each IP address.

All dependencies are included in Python's standard library. No third-party packages are required.

## 5. Prerequisites

Before running the program, ensure that you have:

- Python 3 installed on your computer.
- The Python source file named `ids.py`.
- An authentication log file named `Auth.Log`.
- Log entries formatted to match the regular expression used in the program.

The Python file and log file should be located in the same directory.

## 6. Installation and Setup

### Step 1: Install Python

Download and install Python 3 from the official website:

[https://www.python.org/downloads/](https://www.python.org/downloads/)

Verify the installation by opening a terminal or command prompt and running:

```bash
python --version
```

If your system uses a different command, try:

```bash
python3 --version
```

### Step 2: Download the Project

Download the repository from GitHub using the Code menu, or clone it with Git:

```bash
git clone https://github.com/YOUR-USERNAME/simple-python-ids.git
```

Replace `YOUR-USERNAME` with the GitHub username associated with the repository.

Navigate to the project directory:

```bash
cd simple-python-ids
```

### Step 3: Prepare the Log File

Create a file named `Auth.Log` in the same directory as `ids.py`.

For testing, you can use fictional log entries such as:

```text
Failed password for guest from 192.168.1.25
Failed password for guestfrom 192.168.1.25
Failed password for guest from 192.168.1.25
```

These entries demonstrate how the IDS identifies repeated failed login attempts from the same IP address.

Use only authorized logs or fictional test data.

## 7. How to Run the Program

Open a terminal in the project directory and execute:

```bash
python ids.py
```

Alternatively, on systems that use `python3`:

```bash
python3 ids.py
```

The program will display a startup message and begin processing the log file.

Example startup output:

```text
[*] simulated IDS monitoring Auth.Log for failed login attempts.
```

When an IP address reaches the configured threshold, the program generates an alert similar to:

```text
ALERT: 192.168.1.25 has exceeded the failed login threshold.
```

The actual output depends on the contents of the log file and the timing of the entries.

## 8. How the IDS Works

The program follows these steps:

1. **Initialize configuration:** Set the log filename, detection pattern, failed-login threshold, and time window.
2. **Read the log file:** Process each log entry individually.
3. **Search for failed logins:** Use a regular expression to identify matching authentication events.
4. **Extract the source IP:** Retrieve the IP address from each matching entry.
5. **Record timestamps:** Store the time associated with each failed login attempt.
6. **Filter old attempts:** Remove attempts outside the configured 60-second window.
7. **Check the threshold:** Determine whether the IP address has reached three failed attempts.
8. **Generate an alert:** Print a warning if the threshold is reached.
9. **Reset the counter:** Clear the recorded attempts for that IP address after an alert.

This process demonstrates basic event detection and automated alert generation.

## 9. Configuration Options

The program uses the following variables to control its behavior:

| Variable          | Purpose                                                                     | Default Value      |
| ----------------- | --------------------------------------------------------------------------- | ------------------ |
| `LOG_FILE`        | Specifies the authentication log filename                                   | `Auth.Log`         |
| `FAIL_REGEX`      | Identifies failed password entries and extracts the username and IP address | Regular expression |
| `THRESHOLD`       | Number of attempts needed to trigger an alert                               | `3`                |
| `TIME_WINDOW`     | Time window used to count failed attempts, in seconds                       | `60`               |
| `FAILED_ATTEMPTS` | Stores timestamps for each source IP address                                | Empty dictionary   |

Changing `THRESHOLD` or `TIME_WINDOW` allows the detection criteria to be adjusted.

## 10. Code Documentation and Standards

The Python source code uses comments to explain key configuration settings and important detection logic. The functions separate responsibilities such as reading the log file, checking log entries, and generating alerts.

The project uses meaningful variable and function names to improve readability and maintainability. Consistent indentation and Python naming conventions make the code easier to understand and modify.

## 11. Security Automation

This project demonstrates security automation by reducing the need to manually inspect authentication logs for repeated failed login attempts.

Automated log analysis can help security analysts identify suspicious patterns more efficiently. Although this project implements only basic detection, the same principles can be applied to larger security monitoring systems.

Potential future enhancements include automatic log collection, event correlation, centralized logging, and integration with Security Information and Event Management (SIEM) systems.

## 12. Limitations

This project is a basic educational IDS and has several limitations:

- It processes an existing log file rather than continuously monitoring new entries.
- It depends on log entries matching the configured regular expression.
- It uses a simple threshold-based detection method.
- It may generate false positives when legitimate users repeatedly enter incorrect passwords.
- It does not determine whether a login attempt was successful.
- It does not block IP addresses or automatically respond to suspected attacks.
- It does not provide advanced analytics or centralized logging.

An alert indicates potentially suspicious activity, not definitive proof of an attack.

## 13. Future Improvements

Possible improvements include:

- Continuously monitoring newly added log entries.
- Saving alerts to a separate security log.
- Adding date and time information to alert messages.
- Supporting additional authentication log formats.
- Detecting other suspicious authentication patterns.
- Generating summary reports.
- Sending email notifications.
- Integrating with SIEM platforms.
- Adding configurable command-line options.

## 14. Ethical and Legal Considerations

This tool should only be used on systems and authentication logs that you own or have explicit permission to monitor.

Do not upload real authentication logs containing sensitive information to a public GitHub repository. Use fictional or sanitized log entries for demonstrations and testing.

## 15. Conclusion

The Simple Python Intrusion Detection System demonstrates how Python can be used to analyze authentication logs, track failed login attempts, and generate automated security alerts.

The project provides practical experience with regular expressions, dictionaries, timestamps, file handling, and basic intrusion detection logic. It serves as an introductory example of how programming can support cybersecurity monitoring and incident detection.

## Author

Nikolas Ordonez

Educational cybersecurity and Python security automation project for CYB333
