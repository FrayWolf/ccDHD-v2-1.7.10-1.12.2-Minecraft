# ccDHD-v2-1.7.10-1.12.2-Minecraft
ccDHD v2 is a ComputerCraft/CC: Tweaked program that lets you control multiple Stargates on a wired network from an Advanced Computer’s terminal, offering dialling, iris control, and more in Minecraft 1.7.10 and 1.12.2.


ccDHD v2 User Manual
Introduction
ccDHD v2 is an advanced Stargate control program for ComputerCraft (Minecraft 1.7.10) and CC: Tweaked (Minecraft 1.12.2), designed to manage multiple Stargates on a single Advanced Computer using a wired modem network. It features a graphical user interface (GUI) on the built-in terminal (51x19 resolution), offering gate dialing, iris control, address book management, user permissions, diagnostics, and more. This manual covers setup and usage for both Minecraft versions, with options to run the program manually or on startup, and instructions for installing from a specific GitHub repository without using wget.
Prerequisites
Minecraft Version:
1.7.10: Requires ComputerCraft mod (e.g., version 1.75).

1.12.2: Requires CC: Tweaked mod (e.g., version 1.80pr1 or later).

Advanced Computer: A ComputerCraft/CC: Tweaked Advanced Computer (gold casing, color terminal, 51x19 resolution).

Wired Modem: A wired modem attached to the Advanced Computer (default side: "back"), connected to Stargates via networking cables.

Stargates: One or more Stargate peripherals (e.g., from Aunis or SG Craft) linked via the wired network.

Networking Cables: ComputerCraft/CC: Tweaked cables to connect the modem to Stargates.

Filesystem Access: Ensure the fs API is supported (standard in both mods).

Installation and Setup
Step 1: Install the Program
Access the Advanced Computer:
In Minecraft 1.7.10 (ComputerCraft) or 1.12.2 (CC: Tweaked), right-click the Advanced Computer to open its terminal (color support required).

Download the Code from GitHub:
The program is hosted at: https://github.com/FrayWolf/ccDHD-v2-1.7.10-1.12.2-Minecraft.

Since wget is not used, follow one of these methods:
Method 1: Manual Copy via Browser:
On your real-world computer, visit https://github.com/FrayWolf/ccDHD-v2-1.7.10-1.12.2-Minecraft.

Locate the ccdhd.lua file (likely in the repository’s root or a "src" folder).

Click the file, then click "Raw" to view the plain text version.

Copy all the code (Ctrl+C or right-click > Copy).

In Minecraft, type edit ccdhd.lua on the Advanced Computer, paste the code (right-click to paste or use Ctrl+V if supported), press Ctrl, select "Save," and exit.

Method 2: Local File Transfer:
Download the repository as a ZIP file from GitHub (click "Code" > "Download ZIP").

Extract the ZIP on your real-world computer.

Find ccdhd.lua and open it in a text editor.

Copy the code.

In Minecraft, type edit ccdhd.lua, paste the code, save, and exit.

Step 2: Choose Activation Method
You can run ccDHD v2 manually or set it to start automatically on boot:
Option 1: Manual Activation
Run the Program: Type ccdhd.lua and press Enter each time you want to start it.

Ideal for occasional use or testing.

Option 2: Automatic Startup
Set as Startup:
Rename or copy the file to startup:
Type rename ccdhd.lua startup (replaces any existing startup script), or

Type copy ccdhd.lua startup (keeps the original).

Reboot the computer:
Type reboot and press Enter, or break and replace the Advanced Computer.

The program will run automatically on boot.

Ideal for dedicated Stargate control stations.

Step 3: Hardware Setup
Wired Modem Configuration
Attach a wired modem to the Advanced Computer (default side: "back").

Connect the modem to each Stargate using networking cables:
Run a cable from the modem to the first Stargate.

Extend cables to additional Stargates (e.g., daisy-chain or hub topology).

Ensure all Stargates are powered and linked via cables.

Multiple Stargates
Supports up to 20 Stargates (configurable via config.MAX_GATES) on the wired network.

Each Stargate must have a unique peripheral name (e.g., "stargate_0", "stargate_1").

