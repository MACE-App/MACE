# M.A.C.E. Audit Report

**Example Benchmark**

**Author:** John Doe, Example Organization

---

## Results

| Total | ✅ Passed | ❌ Failed | ⚠️ Errors | 🔍 Manual Review |
|------:|------:|------:|------:|------:|
| 117 | 35 | 80 | 0 | 1 |

## Executive Summary

🔴 This system shows **poor compliance** with a 30.4% pass rate and requires significant remediation.

Audit found **80 of 117** rules failing. 1 rule(s) require manual review.

**Areas needing attention:** Password Policy (0% - 8 failed), iCloud (0% - 1 failed), System Settings (25% - 33 failed)

## Audit Information

| | |
|---|---|
| **Pass Rate** | 30.4% |
| **Compliance** | CIS Level 2 |
| **Platform** | macOS |
| **Baseline** | macOS 26 (Tahoe) |

## Device

| | |
|---|---|
| **Model** | MacBook Air |
| **Serial Number** | C02XY1234Z |
| **OS Version** | macOS 27.0.0 |

## Section Summary

| Section | Total | Passed | Failed | Manual | Pass Rate |
|---|---:|---:|---:|---:|---:|
| Password Policy | 8 | 0 | 8 | 0 | 🔴 0% |
| iCloud | 1 | 0 | 1 | 0 | 🔴 0% |
| Supplemental | 1 | 0 | 0 | 1 | 🔴 0% |
| System Settings | 44 | 11 | 33 | 0 | 🔴 25% |
| Audit | 21 | 7 | 14 | 0 | 🔴 33% |
| Operating System | 42 | 17 | 24 | 0 | 🔴 40% |

## Table of Contents

