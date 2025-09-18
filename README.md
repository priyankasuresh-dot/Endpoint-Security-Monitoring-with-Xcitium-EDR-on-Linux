# Endpoint-Security-Monitoring-with-Xcitium-EDR-on-Linux
This project demonstrates how to deploy Xcitium OpenEDR on a Linux endpoint to monitor, detect, and respond to security threats in real time. OpenEDR provides continuous endpoint telemetry, next-gen antivirus (NGAV), and automated response actions, offering stronger protection than traditional antivirus.
# Why EDR Matters

EDR solutions combine continuous endpoint telemetry with behavioral analytics to identify suspicious activities quickly. Core benefits include:

Continuous Monitoring – Track processes, file modifications, network connections, and user activity in real time.

Threat Detection – Identify malicious behaviors, including zero-day exploits and fileless malware.

Incident Response – Quarantine devices, kill malicious processes, and collect forensic evidence.

Visibility & Investigation – Provide detailed alerts and forensic data for security operations teams.

Unlike traditional antivirus that simply blocks known malware, EDR tools emphasize detection and response, making them essential for modern defense-in-depth strategies.

# About Xcitium OpenEDR

Xcitium (formerly Comodo) OpenEDR is a free, open-source endpoint security platform that combines Next-Gen Antivirus (NGAV) and EDR capabilities in one lightweight agent.

# Key features:

Real-Time Protection – Detects malware, ransomware, and suspicious behaviors immediately.

Cross-Platform – Works on Windows, Linux, and macOS.

Cloud-Based Management – Centralized control via the Xcitium ITSM/Endpoint Manager console.

Zero Trust Architecture – Unrecognized files are executed in a secure container until verified safe.

Forensic Analysis – Provides logs, file hashes, and detailed alerts for incident response.

# Project Objectives

The primary goals of this lab were to:

Install and configure the Xcitium OpenEDR agent on a Linux endpoint.

Enroll the device into the Xcitium ITSM (cloud-based management portal).

Generate safe malware simulations using EICAR test files.

Observe how OpenEDR detects, blocks, and quarantines threats.

Review alerts, logs, and forensic details in the management console.

Demonstrate complete endpoint protection and incident-response capabilities.

# Lab Environment
Component	Details
Host Machine	Windows or Linux PC with VirtualBox/VMware
Target Endpoint	Ubuntu 20.04 (Linux VM)
Management	Xcitium ITSM / Endpoint Manager (cloud console)
Tools	Linux utilities (wget, chmod, zip/unzip), EICAR test files
# Tools Used

Xcitium Endpoint Agent
Installed on the Ubuntu VM to provide monitoring and protection.

Xcitium ITSM / Endpoint Manager
Cloud-based console for device enrollment, alert management, and policy control.

Linux Command-Line Utilities
Used for downloading, installing, and managing test files.

EICAR Test Files
Harmless files used industry-wide to safely simulate malware detections.

# Implementation Steps
1. Download and Install the Xcitium Agent

Log into the Xcitium console and navigate to Devices → Enrollment / Installers.

Select Linux and copy the unique enrollment link.

Download the installer script and run:

sudo chmod +x itsm
sudo ./itsm


The script automatically registers the endpoint with your console.

2. Verify Enrollment

In the Xcitium console, open Devices and confirm that the Linux VM shows as Online / Enrolled.

3. Simulate Malware with EICAR Files

On the Ubuntu VM, download the safe test files:

wget https://secure.eicar.org/eicar_com.zip
wget https://secure.eicar.org/eicarcom2.zip


These files are harmless but recognized as malware by security tools.

4. Detection and Scanning

Run a local scan using the Xcitium agent or wait for real-time detection.

The EDR identifies the EICAR files and flags them as malicious.

5. Quarantine and Response

In the console, navigate to Security → Blocked Threats to see detection details: file name, hash, detection type, and timestamp.

Use the Quarantine File option to isolate the files.

Confirm quarantine under Security → Quarantined Threats.

6. Review Alerts and Logs

Check the device details, file paths, and cryptographic hashes.

Analyze timestamps and signatures to understand how the EDR responded.

# Results

The Xcitium agent successfully detected the EICAR test files, blocked their execution, and moved them into secure quarantine. All events—including detection time, file hash, and actions taken—were visible in the Xcitium management console, demonstrating full EDR functionality: monitoring, detection, automated response, and centralized visibility.

# Key Takeaways

EDR solutions like Xcitium OpenEDR provide comprehensive endpoint security that traditional antivirus cannot match.

The Zero Trust approach ensures unrecognized files are contained until verified safe.

Cloud-based management simplifies incident response and provides a single pane of glass for security teams.

Simulated tests (EICAR) validate deployment and confirm readiness for real-world threats.
