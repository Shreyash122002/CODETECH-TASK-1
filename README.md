# CODETECH-TASK-2
CODETECH  TASK-1 - VULNERABILITY SCANNING TOOL

Name: Shreyash Santosh kajrolkar

Company: CODTECH IT SOLUTIONS

ID: CT6WDS2149 

Domain:  CYBER SECURITY AND ETHICAL HACKING 

Duration: OCTOBER 10th, 2024 to NOVEMBER 25th, 2024 

Vulnerability Scanner
This Python script is a multi-functional security tool designed to perform network and web server vulnerability assessments. It encompasses functionalities for port scanning, outdated software detection, and identification of potential security misconfigurations. This tool uses threading to optimize port scanning and simulates delays to emulate real-world scenarios.


Overview

The script provides three primary capabilities:
Port Scanning:
Identifies open ports on a target IP address within a specified range. Utilizes concurrent threads to improve efficiency and speed.

Outdated Software Detection:
Fetches and analyzes the Server HTTP header to determine if the server is running outdated or known software versions.

Security Misconfiguration Detection:
Analyzes HTTP response headers to identify missing security headers, insecure protocols, and unnecessary information disclosures.


Detailed Functionality

1. Port Scanning
The scan_ports function conducts a thorough scan of a range of ports on a given IP address. It operates as follows:
IP Resolution:
Converts the target hostname into an IP address using socket.gethostbyname.
Port Scanning Loop:
Iterates through the specified port range (from start_port to end_port).
Socket Connection:
Attempts a connection to each port using socket.socket and sock.connect_ex. If the port is open, it is added to the list of open ports.
Delay Simulation:
Introduces a half-second delay between each port scan to reduce the load on the target and mimic real-world scanning intervals.
Threading:
In the scan_network function, port scanning tasks are divided among multiple threads to enhance performance and handle larger port ranges concurrently.


3. Outdated Software Detection
The check_outdated_software function is responsible for determining whether the target web server is running outdated software:
Header Fetching:
Sends an HTTP GET request to the specified URL and retrieves the server’s HTTP headers.
Header Analysis:
Extracts the Server header, if present, to infer the software version and assess whether it is outdated or known to be vulnerable.
Simulated Delays:
Introduces artificial delays to mimic real-world operations and to give users a realistic wait time during checks.


5. Security Misconfiguration Detection
The check_misconfigurations function performs an analysis of HTTP headers to identify common security misconfigurations:
Header Analysis:
Retrieves and examines the HTTP headers from the target URL.
Missing Security Headers:
Checks for the absence of critical security headers such as X-Frame-Options, X-Content-Type-Options, Content-Security-Policy, and Strict-Transport-Security.
Insecure Protocol Detection:
Identifies if the target is using HTTP instead of HTTPS, which is considered insecure.
Unnecessary Header Disclosure:
Checks for the presence of the Server header, which might reveal sensitive information about the server’s software.


7. Input Validation
To ensure that the input provided by the user is valid, the script includes functions for:
IP Address Validation:
The is_valid_ip function uses a regular expression to verify if the input is a valid IP address. URL Validation: The is_valid_url function checks if the input URL starts with http:// or https:// to confirm that it is a properly formatted URL.
