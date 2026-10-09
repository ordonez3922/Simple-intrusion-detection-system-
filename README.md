# Simple IDS CYB333 Project

**Author:** Nikolas Ordonez  
**GitHub Username:** ordonez3922  
**Project Type:** Python Security Automation  
**Course:** CYB333  
**Notebook File:** `Simple IDS CYB333 Project.ipynb`  
**Purpose:** Educational cybersecurity project focused on basic intrusion detection

## 1. Project Overview

This project is a Python-based Intrusion Detection System (IDS) designed to analyze authentication log files and detect repeated failed login attempts from the same source IP address. The program reads log entries, identifies failed login events, tracks the timestamps of those failures, and raises an alert when a threshold is reached.

The goal of this project is to demonstrate how Python can be used for basic security monitoring and log analysis in an educational setting. It uses a lightweight, rule-based detection approach rather than advanced intrusion detection methods, making it suitable for learning and classroom use.

## 2. Project Objectives

The main objectives of this project are to:

- Develop a basic intrusion detection system using Python.
- Analyze authentication logs for failed login attempts.
- Extract source IP addresses associated with suspicious activity.
- Track repeated failed login attempts over a defined time period.
- Trigger alerts when activity exceeds a configured threshold.
- Demonstrate cybersecurity concepts in a simple, practical implementation.
- Apply Python programming skills to a realistic security scenario.
- Document the system clearly for learning and future expansion.

## 3. Key Features

### Authentication Log Analysis
The program reads an authentication log file line by line and searches for failed login attempts.

### IP Address Extraction
A regular expression identifies failed login entries and extracts the relevant source IP address from each event.

### Failure Tracking
The system keeps a record of failed login timestamps for each IP address using Python data structures.

### Time-Based Detection
The IDS evaluates failed attempts within a configurable time window so that only recent activity is considered.

### Threshold-Based Alerts
An alert is triggered when an IP address exceeds the defined number of failed login attempts within the configured time period.

### Simulated Real-Time Monitoring
A short delay between entries simulates real-time processing for demonstration purposes. The system reads from a log file rather than monitoring live traffic.

### Notebook Implementation
This project is provided in a Jupyter Notebook format:

`Simple IDS CYB333 Project.ipynb`

This allows the logic to be run interactively, with code cells and explanatory comments.

## 4. Technologies and Dependencies

This project uses the following technologies and standard library modules:

- **Python 3**: Main programming language
- **`re`**: For matching log patterns and extracting IP addresses
- **`time`**: For timestamps and simulated delay handling
- **`collections`**: For organizing failed-attempt tracking
- **Jupyter Notebook**: For interactive project execution and documentation

No external packages are required beyond Python and Jupyter Notebook.

## 5. Prerequisites

Before running the project, make sure you have:

- Python 3 installed on your machine
- Jupyter Notebook or JupyterLab installed
- A log file containing authentication events
- A working understanding of basic Python syntax

The notebook and log file should be located in the same directory unless you modify the file path in the code.

## 6. Installation and Setup

### Step 1: Install Python
Download and install Python 3 from the official website:

https://www.python.org/downloads/

Verify your installation by opening a terminal and running:

```bash
python --version
```

If your system uses `python3`, run:

```bash
python3 --version
```

### Step 2: Install Jupyter Notebook
If Jupyter is not already installed, install it using:

```bash
pip install notebook
```

Then launch Jupyter with:

```bash
jupyter notebook
```

### Step 3: Download the Project
Clone the repository from GitHub:

```bash
git clone https://github.com/ordonez3922/Simple-intrusion-detection-system-.git
```

Navigate to the project folder:

```bash
cd Simple-intrusion-detection-system-
```

### Step 4: Open the Notebook
Open the file:

```bash
Simple IDS CYB333 Project.ipynb
```

in Jupyter Notebook to run the project.

## 7. How the Project Works

The IDS follows this sequence:

1. **Initialize detection settings**  
   Define the log filename, regex pattern, threshold, and time window.

2. **Read the log file**  
   Process each line in the authentication log.

3. **Identify failed login events**  
   Use a regular expression to find failed password attempts.

4. **Extract the source IP**  
   Capture the IP address associated with each failed login event.

5. **Track timestamps**  
   Store the time when each failed attempt occurred.

6. **Filter outdated activity**  
   Remove attempts outside the selected time window.

7. **Evaluate threshold**  
   Check whether the number of failed attempts exceeds the allowed limit.

8. **Trigger alert**  
   Print a warning when suspicious activity is detected.

9. **Reset tracking**  
   Clear the stored attempts for the IP address after the alert is raised.

This process demonstrates the core logic behind basic event-based detection and threshold-driven alerting.

## 8. Example Log Input

Example log entries may look like this:

```text
Failed password for guest from 192.168.1.25
Failed password for guest from 192.168.1.25
Failed password for guest from 192.168.1.25
```

If the same IP address exceeds the threshold within the defined time window, the system identifies it as suspicious.

## 9. Example Output

A typical alert output may look like:

```text
ALERT: 192.168.1.25 has exceeded the failed login threshold.
```

The actual output depends on the contents of the log file and the threshold/time-window values configured in the script.

## 10. Configuration Options

The project can be adjusted by modifying key variables such as:

- `LOG_FILE`: the authentication log location
- `THRESHOLD`: number of failed login attempts needed to trigger an alert
- `TIME_WINDOW`: time range used to evaluate repeated activity
- `FAIL_REGEX`: pattern used to detect failed login entries

These values can be changed depending on the environment and testing scenario.

## 11. Code Documentation and Standards

The code is designed to be readable and maintainable. It follows these documentation practices:

- Meaningful variable names
- Clear function separation
- Comments explaining the purpose of logic blocks
- Consistent formatting and indentation
- Simple structure that is easy to follow for educational use

This project emphasizes clarity and readability so that students and developers can easily understand how the IDS works.

## 12. Limitations

This project is intentionally simple and has several limitations:

- It reads from a log file rather than continuously monitoring live traffic.
- It depends on the log format matching the detection pattern.
- It may generate false positives for legitimate users who mistype passwords.
- It does not automatically block suspicious IP addresses.
- It does not verify whether a login eventually succeeded.
- It does not provide advanced analytics or centralized log correlation.

An alert indicates suspicious activity, not definitive proof of malicious behavior.

## 13. Future Improvements

Potential improvements include:

- Real-time log monitoring
- Saving alerts to a dedicated security log
- Supporting multiple log formats
- Logging timestamps in a more detailed format
- Detecting more advanced attack patterns
- Generating summary reports
- Sending notifications through email or messaging platforms
- Integrating with SIEM tools
- Adding command-line options for configuration

## 14. Ethical and Legal Considerations

This project should only be used on systems and logs that you own or are explicitly authorized to monitor.

Do not upload sensitive authentication logs to public repositories. Use fictional, sanitized, or authorized data for testing and educational purposes. Respect privacy, institutional policies, and applicable cybersecurity regulations when working with logs or monitoring systems.

## 15. Conclusion

The Simple IDS CYB333 Project demonstrates how Python can be used to analyze authentication logs, identify repeated failed login attempts, and generate security alerts. It provides a foundational example of event-based detection, log analysis, and cybersecurity automation.

This project is a practical introduction to intrusion detection concepts and helps connect Python programming to real-world security monitoring tasks.

## 16. Author Information

**Name:** Nikolas Ordonez  
**GitHub:** ordonez3922  
**Course:** CYB333  
**Project:** Simple IDS CYB333 Project

Educational cybersecurity project focused on Python-based intrusion detection and log analysis.
