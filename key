# Python Keyboard Fault Detector
#
# This script helps diagnose a faulty or "stuck" keyboard key.
# It listens for all key presses and prints the name of the key to the console.
#
# If you see a key's name being printed repeatedly without you pressing it,
# that is likely the faulty key.
#
# How to run this script:
# 1. Make sure you have Python installed on your system.
# 2. Install the 'keyboard' library by opening your terminal or command prompt and typing:
#    pip install keyboard
# 3. Save this code as a Python file (e.g., key_tester.py).
# 4. Run the script from your terminal with administrator/root privileges:
#    - On Windows: Open Command Prompt as Administrator and run 'python key_tester.py'
#    - On macOS/Linux: Run 'sudo python key_tester.py'
#
# IMPORTANT: Administrator/root privileges are required because listening to
# global keyboard events is a privileged operation.
#
# To stop the script, press the 'Esc' key.

import keyboard
import time

# A flag to control the main loop
running = True

def on_key_press(event):
    """
    This function is called every time a key is pressed.
    It prints the name of the key that was pressed.
    """
    print(f"Key Pressed: {event.name} (Scancode: {event.scan_code})")
def stop_script():
    """
    This function sets the running flag to False to stop the main loop.
    """
    global running
    print("\n'Esc' key pressed. Exiting script...")
    running = False

def main():
    """
    Main function to set up the listener and run the script.
    """
    print("Starting keyboard fault detector...")
    print("Press any key to see its name printed below.")
    print("If a key is faulty, you will see its name spammed here.")
    print("Press 'Esc' to stop the script.")
    print("-" * 30)

    # Register the function to be called on each key press
    keyboard.on_press(on_key_press)

    # Register a hotkey to stop the script.
    # The 'suppress=True' argument prevents the 'Esc' press from being passed
    # to other applications, ensuring the script can capture it reliably.
    keyboard.add_hotkey('esc', stop_script, suppress=True)

    # Keep the script running until the 'Esc' key is pressed.
    # The time.sleep() prevents the loop from consuming too much CPU.
    while running:
        time.sleep(0.1)

    # Unhook all keyboard events before exiting to clean up.
    keyboard.unhook_all()
    print("Script stopped.")

if __name__ == "__main__":
    main()