Step 4: Initial Software Setup
When you first run ccDHD v2 (manually or via startup):
Modem Detection
Checks for a wired modem on the "back" side (configurable in config.MODEM_SIDE).

Retries 5 times (2-second delay) if not found. If it fails, it errors with "No modem found on back after retries." Verify the modem is attached and cabled.

Admin Account Creation
If no dhd_config.txt exists, the terminal prompts for an admin account:
Username: Type a username (default: "admin" if blank) and press Enter.

Password: 
Enter a password and confirm it, or type R for a random 8-character password (e.g., "Kj#9mPx$").

If generated, note it down—it’s shown only once.

Recovery Code: A 6-character code (e.g., "X7kP9m") is displayed. Save this—it’s stored in recovery_code.txt for recovery.

Press Enter to finish. Credentials are saved, and the action is logged.

Gate Detection
Scans the wired network for Stargates.

Detects up to 20 gates and selects the first as active.

If none are found, it shows "No Stargates found on network" and exits after 2 seconds (manual run) or loops on startup. Check cables and power.

Step 5: Login
After setup, login is required:
Username: Type your username (e.g., "admin") and press Enter.

Password: Enter your password (shown as asterisks) and press Enter.
If incorrect, it displays "Wrong credentials!" in red and resets.

Press F12 for recovery (see "Password Recovery" below).

Post-Login Prompt:
Press C to change your password (enter and confirm a new one).

Press Enter to proceed to the main interface.

Main Interface and Navigation
Overview
The GUI runs on the Advanced Computer’s 51x19 color terminal:
Main Page (Page 1): Shows the active gate’s status and controls.

System Functions (Page 2): Lists functions for managing multiple gates.

Navigation uses key presses (e.g., M for menu, F1 to return).

Key Controls
M: Open System Functions menu (from Main Page).

T: Toggle the iris of the active gate.

F1: Return to the previous page.

Up/Down: Scroll through lists (e.g., gate selection, address book).

E: Emergency shutdown (affects the active gate).

G: Dial a gate manually.

A: Open the address book.

U: Manage user permissions (admin only).

Main Page Layout
Gate: Name of the active gate (e.g., "Earth Gate" or "stargate_0").

Address: Local address (e.g., "ABC123").

Distance: Distance to the active gate in blocks (from config.gatePositions).

Status: "Connected" (green) or "Disconnected" (red).

System Gates: Number of gates on the wired network.

Iris: "Open" or "Closed" for the active gate.

Gate Activation: Dialed or incoming address when connected.

Power: Fuel percentage (red if below 20%).

Security: Status like "allclear" (green), "incoming" (yellow), "blocked" (orange).

LOCKDOWN: Shows "LOCKDOWN" in red if active.

Controls: [E]mergency (red), [M]enu (yellow).

Features and Usage
1. Gate Management
Selecting a Gate
Press M → S (Select Gate).

Use Up/Down to highlight a gate, press S to set it as active.

Shows name, address, state, and group (if set).

Naming a Gate
Press M → N (Name Gate).

Type a name (e.g., "Gamma Site") and press Enter.

Saved in config.gateNames.

Dialing a Gate
Manual Dialing:
Press M → G (Dial Gate).

Enter a 6-9 character address (e.g., "XYZ789") and press Enter.

The active gate dials; result is logged.

From Address Book:
Press M → A, select an entry with Up/Down, press D (Dial).

Disconnecting a Gate
Press M → D (Disconnect Gate).

Disconnects the active gate.

Iris Control
Press T to toggle the iris of the active gate.

Logs the action (e.g., "Iris closed on stargate_0").

Emergency Shutdown
Press E from the Main Page.

Disconnects the active gate and closes its iris (if config.EMERGENCY_IRIS_CLOSE is true).

Enables lockdown mode.

Lockdown Mode
Press M → L (Toggle Lockdown).

Prevents dialing from the active gate and disconnects it. Shows "LOCKDOWN".

2. Address Book
Access: M → A.

Lists addresses with name, code, trust status ([T] or [U]), and block status ([B]).

Adding an Address
Press A (Add) → type a name (e.g., "Pegasus") → Enter → type an address (e.g., "DEF456") → Enter.

Saved with isTrusted = false.

