# Keyboard-Fault-Detector
Python Keyboard Fault Detector (with Scancode) & Fixes

# This guide provides two tools to help you diagnose and permanently disable a faulty or "stuck" key on a Windows machine.

key.py: A Python script to identify the name and hardware scancode of any key being pressed, even phantom presses from a faulty key.

Windows Registry Fix: A permanent solution to disable a key at the system level using the scancode found with the Python script.

1. Python Keyboard Fault Detector (key.py)
This script is your diagnostic tool. It listens to all keyboard activity and prints the name and unique hardware scancode for every key press it detects. If a key is malfunctioning and sending repeated signals, this script will reveal exactly which key it is and provide the scancode needed for the registry fix.

Requirements
Python 3 installed on your system.

The keyboard library.

How to Use
Step 1: Install the keyboard library

Open a Command Prompt or PowerShell terminal and run the following command:

pip install keyboard

Step 2: Run the Script with Administrator Privileges

It is essential to run this script as an administrator, otherwise it cannot monitor system-wide keyboard events.

Save the script from the Canvas to a file named key.py.

Right-click the Start Menu and select Command Prompt (Admin) or Windows PowerShell (Admin).

Navigate to the directory where you saved the file (e.g., cd C:\Users\YourUser\Desktop).

Run the script using the command:

python key.py

Step 3: Diagnose the Faulty Key

Once the script is running, do not touch your keyboard.

Watch the output. If a key is faulty, you will see its details spammed repeatedly in the console, for example:

Key Pressed: browser_home (Scancode: 562)

Note down the Scancode number. This is the crucial piece of information you need for the permanent fix.

Press the Esc key to stop the script.

2. Windows Registry Fix (Permanent Disable)
This method uses the scancode you found to tell Windows to completely ignore any input from that specific key. This is the most powerful software method for disabling a key.

Warning: Editing the registry can be risky. Follow these steps carefully.
Step 1: Open Registry Editor

Press the Windows Key + R to open the Run dialog.

Type regedit and press Enter.

Click "Yes" to allow the app to make changes.

Step 2: Navigate to the Keyboard Layout Key

In the address bar at the top of the Registry Editor, copy and paste the following path and press Enter:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout

Step 3: Create the Scancode Map

In the right-hand pane, right-click on an empty space.

Select New > Binary Value.

Name the new value exactly Scancode Map.

Step 4: Enter the Disabling Code

Double-click the Scancode Map value you just created.

In the "Edit Binary Value" window, you will enter a specific hexadecimal code. The code below is specifically for disabling the "Browser Home" key (which has a scancode that translates to E032).

Enter the following sequence exactly:

00 00 00 00 00 00 00 00 02 00 00 00 00 00 32 E0 00 00 00 00

Click OK.

Step 5: Restart Your Computer

You must restart your computer for the changes to take effect. After restarting, the faulty key will be permanently disabled.

How to Undo the Registry Fix
If you ever need to re-enable the key, simply:

Navigate back to the same location in the Registry Editor.

Right-click the Scancode Map value and select Delete.

Restart your computer.
