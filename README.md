# Simple Python Intrusion Detection System (IDS)

## Project Overview

This project is a Python-based Intrusion Detection System that monitors an authentication log for repeated failed login attempts. It identifies IP addresses that exceed a defined threshold within a specific time window and generates an alert.

This project demonstrates how Python can automate basic security monitoring and help identify potentially suspicious login activity.

## Objectives

- Monitor authentication logs for failed login attempts.
- Identify source IP addresses associated with failed logins.
- Track repeated attempts within a 60-second time window.
- Generate alerts when an IP address reaches the configured threshold.
- Demonstrate the use of Python for security automation.

## Key Features

- Regular-expression log analysis
- IP address extraction
- Failed login attempt tracking
- Configurable attempt threshold and time window
- Automatic alert generation
- Simulated real-time log reading

## Technologies Used

- Python 3
- `time` module
- `re` module
- `collections.defaultdict`

## Prerequisites

- Python 3 installed
- An authentication log file named `Auth.Log`
- Failed login entries formatted to match the pattern used in the script

No third-party Python packages are required because the script uses Python's standard library.

## Installation

1. Download or clone this repository.
2. Place `ids.py` and `Auth.Log` in the same directory.
3. Make sure Python 3 is installed.

## How to Run

Open a terminal in the project directory and run:

```bash
python ids.py
```

On some systems, use:

```bash
python3 ids.py
```

## How It Works

1. The program reads the authentication log one line at a time.
2. A regular expression searches for failed password attempts.
3. The source IP address is extracted from each matching entry.
4. The program records the time of each failed attempt.
5. Attempts older than 60 seconds are removed from the count.
6. An alert is generated when an IP address reaches three failed attempts within the time window.
7. The attempt counter is reset for that IP after an alert.

## Configuration

The following variables control the detection behavior:

- `LOG_FILE`: Name of the authentication log file.
- `FAIL_REGEX`: Pattern used to identify failed login attempts.
- `THRESHOLD`: Number of failed attempts needed to trigger an alert.
- `TIME_WINDOW`: Time window, in seconds, for counting attempts.

## Security Automation

This project automates the review of authentication logs, reducing the need to manually inspect every entry. The alert mechanism can help an analyst identify repeated failed login attempts that may indicate a brute-force login attempt.

## Limitations

- The program reads an existing log file rather than continuously following new entries as they arrive.
- Detection depends on the log format matching the regular expression.
- The script uses basic threshold-based detection and may produce false positives.
- An alert does not prove that an attack occurred.
- The counter resets after each alert.

## Ethical Use

Use this tool only with logs and systems you own or are authorized to monitor. Do not upload logs containing passwords, personal information, or other sensitive data to a public repository.

## Future Improvements

- Monitor new log entries continuously.
- Save alerts to a separate log file.
- Add configurable command-line options.
- Detect additional suspicious authentication patterns.
- Add automated reports and notifications.

## Author

Student Python security automation project.
