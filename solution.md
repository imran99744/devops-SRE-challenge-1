# Day 1: Menu-Based System Health Check Script 🛠️

Welcome to my submission for the **Day 1 Challenge** of the DevOps SRE Daily Challenge!

## 🚀 Objective

Build a **menu-driven Bash script** that performs **essential system health checks** and allows the user to:

- ✅ Check Disk Usage
- ✅ Monitor Running Services
- ✅ Assess Memory Usage
- ✅ Evaluate CPU Usage
- ✅ Send a Comprehensive Report via Email **every four hours**

---

## 📜 Script Overview

**Filename**: `system_health_check.sh`

This script provides an interactive menu to monitor system health metrics. Each selection performs a specific check and logs the output into a report file located at `/tmp/system_health_report.txt`.

---

## 🔧 Features

### ✅ Menu-Driven Interface

Users can interactively select an option from a numbered list. The loop keeps running until the user chooses to exit.

### ✅ System Monitoring Functions

Each monitoring task is modularized into a dedicated function:
- `check_disk_usage()`: Uses `df -h` to report disk space.
- `monitor_services()`: Uses `systemctl` to list running services.
- `check_memory_usage()`: Uses `free -h` to display memory usage.
- `check_cpu_usage()`: Uses `top` to capture CPU usage snapshot.
- `send_email_report()`: Sends a system report via `ssmtp`.

### ✅ Email Integration

A system report is compiled and emailed to a configured address using `ssmtp`.

### ✅ Debugging Support

Debugging mode is enabled by setting `DEBUG=true`, which activates `set -x` to trace commands during execution.

### ✅ Exception Handling

The script includes basic checks such as:
- File existence validation before sending emails.
- Return code checks to confirm if email was sent successfully.
- Fallback messages for invalid menu input.

---

## 🕒 Cron Job Setup

To send the system health report **every four hours**, add the following line to your crontab:

```bash
0 */4 * * * /path/to/system_health_check.sh <<< "5"


## 🧠 Lessons Learned

- Modularizing Bash functions makes scripts easier to read and extend.
- Debugging with `set -x` helps trace issues line by line.
- `ssmtp` is a simple way to send emails from Bash.
- Adding exception handling using `if` conditions makes scripts more robust.
- Scheduling with `cron` is essential for automation in DevOps and SRE.

---

## ❗Challenges Faced

- Setting up `ssmtp` and Gmail app passwords took time due to email security restrictions.
- Handling interactive input in a cron job required using `<<<` to simulate input.
- Managing multiline email content inside Bash required using `cat <<EOF`.

---

## 💬 Sharing the Experience

I'm thrilled to participate in this challenge to grow my **DevOps and SRE skills**!


