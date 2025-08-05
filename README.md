# Keyboard-Fault-Detector

**Python Keyboard Fault Detector (with Scancode) & Fixes**

---

## Overview

This guide provides two tools to help you diagnose and permanently disable a faulty or "stuck" key on a Windows machine:

- **`key.py`**: A Python script to identify the name and hardware scancode of any key being pressed, even phantom presses from a faulty key.
- **Windows Registry Fix**: A permanent solution to disable a key at the system level using the scancode found with the Python script.

---

## 1. Python Keyboard Fault Detector (`key.py`)

This script is your diagnostic tool. It listens to all keyboard activity and prints the name and unique hardware scancode for every key press it detects. If a key is malfunctioning and sending repeated signals, this script will reveal exactly which key it is and provide the scancode needed for the registry fix.

### Requirements

- Python 3 installed on your system
- The `keyboard` library

### How to Use

#### Step 1: Install the `keyboard` library

Open a Command Prompt or PowerShell terminal and run:

```bash
pip install keyboard