1. [Failed](#failed-80) (80 rules)
2. [Manual Review](#manual-review-1) (1 rule)
3. [Passed](#passed-35) (35 rules)
4. [Not Applicable](#not-applicable-1) (1 rule)

## Failed (80)

### Ensure Location Services Is In the Menu Bar

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```

```

**Error:** Expected: 1, Got: 

### Enforce Session Lock After Screen Saver is Started

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Disable Printer Sharing

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable the Guest Account

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Require Administrator Password to Modify System-Wide Preferences

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Improve Search Information to Apple

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
2
```

**Actual Result:**

```

```

**Error:** Expected: 2, Got: 

### Disable Server Message Block Sharing

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure Login Window to Prompt for Username and Password

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Disable Personalized Advertising

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Configure Time Machine for Automatic Backups

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Disable Password Hints

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
0
```

**Actual Result:**

```

```

**Error:** Expected: 0, Got: 

### Disable External Intelligence Integrations

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Enforce Screen Saver Timeout

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Enforce FileVault

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Content Caching Service

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Internet Sharing

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Enable macOS Application Firewall

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Disable Siri

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Bluetooth Sharing

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
0
```

**Actual Result:**

```

```

**Error:** Expected: 0, Got: 

### Ensure Wake for Network Access Is Disabled

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
0
```

**Actual Result:**

```
1
```

**Error:** Expected: 0, Got: 1

### Disable Sending Diagnostic and Usage Data to Apple

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Disable Improve Siri and Dictation Information to Apple

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
2
```

**Actual Result:**

```

```

**Error:** Expected: 2, Got: 

### Configure Login Window to Show A Custom Message

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
Q2VudGVyIGZvciBJbnRlcm5ldCBTZWN1cml0eSBUZXN0IE1lc3NhZ2UK
```

**Actual Result:**

```

```

**Error:** Expected: Q2VudGVyIGZvciBJbnRlcm5ldCBTZWN1cml0eSBUZXN0IE1lc3NhZ2UK, Got: 

### Disable Unattended or Automatic Logon to the System

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Disable External Intelligence Integration Sign In

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Sending Audio Recordings and Transcripts to Apple

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Enforce macOS Time Synchronization

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Enforce Screen Saver Password

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Configure macOS to Use an Authorized Time Server

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
time.apple.com
```

**Actual Result:**

```

```

**Error:** Expected: time.apple.com, Got: 

### Disable Media Sharing

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Disable Airplay Receiver

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Remote Apple Events

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure System to Audit All Failed Change of Object Attributes

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure System to Audit All Authorization and Authentication Events

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure System to Audit All Administrative Action Events

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure System to Audit All Failed Program Execution on the System

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Enable Security Auditing

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
pass
```

**Actual Result:**

```
fail
```

**Error:** Expected: pass, Got: fail

### Configure Audit Log Files to Mode 440 or Less Permissive

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
22
```

**Error:** Expected: 0, Got: 22

### Configure Audit_Control Owner to Root

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```

```

**Error:** Expected: 0, Got: 

### Configure System to Audit All Failed Read Actions on the System

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure System to Audit All Failed Write Actions on the System

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure Audit Retention to $ODV

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
60d OR 5G
```

**Actual Result:**

```

```

**Error:** Expected: 60d OR 5G, Got: 

### Configure Audit Log Folders to Mode 700 or Less Permissive

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
700
```

**Actual Result:**

```
666
```

**Error:** Expected: 700, Got: 666

### Configure System to Audit All Log In and Log Out Events

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Configure Audit_Control Group to Wheel

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```

```

**Error:** Expected: 0, Got: 

### Configure Audit Log Files Group to Wheel

**Status:** ❌ Fail · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
320
```

**Error:** Expected: 0, Got: 320

### Ensure Warn When Visiting A Fraudulent Website in Safari Is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Apple Intelligence Notes Transcription

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Automatic Opening of Safe Files in Safari

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Apple Intelligence Mail Summary

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Apple Intelligence Notes Transcription Summary

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Ensure Advertising Privacy Protection in Safari Is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Ensure Sleep and Display Sleep Is Enabled on Apple Silicon Devices

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
1
```

**Error:** Expected: 0, Got: 1

### Enable Firewall Stealth Mode

**Status:** ❌ Fail · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Enforce Software Update App Update Updates Automatically

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Configure Sudo To Log Events

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Display Policy Banner at Login Window

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Apple Intelligence Writing Tools

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Network File System Service

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
pass
```

**Actual Result:**

```
fail
```

**Error:** Expected: pass, Got: fail

### Disable AirDrop

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Ensure Show Full Website Address in Safari Is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Ensure Secure Keyboard Entry Terminal.app is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Enable Gatekeeper

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Configure Sudo Timeout Period to $ODV

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Secure User's Home Folders

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
3
```

**Error:** Expected: 0, Got: 3

### Configure Install.log Retention to $ODV

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
Yes
```

**Actual Result:**

```
all_max setting is configured, must be removed
TTL not configured
```

**Error:** Expected: Yes, Got: all_max setting is configured, must be removed TTL not configured

### Enforce On Device Dictation

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Ensure Prevent Cross-site Tracking in Safari Is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Disable Bonjour Multicast

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```

```

**Error:** Expected: true, Got: 

### Require Passwords to Match the Defined Custom Regular Expression

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
true
```

**Actual Result:**

```
false
```

**Error:** Expected: true, Got: false

### Restrict Maximum Password Lifetime to $ODV Days

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```

```

**Error:** Expected: pass, Got: 

### Prohibit Password Reuse for a Minimum of $ODV Generations

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```

```

**Error:** Expected: pass, Got: 

### Limit Consecutive Failed Login Attempts to $ODV

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```

```

**Error:** Expected: pass, Got: 

### Require Passwords Contain a Minimum of One Special Character

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```

```

**Error:** Expected: pass, Got: 

### Set Account Lockout Time to $ODV Minutes

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```

```

**Error:** Expected: pass, Got: 

### Require Passwords Contain a Minimum of One Numeric Character

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

### Require a Minimum Password Length of $ODV Characters

**Status:** ❌ Fail · **Section:** Password Policy

**Expected Result:**

```
pass
```

**Actual Result:**

```
fail
```

**Error:** Expected: pass, Got: fail

### Disable iCloud Desktop and Document Folder Sync

**Status:** ❌ Fail · **Section:** iCloud

**Expected Result:**

```
false
```

**Actual Result:**

```

```

**Error:** Expected: false, Got: 

### Disable Login to Other User's Active and Locked Sessions

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
PASS
```

**Actual Result:**

```
FAIL
```

**Error:** Expected: PASS, Got: FAIL

### Ensure Show Safari shows the Status Bar is Enabled

**Status:** ❌ Fail · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
0
```

**Error:** Expected: 1, Got: 0

## Manual Review (1)

### CIS Manual Recommendations

**Status:** 🔍 Manual Review · **Section:** Supplemental

**Discussion:** List of CIS recommendations that are manual check in the CIS macOS Benchmark.  [cols="15%h, 85%a"] \|=== \|Section \|System Settings  \|Recommendations \| 1.7 Ensure the System is Managed by a Mobile Device Management (MDM) Software \|===  [cols="15%h, 85%a"] \|=== \|Section \|System Settings  \|Recommendations \|2.1.1.1 Audit iCloud Keychain + 2.1.1.2 Audit iCloud Drive + 2.1.1.4 Audit Security Keys Used With Apple Accounts + 2.1.1.5 Audit Freeform Sync to iCloud + 2.1.1.6 Audit Find My Mac + 2.1.2 Audit App Store Password Settings + 2.3.3.11 Ensure Computer Name Does Not Contain PII or Protected Organizational Information + 2.4.1 Audit Menu Bar and Control Center Icons + 2.5.2.2 Ensure Listen for Siri is Disabled + 2.6.1.3 Audit Location Services Access + 2.6.2.1 Audit Full Disk Access for Applications + 2.6.3.5 Ensure Share iCloud Analytics Is Disabled + 2.6.7 Audit Lockdown Mode + 2.7.2 Audit iPhone Mirroring + 2.8.1 Audit Universal Control Settings + 2.10.1.1 Ensure the OS Is Not Active When Resuming from Standby (Intel) + 2.12.2 Audit Touch ID + 2.14.1 Audit Game Center Settings + 2.15.1 Audit Notification & Focus Settings + 2.16.1 Audit Wallet & Apple Pay Settings + 2.17.1 Audit Internet Accounts for Authorized Use + \|===  [cols="15%h, 85%a"] \|=== \|Section \|Logging and Auditing  \|Recommendations \|3.6 Audit Software Inventory \|===  [cols="15%h, 85%a"] \|=== \|Section \|System Access, Authentication and Authorization  \|Recommendations \|5.2.3 Ensure Complex Password Must Contain Alphabetic Characters Is Configured + 5.2.4 Ensure Complex Password Must Contain Numeric Character Is Configured + 5.2.5 Ensure Complex Password Must Contain Special Character Is Configured + 5.2.6 Ensure Complex Password Must Contain Uppercase and Lowercase Characters Is Configured + 5.3.1 Ensure All User Storage APFS Volumes are Encrypted + 5.3.2 Ensure All User Storage CoreStorage Volumes are Encrypted + \|===  [cols="15%h, 85%a"] \|=== \|Section \|Applications  \|Recommendations \|6.1.1 Ensure Show All Filename Extensions Setting is Enabled + 6.2.1 Ensure Protect Mail Activity in Mail Is Enabled + 6.3.2 Audit History and Remove History Items + 6.3.5 Audit Hide IP Address in Safari Setting + 6.3.8 Audit Autofill + 6.3.9 Audit Pop-up Windows + 6.5.1 Audit Passwords + \|=== 

**Error:** No automated check available

## Passed (35)

### Enforce macOS Updates are Automatically Installed

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

### Ensure Time Machine Volumes are Encrypted

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Disable Guest Access to Shared SMB Folders

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
1
```

### Enable Location Services

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

### Secure Hot Corners

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Disable Remote Management

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
1
```

### Disable Screen Sharing and Apple Remote Desktop

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
PASS
```

**Actual Result:**

```
PASS
```

### Ensure Software Update is Updated and Current

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
1
```

**Actual Result:**

```
1
```

### Disable SSH Server for Remote Access Sessions

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
PASS
```

**Actual Result:**

```
PASS
```

### Enforce Software Update Downloads Updates Automatically

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

### Enforce Critical Security Updates to be Installed

**Status:** ✅ Pass · **Section:** System Settings

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

### Configure Audit Log Folders Group to Wheel

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit_Control Owner to Mode 440 or Less Permissive

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit Log Files to be Owned by Root

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit Log Folders to be Owned by Root

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit_Control to Not Contain Access Control Lists

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit Log Files to Not Contain Access Control Lists

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Configure Audit Log Folder to Not Contain Access Control Lists

**Status:** ✅ Pass · **Section:** Audit

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Disable Root Login

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Must Use an Approved Antivirus Program

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
2
```

**Actual Result:**

```
2
```

### Ensure No World Writable Files Exist in the System Folder

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Ensure All Internal User Storage APFS Volumes Are Encrypted

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
Yes
```

**Actual Result:**

```
Yes
```

### Ensure All APFS and HFS+ External User Storage Volumes Are Encrypted

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
Yes
```

**Actual Result:**

```
Yes
```

### Enable Authenticated Root

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
sealed
```

**Actual Result:**

```
sealed
```

### Enforce Installation of XProtect Remediator and Gatekeeper Updates Automatically

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

### Remove Guest Folder if Present

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Remove Password Hint From User Accounts

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
PASS
```

**Actual Result:**

```
PASS
```

### Configure Sudoers Timestamp Type

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
tty
```

**Actual Result:**

```
tty
```

### Disable the Built-in Web Server

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
PASS
```

**Actual Result:**

```
PASS
```

### Enable Apple Mobile File Integrity

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Ensure System Integrity Protection is Enabled

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
1
```

### Ensure No World Writable Files Exist in the Library Folder

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Enable Time Synchronization Daemon

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
1
```

**Actual Result:**

```
1
```

### Ensure Appropriate Permissions Are Enabled for System Wide Applications

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
0
```

**Actual Result:**

```
0
```

### Ensure Software Update Deferment Is Less Than or Equal to $ODV Days

**Status:** ✅ Pass · **Section:** Operating System

**Expected Result:**

```
true
```

**Actual Result:**

```
true
```

## Not Applicable (1)

### Disable Power Nap

**Status:** ➖ N/A · **Section:** Operating System

**Expected Result:**

```
N/A
```

**Actual Result:**

```
N/A
```

**Error:** Rule does not apply to this architecture (arm64)

---

_Generated by M.A.C.E. (macOS Advanced Compliance Editor) · Aug 9, 2026 at 7:54 PM_