Managing Entries
Trust: Select with Up/Down, press T to toggle trust.

Block: Press B to toggle blocking (stops incoming calls).

Dial: Press D to dial using the active gate.

Clear: Press C to erase all entries.

Save: Press S to save to addressBook.txt.

Search: Press Q, type a query (e.g., "Earth"), press Enter to filter.

Recent Addresses
Tracks the last 10 dialed addresses (configurable via config.MAX_RECENT_ADDRESSES) as "Recent 1", etc., if not in the address book.

3. Diagnostics
Access: M → I (Diagnostics).

Shows:
Fuel Level: Percentage and bar for the active gate (red if below 20%).

Log Entries: Recent actions (scroll with Up/Down).

Logs saved to gate_log.txt.

4. User Permissions (Admin Only)
Access: M → U.

Lists users and roles (e.g., "admin", "user").

Adding a User
Press A → type a username → Enter → type a password → Enter.

Default role is "user".

Managing Users
Change Role: Select with Up/Down, press R to toggle "admin"/"user".

Delete: Press D to remove (cannot delete "admin").

5. Gate Network Map
Access: M → M (Gate Network Map).

Visualizes gates on the wired network:
O: Advanced Computer (yellow).

G: Network gates (green if connected, red if disconnected).

*: Active gate (cyan).

Gates are arranged in a circle.

6. Password Management
Changing Password
After login, press C, enter a new password, and press Enter.

Password Recovery
At login, press F12 → enter the recovery code → enter and confirm a new password.

Enabled if config.RECOVERY_ENABLED is true.

Configuration Options
Edit in dhd_config.txt or the script (edit ccdhd.lua or edit startup depending on your activation choice):
MODEM_SIDE: Wired modem side (default: "back").

MAX_GATES: Max detectable gates (default: 20).

FUEL_WARNING_THRESHOLD: Low fuel warning (default: 20%).

SYNC_INTERVAL: Gate sync frequency (default: 0.5 seconds).

ADDRESS_MIN_LENGTH/MAX_LENGTH: Address range (default: 6-9).

AUTO_DIAL_ADDRESS: Startup dial address (default: nil).

PRE_DIAL_ADDRESS: Dial first address book entry on startup (default: false).

LOCKDOWN_MODE: Start in lockdown (default: false).

EMERGENCY_IRIS_CLOSE: Close iris on emergency (default: true).

Compatibility Notes
Minecraft 1.7.10 (ComputerCraft):
Tested with ComputerCraft 1.75.

Requires a Stargate mod compatible with ComputerCraft’s peripheral API (e.g., SG Craft).

Minecraft 1.12.2 (CC: Tweaked):
Tested with CC: Tweaked 1.80pr1 or later.

Requires a Stargate mod compatible with CC: Tweaked’s peripheral API (e.g., Aunis).

Uses standard Lua and ComputerCraft/CC: Tweaked APIs, ensuring compatibility.

Troubleshooting
No Modem Found: Ensure the wired modem is on "back" and cabled.

No Stargates Detected: Verify cables and power; check Stargate mod compatibility.

Login Issues: Confirm credentials; use recovery if needed.

Terminal Display Issues: Ensure you’re using an Advanced Computer (color support required).

Example Workflow
Setup: Cable modem to three Stargates, visit https://github.com/FrayWolf/ccDHD-v2-1.7.10-1.12.2-Minecraft, copy ccdhd.lua into edit ccdhd.lua, optionally rename ccdhd.lua startup, set up "admin" with "Pass123", save recovery code "K9mP2x".

Login: Enter "admin" and "Pass123".

Select Gate: Press M → S, choose "stargate_1", press S.

Dial: Press M → G, enter "ABC123", press Enter.

Add Address: Press M → A → A, add "Earth" with "ABC123".

Toggle Iris: Press T.

Emergency: Press E.

This manual is tailored for the GitHub repository https://github.com/FrayWolf/ccDHD-v2-1.7.10-1.12.2-Minecraft, avoids wget, and supports both manual (ccdhd.lua) and automatic (startup) activation for Minecraft 1.7.10 (ComputerCraft) and 1.12.2 (CC: Tweaked). For further help, consult the repository or code comments. Enjoy managing your Stargates!

