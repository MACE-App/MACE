# macOS Security Configuration

**Compliance Guide - CIS Level 1**

**Version:** macOS 26 (Tahoe) &nbsp;|&nbsp; **Date:** 2026-04-29

---

## Table of Contents

1. [Operating System](#operating-system) (36 rules)
   - [os_safari_warn_fraudulent_website_enable](#ossafariwarnfraudulentwebsiteenable) — Ensure Warn When Visiting A Fraudulent Website in Safari Is Enabled
   - [os_root_disable](#osrootdisable) — Disable Root Login
   - [os_power_nap_disable](#ospowernapdisable) — Disable Power Nap
   - [os_notes_transcription_disable](#osnotestranscriptiondisable) — Disable Apple Intelligence Notes Transcription
   - [os_anti_virus_installed](#osantivirusinstalled) — Must Use an Approved Antivirus Program
   - [os_world_writable_system_folder_configure](#osworldwritablesystemfolderconfigure) — Ensure No World Writable Files Exist in the System Folder
   - [os_mail_summary_disable](#osmailsummarydisable) — Disable Apple Intelligence Mail Summary
   - [os_safari_open_safe_downloads_disable](#ossafariopensafedownloadsdisable) — Disable Automatic Opening of Safe Files in Safari
   - [os_safari_advertising_privacy_protection_enable](#ossafariadvertisingprivacyprotectionenable) — Ensure Advertising Privacy Protection in Safari Is Enabled
   - [os_authenticated_root_enable](#osauthenticatedrootenable) — Enable Authenticated Root
   - [os_config_data_install_enforce](#osconfigdatainstallenforce) — Enforce Installation of XProtect Remediator and Gatekeeper Updates Automatically
   - [os_notes_transcription_summary_disable](#osnotestranscriptionsummarydisable) — Disable Apple Intelligence Notes Transcription Summary
   - [os_guest_folder_removed](#osguestfolderremoved) — Remove Guest Folder if Present
   - [os_software_update_app_update_enforce](#ossoftwareupdateappupdateenforce) — Enforce Software Update App Update Updates Automatically
   - [os_password_hint_remove](#ospasswordhintremove) — Remove Password Hint From User Accounts
   - [os_sudo_log_enforce](#ossudologenforce) — Configure Sudo To Log Events
   - [os_writing_tools_disable](#oswritingtoolsdisable) — Disable Apple Intelligence Writing Tools
   - [os_sudoers_timestamp_type_configure](#ossudoerstimestamptypeconfigure) — Configure Sudoers Timestamp Type
   - [os_airdrop_disable](#osairdropdisable) — Disable AirDrop
   - [os_nfsd_disable](#osnfsddisable) — Disable Network File System Service
   - [os_httpd_disable](#oshttpddisable) — Disable the Built-in Web Server
   - [os_gatekeeper_enable](#osgatekeeperenable) — Enable Gatekeeper
   - [os_safari_show_full_website_address_enable](#ossafarishowfullwebsiteaddressenable) — Ensure Show Full Website Address in Safari Is Enabled
   - [os_mobile_file_integrity_enable](#osmobilefileintegrityenable) — Enable Apple Mobile File Integrity
   - [os_sip_enable](#ossipenable) — Ensure System Integrity Protection is Enabled
   - [os_terminal_secure_keyboard_enable](#osterminalsecurekeyboardenable) — Ensure Secure Keyboard Entry Terminal.app is Enabled
   - [os_unlock_active_user_session_disable](#osunlockactiveusersessiondisable) — Disable Login to Other User's Active and Locked Sessions
   - [os_time_server_enabled](#ostimeserverenabled) — Enable Time Synchronization Daemon
   - [os_sudo_timeout_configure](#ossudotimeoutconfigure) — Configure Sudo Timeout Period to 0
   - [os_software_update_deferral](#ossoftwareupdatedeferral) — Ensure Software Update Deferment Is Less Than or Equal to 30 Days
   - [os_system_wide_applications_configure](#ossystemwideapplicationsconfigure) — Ensure Appropriate Permissions Are Enabled for System Wide Applications
   - [os_safari_show_status_bar_enabled](#ossafarishowstatusbarenabled) — Ensure Show Safari shows the Status Bar is Enabled
   - [os_install_log_retention_configure](#osinstalllogretentionconfigure) — Configure Install.log Retention to 365
   - [os_home_folders_secure](#oshomefolderssecure) — Secure User's Home Folders
   - [os_on_device_dictation_enforce](#osondevicedictationenforce) — Enforce On Device Dictation
   - [os_safari_prevent_cross-site_tracking_enable](#ossafaripreventcross-sitetrackingenable) — Ensure Prevent Cross-site Tracking in Safari Is Enabled
2. [Password Policy](#password-policy) (5 rules)
   - [pwpolicy_max_lifetime_enforce](#pwpolicymaxlifetimeenforce) — Restrict Maximum Password Lifetime to 365 Days
   - [pwpolicy_account_lockout_timeout_enforce](#pwpolicyaccountlockouttimeoutenforce) — Set Account Lockout Time to 15 Minutes
   - [pwpolicy_history_enforce](#pwpolicyhistoryenforce) — Prohibit Password Reuse for a Minimum of 15 Generations
   - [pwpolicy_account_lockout_enforce](#pwpolicyaccountlockoutenforce) — Limit Consecutive Failed Login Attempts to 5
   - [pwpolicy_minimum_length_enforce](#pwpolicyminimumlengthenforce) — Require a Minimum Password Length of 15 Characters
3. [Audit](#audit) (14 rules)
   - [audit_folder_group_configure](#auditfoldergroupconfigure) — Configure Audit Log Folders Group to Wheel
   - [audit_files_mode_configure](#auditfilesmodeconfigure) — Configure Audit Log Files to Mode 440 or Less Permissive
   - [audit_retention_configure](#auditretentionconfigure) — Configure Audit Retention to 60d OR 5G
   - [audit_files_owner_configure](#auditfilesownerconfigure) — Configure Audit Log Files to be Owned by Root
   - [audit_auditd_enabled](#auditauditdenabled) — Enable Security Auditing
   - [audit_control_owner_configure](#auditcontrolownerconfigure) — Configure Audit_Control Owner to Root
   - [audit_folder_owner_configure](#auditfolderownerconfigure) — Configure Audit Log Folders to be Owned by Root
   - [audit_control_acls_configure](#auditcontrolaclsconfigure) — Configure Audit_Control to Not Contain Access Control Lists
   - [audit_folders_mode_configure](#auditfoldersmodeconfigure) — Configure Audit Log Folders to Mode 700 or Less Permissive
   - [audit_acls_folders_configure](#auditaclsfoldersconfigure) — Configure Audit Log Folder to Not Contain Access Control Lists
   - [audit_files_group_configure](#auditfilesgroupconfigure) — Configure Audit Log Files Group to Wheel
   - [audit_control_mode_configure](#auditcontrolmodeconfigure) — Configure Audit_Control Owner to Mode 440 or Less Permissive
   - [audit_acls_files_configure](#auditaclsfilesconfigure) — Configure Audit Log Files to Not Contain Access Control Lists
   - [audit_control_group_configure](#auditcontrolgroupconfigure) — Configure Audit_Control Group to Wheel
4. [System Settings](#system-settings) (39 rules)
   - [system_settings_location_services_menu_enforce](#systemsettingslocationservicesmenuenforce) — Ensure Location Services Is In the Menu Bar
   - [system_settings_guest_access_smb_disable](#systemsettingsguestaccesssmbdisable) — Disable Guest Access to Shared SMB Folders
   - [system_settings_screensaver_ask_for_password_delay_enforce](#systemsettingsscreensaveraskforpassworddelayenforce) — Enforce Session Lock After Screen Saver is Started
   - [system_settings_time_machine_encrypted_configure](#systemsettingstimemachineencryptedconfigure) — Ensure Time Machine Volumes are Encrypted
   - [system_settings_install_macos_updates_enforce](#systemsettingsinstallmacosupdatesenforce) — Enforce macOS Updates are Automatically Installed
   - [system_settings_system_wide_preferences_configure](#systemsettingssystemwidepreferencesconfigure) — Require Administrator Password to Modify System-Wide Preferences
   - [system_settings_printer_sharing_disable](#systemsettingsprintersharingdisable) — Disable Printer Sharing
   - [system_settings_improve_search_disable](#systemsettingsimprovesearchdisable) — Disable Improve Search Information to Apple
   - [system_settings_personalized_advertising_disable](#systemsettingspersonalizedadvertisingdisable) — Disable Personalized Advertising
   - [system_settings_guest_account_disable](#systemsettingsguestaccountdisable) — Disable the Guest Account
   - [system_settings_smbd_disable](#systemsettingssmbddisable) — Disable Server Message Block Sharing
   - [system_settings_password_hints_disable](#systemsettingspasswordhintsdisable) — Disable Password Hints
   - [system_settings_screen_sharing_disable](#systemsettingsscreensharingdisable) — Disable Screen Sharing and Apple Remote Desktop
   - [system_settings_remote_management_disable](#systemsettingsremotemanagementdisable) — Disable Remote Management
   - [system_settings_screensaver_timeout_enforce](#systemsettingsscreensavertimeoutenforce) — Enforce Screen Saver Timeout
   - [system_settings_loginwindow_prompt_username_password_enforce](#systemsettingsloginwindowpromptusernamepasswordenforce) — Configure Login Window to Prompt for Username and Password
   - [system_settings_software_update_download_enforce](#systemsettingssoftwareupdatedownloadenforce) — Enforce Software Update Downloads Updates Automatically
   - [system_settings_siri_disable](#systemsettingssiridisable) — Disable Siri
   - [system_settings_ssh_disable](#systemsettingssshdisable) — Disable SSH Server for Remote Access Sessions
   - [system_settings_internet_sharing_disable](#systemsettingsinternetsharingdisable) — Disable Internet Sharing
   - [system_settings_external_intelligence_disable](#systemsettingsexternalintelligencedisable) — Disable External Intelligence Integrations
   - [system_settings_filevault_enforce](#systemsettingsfilevaultenforce) — Enforce FileVault
   - [system_settings_softwareupdate_current](#systemsettingssoftwareupdatecurrent) — Ensure Software Update is Updated and Current
   - [system_settings_loginwindow_loginwindowtext_enable](#systemsettingsloginwindowloginwindowtextenable) — Configure Login Window to Show A Custom Message
   - [system_settings_external_intelligence_sign_in_disable](#systemsettingsexternalintelligencesignindisable) — Disable External Intelligence Integration Sign In
   - [system_settings_firewall_enable](#systemsettingsfirewallenable) — Enable macOS Application Firewall
   - [system_settings_improve_siri_dictation_disable](#systemsettingsimprovesiridictationdisable) — Disable Improve Siri and Dictation Information to Apple
   - [system_settings_bluetooth_sharing_disable](#systemsettingsbluetoothsharingdisable) — Disable Bluetooth Sharing
   - [system_settings_diagnostics_reports_disable](#systemsettingsdiagnosticsreportsdisable) — Disable Sending Diagnostic and Usage Data to Apple
   - [system_settings_critical_update_install_enforce](#systemsettingscriticalupdateinstallenforce) — Enforce Critical Security Updates to be Installed
   - [system_settings_screensaver_password_enforce](#systemsettingsscreensaverpasswordenforce) — Enforce Screen Saver Password
   - [system_settings_time_server_configure](#systemsettingstimeserverconfigure) — Configure macOS to Use an Authorized Time Server
   - [system_settings_time_server_enforce](#systemsettingstimeserverenforce) — Enforce macOS Time Synchronization
   - [system_settings_wake_network_access_disable](#systemsettingswakenetworkaccessdisable) — Ensure Wake for Network Access Is Disabled
   - [system_settings_automatic_login_disable](#systemsettingsautomaticlogindisable) — Disable Unattended or Automatic Logon to the System
   - [system_settings_airplay_receiver_disable](#systemsettingsairplayreceiverdisable) — Disable Airplay Receiver
   - [system_settings_improve_assistive_voice_disable](#systemsettingsimproveassistivevoicedisable) — Disable Sending Audio Recordings and Transcripts to Apple
   - [system_settings_firewall_stealth_mode_enable](#systemsettingsfirewallstealthmodeenable) — Enable Firewall Stealth Mode
   - [system_settings_rae_disable](#systemsettingsraedisable) — Disable Remote Apple Events

## Summary

| Section | Rules |
|---------|------:|
| Operating System | 36 |
| Password Policy | 5 |
| Audit | 14 |
| System Settings | 39 |
| **Total** | **94** |

## Authors

| Name | Organization |
|------|-------------|
| Bob Gendler | National Institute of Standards and Technology |
| Dan Brodjieski | National Aeronautics and Space Administration |
| Allen Golbig | Jamf |
| Edward Byrd | Center for Internet Security |

---

## Operating System

### Ensure Warn When Visiting A Fraudulent Website in Safari Is Enabled

`os_safari_warn_fraudulent_website_enable`

Warn when visiting a fraudulent website _MUST_ be enabled in Safari.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - WarnAboutFraudulentWebsites: true
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.3 (level 1) &nbsp;| **CIS Controls v8:** 9.1, 9.3 &nbsp;| **CCE:** CCE-95289-5

</details>


### Disable Root Login

`os_root_disable`

To assure individual accountability and prevent unauthorized access, logging in as root at the login window _MUST_ be disabled.

The macOS system _MUST_ require individuals to be authenticated with an individual authenticator prior to using a group authenticator, and administrator users _MUST_ never log in directly as root.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/dscl . -create /Users/root UserShell /usr/bin/false
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-2, IA-2(5) &nbsp;| **800-171r3:** 03.05.01 &nbsp;| **CCI:** CCI-000764, CCI-000770, CCI-001813, CCI-004045 &nbsp;| **SRG:** SRG-OS-000364-GPOS-00151, SRG-OS-000109-GPOS-00056, SRG-OS-000104-GPOS-00051 &nbsp;| **DISA STIG:** APPL-26-000100 &nbsp;| **CMMC:** IA.L1-3.5.1, IA.L1-3.5.2 &nbsp;| **CIS Benchmark:** 5.6 (level 1) &nbsp;| **CIS Controls v8:** 5.4 &nbsp;| **CCE:** CCE-95282-0

</details>


### Disable Power Nap

`os_power_nap_disable`

Power Nap _MUST_ be disabled.

NOTE: Power Nap allows your Mac to perform actions while a Mac is asleep. This can interfere with USB power and may cause devices such as smartcards to stop functioning until a reboot and must therefore be disabled on all applicable systems.

The following Macs support Power Nap:

* MacBook (Early 2015 and later)
* MacBook Air (Late 2010 and later)
* MacBook Pro (all models with Retina display)
* Mac mini (Late 2012 and later)
* iMac (Late 2012 and later)
* Mac Pro (Late 2013 and later)


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/pmset -a powernap 0
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.04.06 &nbsp;| **CMMC:** CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.10.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95260-6

</details>


### Disable Apple Intelligence Notes Transcription

`os_notes_transcription_disable`

Apple Intelligence features such as Notes Transcription that use off device AI _MUST_ be disabled.

<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowNotesTranscription: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, AC-20(1), CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381, CCI-001774 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.4 (level 1) &nbsp;| **CCE:** CCE-95238-2

</details>


### Must Use an Approved Antivirus Program

`os_anti_virus_installed`

An approved antivirus product _MUST_ be installed and configured to run.

Malicious software can establish a base on individual desktops and servers. Employing an automated mechanism to detect this type of software will aid in elimination of the software from the operating system.'


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/launchctl load -w /Library/Apple/System/Library/LaunchDaemons/com.apple.XProtect.daemon.scan.plist
/bin/launchctl load -w /Library/Apple/System/Library/LaunchDaemons/com.apple.XprotectFramework.PluginService.plist
```

</details>

<details>
<summary><strong>References</strong></summary>

**CCI:** CCI-000366 &nbsp;| **CIS Benchmark:** 5.10 (level 1) &nbsp;| **CIS Controls v8:** 10.5, 10.1, 10.2 &nbsp;| **CCE:** CCE-95158-2

</details>


### Ensure No World Writable Files Exist in the System Folder

`os_world_writable_system_folder_configure`

Folders in /System/Volumes/Data/System _MUST_ not be world-writable.


<details>
<summary><strong>Remediation</strong></summary>

```bash
IFS=$'\n'
for sysPermissions in $( /usr/bin/find /System/Volumes/Data/System -type d -perm -2 | /usr/bin/grep -vE "downloadDir|locks" ); do
  /bin/chmod -R o-w "$sysPermissions"
done
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 5.1.6 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95333-1

</details>


### Disable Apple Intelligence Mail Summary

`os_mail_summary_disable`

Apple Intelligence features such as Apple Mail Summary that use off device AI _MUST_ be disabled.

<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowMailSummary: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, AC-20(1), CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.3 (level 1) &nbsp;| **CCE:** CCE-95223-4

</details>


### Disable Automatic Opening of Safe Files in Safari

`os_safari_open_safe_downloads_disable`

Open "safe" files after downloading _MUST_ be disabled in Safari.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AutoOpenSafeDownloads: false
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.1 (level 1) &nbsp;| **CIS Controls v8:** 9.1, 9.6 &nbsp;| **CCE:** CCE-95284-6

</details>


### Ensure Advertising Privacy Protection in Safari Is Enabled

`os_safari_advertising_privacy_protection_enable`

Allow privacy-preserving measurement of ad effectiveness _MUST_ be enabled in Safari.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - WebKitPreferences.privateClickMeasurementEnabled: true
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.6 (level 1) &nbsp;| **CIS Controls v8:** 9.1 &nbsp;| **CCE:** CCE-95283-8

</details>


### Enable Authenticated Root

`os_authenticated_root_enable`

Authenticated Root _MUST_ be enabled.

When Authenticated Root is enabled the macOS is booted from a signed volume that is cryptographically protected to prevent tampering with the system volume.

NOTE: Authenticated Root is enabled by default on macOS systems.

WARNING: If more than one partition with macOS is detected, the csrutil command will hang awaiting input.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/csrutil authenticated-root enable
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, CM-5, SC-34, SI-7(6), SI-7, MA-4(1) &nbsp;| **800-171r3:** 03.01.02, 03.04.05 &nbsp;| **CCI:** CCI-000213 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048 &nbsp;| **DISA STIG:** APPL-26-005070 &nbsp;| **CMMC:** AC.L1-3.1.1, CM.L2-3.4.5, SC.L2-3.13.11 &nbsp;| **CIS Benchmark:** 5.1.4 (level 1) &nbsp;| **CIS Controls v8:** 3.6, 3.11 &nbsp;| **CCE:** CCE-95164-0

</details>


### Enforce Installation of XProtect Remediator and Gatekeeper Updates Automatically

`os_config_data_install_enforce`

Software Update _MUST_ be configured to update XProtect Remediator and Gatekeeper automatically.

This setting enforces definition updates for XProtect Remediator and Gatekeeper; with this setting in place, new malware and adware that Apple has added to the list of malware or untrusted software will not execute. These updates do not require the computer to be restarted.

link:https://support.apple.com/en-us/HT207005[]

NOTE: Software update will automatically update XProtect Remediator and Gatekeeper by default in the macOS.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - ConfigDataInstall: true
  PayloadType: com.apple.SoftwareUpdate

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** SI-3, SI-2(5) &nbsp;| **800-171r3:** 03.14.02 &nbsp;| **CCI:** CCI-000366 &nbsp;| **SRG:** SRG-OS-000480-GPOS-00227 &nbsp;| **DISA STIG:** APPL-26-005130 &nbsp;| **CMMC:** SI.L1-3.14.1, SI.L1-3.14.2, SI.L1-3.14.4 &nbsp;| **CIS Benchmark:** 1.5 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4, 7.7 &nbsp;| **CCE:** CCE-95176-4

</details>


### Disable Apple Intelligence Notes Transcription Summary

`os_notes_transcription_summary_disable`

Apple Intelligence features such as Notes Transcription Summary that use off device AI _MUST_ be disabled.

<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowNotesTranscriptionSummary: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, AC-20(1), CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381, CCI-001774 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.4 (level 1) &nbsp;| **CCE:** CCE-95239-0

</details>


### Remove Guest Folder if Present

`os_guest_folder_removed`

The guest folder _MUST_ be deleted if present.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/rm -Rf /Users/Guest
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 5.9 (level 1) &nbsp;| **CIS Controls v8:** 4.1 &nbsp;| **CCE:** CCE-95198-8

</details>


### Enforce Software Update App Update Updates Automatically

`os_software_update_app_update_enforce`

Software Update _MUST_ be configured to enforce automatic updates of App Updates is enabled.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AutomaticallyInstallAppUpdates: true
  PayloadType: com.apple.SoftwareUpdate

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 1.4 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4 &nbsp;| **CCE:** CCE-95402-4

</details>


### Remove Password Hint From User Accounts

`os_password_hint_remove`

User accounts _MUST_ not contain password hints.


<details>
<summary><strong>Remediation</strong></summary>

```bash
for u in $(/usr/bin/dscl . -list /Users UniqueID | /usr/bin/awk '$2 > 500 {print $1}'); do
  /usr/bin/dscl . -delete /Users/$u hint
done
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-6 &nbsp;| **800-171r3:** 03.05.11 &nbsp;| **CCI:** CCI-000206 &nbsp;| **SRG:** SRG-OS-000079-GPOS-00047 &nbsp;| **DISA STIG:** APPL-26-003014 &nbsp;| **CMMC:** IA.L2-3.5.11 &nbsp;| **CIS Benchmark:** 2.12.1 (level 1) &nbsp;| **CIS Controls v8:** 5.2 &nbsp;| **CCE:** CCE-95250-7

</details>


### Configure Sudo To Log Events

`os_sudo_log_enforce`

Sudo _MUST_ be configured to log privilege escalation.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/find /etc/sudoers* -type f -exec sed -i '' '/^Defaults[[:blank:]]*\!log_allowed/s/^/# /' '{}' \;
/bin/echo "Defaults log_allowed" >> /etc/sudoers.d/mscp
```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
config_file: sudoers
configuration_key: Defaults
configuration_value: log_allowed
declarationtype: com.apple.configuration.services.configuration-files
service: com.apple.sudo

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-6(9) &nbsp;| **800-171r3:** 03.01.07 &nbsp;| **CCI:** CCI-000172 &nbsp;| **SRG:** SRG-OS-000064-GPOS-00033 &nbsp;| **DISA STIG:** APPL-26-000190 &nbsp;| **CMMC:** AU.L2-3.3.3, AU.L2-3.3.6, SI.L2-3.14.3 &nbsp;| **CIS Benchmark:** 5.11 (level 1) &nbsp;| **CCE:** CCE-95316-6

</details>


### Disable Apple Intelligence Writing Tools

`os_writing_tools_disable`

Apple Intelligence features such as writing tools that use off device AI _MUST_ be disabled.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowWritingTools: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, AC-20(1), CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381, CCI-001774 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-005160 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.2 (level 1) &nbsp;| **CCE:** CCE-95334-9

</details>


### Configure Sudoers Timestamp Type

`os_sudoers_timestamp_type_configure`

The file /etc/sudoers _MUST_ be configured to not include a timestamp_type of global or ppid and be configured for timestamp record types of tty.

This rule ensures that the "sudo" command will prompt for the administrator's password at least once in each newly opened terminal window. This prevents a malicious user from taking advantage of an unlocked computer or an abandoned logon session by bypassing the normal password prompt requirement.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/find /etc/sudoers* -type f -exec sed -i '' '/timestamp_type/d; /!tty_tickets/d' '{}' \;
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-5(1), IA-11 &nbsp;| **800-171r3:** 03.05.01 &nbsp;| **CCI:** CCI-002038 &nbsp;| **SRG:** SRG-OS-000373-GPOS-00157, SRG-OS-000373-GPOS-00156 &nbsp;| **DISA STIG:** APPL-26-004060 &nbsp;| **CIS Benchmark:** 5.5 (level 1) &nbsp;| **CIS Controls v8:** 4.3 &nbsp;| **CCE:** CCE-95318-2

</details>


### Disable AirDrop

`os_airdrop_disable`

AirDrop _MUST_ be disabled to prevent file transfers to or from unauthorized devices.
AirDrop allows users to share and receive files from other nearby Apple devices.

<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowAirDrop: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-20, CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.01.02, 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000213, CCI-000381, CCI-001443 &nbsp;| **SRG:** SRG-OS-000300-GPOS-00118, SRG-OS-000080-GPOS-00048, SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002009 &nbsp;| **CMMC:** AC.L1-3.1.1, AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.1.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8, 6.7 &nbsp;| **CCE:** CCE-95156-6

</details>


### Disable Network File System Service

`os_nfsd_disable`

Support for Network File Systems (NFS) services is non-essential and, therefore, _MUST_ be disabled.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/launchctl disable system/com.apple.nfsd
/bin/rm -rf /etc/exports
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000213 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048 &nbsp;| **DISA STIG:** APPL-26-002003 &nbsp;| **CMMC:** AC.L1-3.1.1 &nbsp;| **CIS Benchmark:** 4.3 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95235-8

</details>


### Disable the Built-in Web Server

`os_httpd_disable`

The built-in web server which is managed by launchd is a non-essential service built into macOS and _MUST_ be disabled and not running.

NOTE: The built in web server service is disabled at startup by default macOS.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/apachectl stop 2>/dev/null
/bin/launchctl disable system/org.apache.httpd
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000213 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048 &nbsp;| **DISA STIG:** APPL-26-002008 &nbsp;| **CMMC:** AC.L1-3.1.1 &nbsp;| **CIS Benchmark:** 4.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95204-4

</details>


### Enable Gatekeeper

`os_gatekeeper_enable`

Gatekeeper _MUST_ be enabled.

Gatekeeper is a security feature that ensures that applications are digitally signed by an Apple-issued certificate before they are permitted to run. Digital signatures allow the macOS host to verify that the application has not been modified by a malicious third party.

Administrator users will still have the option to override these settings on a case-by-case basis.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - EnableAssessment: true
  PayloadType: com.apple.systempolicy.control

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-14, CM-5, SI-7(1), SI-7(15), SI-3 &nbsp;| **800-171r3:** 03.14.02 &nbsp;| **CCI:** CCI-001749, CCI-003992 &nbsp;| **SRG:** SRG-OS-000366-GPOS-00153, SRG-OS-000480-GPOS-00228 &nbsp;| **DISA STIG:** APPL-26-002064 &nbsp;| **CMMC:** CM.L2-3.4.5, SI.L1-3.14.1, SI.L1-3.14.2, SI.L1-3.14.4 &nbsp;| **CIS Benchmark:** 2.6.5 (level 1) &nbsp;| **CIS Controls v8:** 10.1, 10.2, 10.5 &nbsp;| **CCE:** CCE-95195-4

</details>


### Ensure Show Full Website Address in Safari Is Enabled

`os_safari_show_full_website_address_enable`

Show full website address _MUST_ be enabled in Safari.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - ShowFullURLInSmartSearchField: true
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.7 (level 1) &nbsp;| **CIS Controls v8:** 9.1 &nbsp;| **CCE:** CCE-95287-9

</details>


### Enable Apple Mobile File Integrity

`os_mobile_file_integrity_enable`

Mobile file integrity _MUST_ be enabled.

<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/nvram boot-args=""
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 5.1.3 (level 1) &nbsp;| **CIS Controls v8:** 2.3, 2.6 &nbsp;| **CCE:** CCE-95231-7

</details>


### Ensure System Integrity Protection is Enabled

`os_sip_enable`

System Integrity Protection (SIP) _MUST_ be enabled.

SIP is vital to protecting the integrity of the system as it prevents malicious users and software from making unauthorized and/or unintended modifications to protected files and folders; ensures the presence of an audit record generation capability for defined auditable events for all operating system components; protects audit tools from unauthorized access, modification, and deletion; restricts the root user account and limits the actions that the root user can perform on protected parts of the macOS; and prevents non-privileged users from granting other users direct access to the contents of their home directories and folders.

NOTE: SIP is enabled by default in macOS.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/csrutil enable
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AU-9, AU-9(3), CM-5, CM-5(6), SC-4, SI-2, SI-7 &nbsp;| **800-171r3:** 03.01.02, 03.03.08, 03.04.05, 03.13.04 &nbsp;| **CCI:** CCI-000154, CCI-000158, CCI-000169, CCI-001493, CCI-001494, CCI-001495, CCI-001499, CCI-001875, CCI-001876, CCI-001877, CCI-001878, CCI-001879, CCI-001880, CCI-001881, CCI-001882, CCI-001090, CCI-001496 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000062-GPOS-00031, SRG-OS-000051-GPOS-00024, SRG-OS-000054-GPOS-00025, SRG-OS-000278-GPOS-00108, SRG-OS-000080-GPOS-00048, SRG-OS-000059-GPOS-00029, SRG-OS-000138-GPOS-00069, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000259-GPOS-00100, SRG-OS-000122-GPOS-00063, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-005001 &nbsp;| **CMMC:** AC.L1-3.1.1, AU.L2-3.3.8, CM.L2-3.4.5, SC.L2-3.13.4, SI.L1-3.14.1, SI.L1-3.14.4 &nbsp;| **CIS Benchmark:** 5.1.2 (level 1) &nbsp;| **CIS Controls v8:** 2.3, 2.6, 10.5 &nbsp;| **CCE:** CCE-95298-6

</details>


### Ensure Secure Keyboard Entry Terminal.app is Enabled

`os_terminal_secure_keyboard_enable`

Secure keyboard entry _MUST_ be enabled in Terminal.app.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - SecureKeyboardEntry: true
  PayloadType: com.apple.Terminal

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.4.1 (level 1) &nbsp;| **CIS Controls v8:** 4.8 &nbsp;| **CCE:** CCE-95321-6

</details>


### Disable Login to Other User's Active and Locked Sessions

`os_unlock_active_user_session_disable`

The ability to log in to another user's active or locked session _MUST_ be disabled.

macOS has a privilege that can be granted to any user that will allow that user to unlock active user's sessions. Disabling the admins and/or user's ability to log into another user's active and locked session prevents unauthorized persons from viewing potentially sensitive and/or personal information.

NOTE: Configuring this setting will change the user experience and disable TouchID from unlocking the screensaver. A configuration profile will be generated to include the setting that restores the expected behavior. You can also apply the settings using `/usr/bin/sudo /usr/bin/defaults write /Library/Preferences/com.apple.loginwindow screenUnlockMode -int 1`.

WARNING: Do not apply this rule if your organization uses smartcards and Platform Single Sign-On (PSSO).


<details>
<summary><strong>Remediation</strong></summary>

```bash
SS_RULE=$(/usr/bin/security -q authorizationdb read system.login.screensaver 2>&1 | /usr/bin/xmllint --xpath "//dict/key[.='rule']/following-sibling::array[1]/string/text()" -)

if [[ "$SS_RULE" == *psso* ]]; then
    /usr/bin/security -q authorizationdb read psso-screensaver > "/tmp/psso-screensaver-mscp.plist"
    /usr/bin/sed -i.bak 's/<string>authenticate-session-owner-or-admin<\/string>/<string>authenticate-session-owner<\/string>/' /tmp/psso-screensaver-mscp.plist
    /usr/bin/security -q authorizationdb write psso-screensaver-mscp < /tmp/psso-screensaver-mscp.plist
    /usr/bin/security -q authorizationdb write system.login.screensaver psso-screensaver-mscp 2>&1
else
    /usr/bin/security -q authorizationdb write system.login.screensaver "authenticate-session-owner" 2>&1
fi
```

</details>

<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - screenUnlockMode: 1
  PayloadType: com.apple.loginwindow

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-2, IA-2(5) &nbsp;| **800-171r3:** 03.05.01 &nbsp;| **CCI:** CCI-000764, CCI-000770, CCI-004045 &nbsp;| **SRG:** SRG-OS-000109-GPOS-00056, SRG-OS-000104-GPOS-00051 &nbsp;| **DISA STIG:** APPL-26-000090 &nbsp;| **CMMC:** IA.L1-3.5.1, IA.L1-3.5.2 &nbsp;| **CIS Benchmark:** 5.7 (level 1) &nbsp;| **CIS Controls v8:** 4.3 &nbsp;| **CCE:** CCE-95328-1

</details>


### Enable Time Synchronization Daemon

`os_time_server_enabled`

The macOS time synchronization daemon (timed) _MUST_ be enabled for proper time synchronization to an authorized time server.

NOTE: The time synchronization daemon is enabled by default on macOS.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/launchctl load -w /System/Library/LaunchDaemons/com.apple.timed.plist
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-12(1), SC-45(1) &nbsp;| **800-171r3:** 03.03.07 &nbsp;| **CCI:** CCI-002046, CCI-001891, CCI-004923, CCI-004926, CCI-004922 &nbsp;| **SRG:** SRG-OS-000355-GPOS-00143, SRG-OS-000356-GPOS-00144, SRG-OS-000785-GPOS-00250 &nbsp;| **DISA STIG:** APPL-26-000180 &nbsp;| **CMMC:** AU.L2-3.3.7 &nbsp;| **CIS Benchmark:** 2.3.2.2 (level 1) &nbsp;| **CIS Controls v8:** 8.4 &nbsp;| **CCE:** CCE-95325-7

</details>


### Configure Sudo Timeout Period to 0

`os_sudo_timeout_configure`

The file /etc/sudoers _MUST_ include a timestamp_timeout of 0.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/find /etc/sudoers* -type f -exec sed -i '' '/timestamp_timeout/d' '{}' \;
/bin/echo "Defaults timestamp_timeout=0" >> /etc/sudoers.d/mscp
```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
config_file: sudoers
configuration_key: Defaults timestamp_timeout=
configuration_value: 0
declarationtype: com.apple.configuration.services.configuration-files
service: com.apple.sudo

```

</details>

<details>
<summary><strong>References</strong></summary>

**CCI:** CCI-002038 &nbsp;| **SRG:** SRG-OS-000373-GPOS-00156 &nbsp;| **DISA STIG:** APPL-26-004022 &nbsp;| **CIS Benchmark:** 5.4 (level 1) &nbsp;| **CIS Controls v8:** 4.3 &nbsp;| **CCE:** CCE-95317-4

</details>


### Ensure Software Update Deferment Is Less Than or Equal to 30 Days

`os_software_update_deferral`

Software updates _MUST_ be deferred for 30 days or less.

If you need to defer software updates, create a Restrictions profile using the com.apple.applicationaccess domain and the key enforcedSoftwareUpdateDelay.


<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 1.6 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4 &nbsp;| **CCE:** CCE-95303-4

</details>


### Ensure Appropriate Permissions Are Enabled for System Wide Applications

`os_system_wide_applications_configure`

Applications in the System Applications Directory (/Applications) _MUST_ not be world-writable.


<details>
<summary><strong>Remediation</strong></summary>

```bash
IFS=$'\n'
for apps in $( /usr/bin/find /Applications -iname "*\.app" -type d -perm -2 ); do
  /bin/chmod -R o-w "$apps"
done
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 5.1.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95320-8

</details>


### Ensure Show Safari shows the Status Bar is Enabled

`os_safari_show_status_bar_enabled`

Safari _MUST_ be configured to show the status bar.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - ShowOverlayStatusBar: true
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.10 (level 1) &nbsp;| **CIS Controls v8:** 9.1 &nbsp;| **CCE:** CCE-95288-7

</details>


### Configure Install.log Retention to 365

`os_install_log_retention_configure`

The install.log _MUST_ be configured to require records be kept for a organizational defined value before deletion, unless the system uses a central audit record storage facility.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/sed -i '' "s/\* file \/var\/log\/install.log.*/\* file \/var\/log\/install.log format='\$\(\(Time\)\(JZ\)\) \$Host \$\(Sender\)\[\$\(PID\\)\]: \$Message' rotate=utc compress file_max=50M size_only ttl=365/g" /etc/asl/com.apple.install
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-11, AU-4 &nbsp;| **800-171r3:** 03.03.03 &nbsp;| **CCI:** CCI-001849 &nbsp;| **SRG:** SRG-OS-000341-GPOS-00132 &nbsp;| **DISA STIG:** APPL-26-004050 &nbsp;| **CMMC:** AU.L2-3.3.1 &nbsp;| **CIS Benchmark:** 3.3 (level 1) &nbsp;| **CIS Controls v8:** 8.1, 8.3 &nbsp;| **CCE:** CCE-95211-9

</details>


### Secure User's Home Folders

`os_home_folders_secure`

The system _MUST_ be configured to prevent access to other user's home folders.

The default behavior of macOS is to allow all valid users access to the top level of every other user's home folder while restricting access only to the Apple default folders within.


<details>
<summary><strong>Remediation</strong></summary>

```bash
IFS=$'\n'
for userDirs in $( /usr/bin/find /System/Volumes/Data/Users -mindepth 1 -maxdepth 1 -type d ! \( -perm 700 -o -perm 711 \) | /usr/bin/grep -v "Shared" | /usr/bin/grep -v "Guest" ); do
  /bin/chmod og-rwx "$userDirs"
done
unset IFS
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-6 &nbsp;| **800-171r3:** 03.01.05 &nbsp;| **CCI:** CCI-000366 &nbsp;| **SRG:** SRG-OS-000480-GPOS-00230, SRG-OS-000480-GPOS-00228 &nbsp;| **DISA STIG:** APPL-26-002068 &nbsp;| **CMMC:** AC.L1-3.1.1, AC.L1-3.1.2, AC.L2-3.1.5, AC.L2-3.1.6 &nbsp;| **CIS Benchmark:** 5.1.1 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95203-6

</details>


### Enforce On Device Dictation

`os_on_device_dictation_enforce`

The system _MUST_ be configured for on device dictation.

By enforcing on device dictation this will mitigate the risk of unwanted data being sent to Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - forceOnDeviceOnlyDictation: true
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002220 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.18.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95247-3

</details>


### Ensure Prevent Cross-site Tracking in Safari Is Enabled

`os_safari_prevent_cross-site_tracking_enable`

Prevent cross-site tracking _MUST_ be enabled in Safari.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - WebKitPreferences.storageBlockingPolicy: 1
  - WebKitStorageBlockingPolicy: 1
  - BlockStoragePolicy: 2
  PayloadType: com.apple.Safari

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 6.3.4 (level 1) &nbsp;| **CIS Controls v8:** 9.1, 9.3 &nbsp;| **CCE:** CCE-95285-3

</details>


---

## Password Policy

> Password policy settings including complexity, length, and expiration requirements.

### Restrict Maximum Password Lifetime to 365 Days

`pwpolicy_max_lifetime_enforce`

The system _MUST_ be configured to enforce a maximum password lifetime limit of 365 days.

This rule ensures that users are forced to change their passwords frequently enough to prevent malicious users from gaining and maintaining access to the system.

NOTE: To comply with Executive Order 14028, “Improving the Nation's Cybersecurity”, OMB M-22-09, “Moving the U.S. Government Toward Zero Trust Cybersecurity Principles”, and NIST SP-800-63b, “Digital Identity Guidelines: Authentication and Lifecycle Management” federal, military, and intelligence communities must adopt the following configuration settings. Password policies must not require the use of complexity policies such as upper characters, lower characters, or special characters. Password policies must also not require the use of regular rotation. Password policies should define a minimum length. Multifactor authentication should be used where ever possible.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - maxPINAgeInDays: 365
  PayloadType: com.apple.mobiledevice.passwordpolicy

```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
ddm_key: MaximumPasscodeAgeInDays
ddm_value: 365
declarationtype: com.apple.configuration.passcode.settings

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-5 &nbsp;| **800-171r3:** 03.05.12 &nbsp;| **CCI:** CCI-000199, CCI-004066 &nbsp;| **SRG:** SRG-OS-000076-GPOS-00044, SRG-OS-000775-GPOS-00230 &nbsp;| **DISA STIG:** APPL-26-003008 &nbsp;| **CMMC:** IA.L2-3.5.8, IA.L2-3.5.9 &nbsp;| **CIS Benchmark:** 5.2.7 (level 1) &nbsp;| **CIS Controls v8:** 5.3 &nbsp;| **CCE:** CCE-95345-5

</details>


### Set Account Lockout Time to 15 Minutes

`pwpolicy_account_lockout_timeout_enforce`

The macOS _MUST_ be configured to enforce a lockout time period of at least 15 minutes when the maximum number of failed logon attempts is reached.

This rule protects against malicious users attempting to gain access to the system via brute-force hacking methods.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - minutesUntilFailedLoginReset: 15
  PayloadType: com.apple.mobiledevice.passwordpolicy

```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
ddm_key: MaximumGracePeriodInMinutes
ddm_value: 15
declarationtype: com.apple.configuration.passcode.settings

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-7 &nbsp;| **800-171r3:** 03.01.08 &nbsp;| **CCI:** CCI-002238, CCI-000044 &nbsp;| **SRG:** SRG-OS-000329-GPOS-00128, SRG-OS-000021-GPOS-00005 &nbsp;| **DISA STIG:** APPL-26-000060 &nbsp;| **CMMC:** AC.L2-3.1.8 &nbsp;| **CIS Benchmark:** 5.2.1 (level 1) &nbsp;| **CIS Controls v8:** 6.2 &nbsp;| **CCE:** CCE-95338-0

</details>


### Prohibit Password Reuse for a Minimum of 15 Generations

`pwpolicy_history_enforce`

The device _MUST_ be configured to enforce a password history of at least 15 previous passwords when a password is created.

This rule ensures that users are not allowed to re-use a password that was used in any of the 15 previous password generations.

Limiting password reuse protects against malicious users attempting to gain access to the system via brute-force hacking methods.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - pinHistory: 15
  PayloadType: com.apple.mobiledevice.passwordpolicy

```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
ddm_key: PasscodeReuseLimit
ddm_value: 15
declarationtype: com.apple.configuration.passcode.settings

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-5(1) &nbsp;| **800-171r3:** 03.05.07 &nbsp;| **CCI:** CCI-000200 &nbsp;| **SRG:** SRG-OS-000077-GPOS-00045, SRG-OS-000775-GPOS-00230 &nbsp;| **DISA STIG:** AIOS-26-006950 &nbsp;| **CMMC:** IA.L2-3.5.7, IA.L2-3.5.8, IA.L2-3.5.9 &nbsp;| **CIS Benchmark:** 5.2.8 (level 1) &nbsp;| **CIS Controls v8:** 5.2 &nbsp;| **CCE:** CCE-95343-0

</details>


### Limit Consecutive Failed Login Attempts to 5

`pwpolicy_account_lockout_enforce`

The system _MUST_ be configured to limit the number of failed login attempts to a maximum of 5. When the maximum number of failed attempts is reached, the system _MUST_ prevent logins for a period of time after.

This rule protects against malicious users attempting to gain access to the system via brute-force hacking methods.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - maxFailedAttempts: 5
  PayloadType: com.apple.mobiledevice.passwordpolicy

```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
ddm_key: MaximumFailedAttempts
ddm_value: 5
declarationtype: com.apple.configuration.passcode.settings

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-7 &nbsp;| **800-171r3:** 03.01.08 &nbsp;| **CCI:** CCI-000044, CCI-002238 &nbsp;| **SRG:** SRG-OS-000329-GPOS-00128, SRG-OS-000021-GPOS-00005 &nbsp;| **DISA STIG:** APPL-26-000022 &nbsp;| **CMMC:** AC.L2-3.1.8 &nbsp;| **CIS Benchmark:** 5.2.1 (level 1) &nbsp;| **CIS Controls v8:** 6.2 &nbsp;| **CCE:** CCE-95337-2

</details>


### Require a Minimum Password Length of 15 Characters

`pwpolicy_minimum_length_enforce`

The macOS _MUST_ be configured to require a minimum of 15 characters be used when a password is created.

This rule enforces password complexity by requiring users to set passwords that are less vulnerable to malicious users.

NOTE: To comply with Executive Order 14028, "Improving the Nation's Cybersecurity", OMB M-22-09, "Moving the U.S. Government Toward Zero Trust Cybersecurity Principles", and NIST SP-800-63b, "Digital Identity Guidelines: Authentication and Lifecycle Management" federal, military, and intelligence communities must adopt the following configuration settings. Password policies must not require the use of complexity policies such as upper characters, lower characters, or special characters. Password policies must also not require the use of regular rotation. Password policies should define a minimum length. Multifactor authentication should be used where ever possible.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - minLength: 15
  PayloadType: com.apple.mobiledevice.passwordpolicy

```

</details>

<details>
<summary><strong>Declarative Management</strong></summary>

```yaml
ddm_key: MinimumLength
ddm_value: 15
declarationtype: com.apple.configuration.passcode.settings

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-5(1) &nbsp;| **800-171r3:** 03.05.07 &nbsp;| **CCI:** CCI-000205, CCI-004066 &nbsp;| **SRG:** SRG-OS-000078-GPOS-00046 &nbsp;| **DISA STIG:** APPL-26-003010 &nbsp;| **CMMC:** IA.L2-3.5.7, IA.L2-3.5.8, IA.L2-3.5.9 &nbsp;| **CIS Benchmark:** 5.2.2 (level 1) &nbsp;| **CIS Controls v8:** 5.2 &nbsp;| **CCE:** CCE-95346-3

</details>


---

## Audit

### Configure Audit Log Folders Group to Wheel

`audit_folder_group_configure`

Audit log files _MUST_ have the group set to wheel.

The audit service _MUST_ be configured to create log files with the correct group ownership to prevent normal users from reading audit logs.

Audit logs contain sensitive data about the system and users. If log files are set to be readable and writable only by system administrators, the risk is mitigated.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/chgrp wheel /var/audit
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001015 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95124-4

</details>


### Configure Audit Log Files to Mode 440 or Less Permissive

`audit_files_mode_configure`

The audit service _MUST_ be configured to create log files that are readable only by the root user and group wheel. To achieve this, audit log files _MUST_ be configured to mode 440 or less permissive; thereby preventing normal users from reading, modifying or deleting audit logs.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod 440 /var/audit/*
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001016 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95113-7

</details>


### Configure Audit Retention to 60d OR 5G

`audit_retention_configure`

The audit service _MUST_ be configured to require records be kept for a organizational defined value before deletion, unless the system uses a central audit record storage facility.

When "expire-after" is set to "60d OR 5G", the audit service will not delete audit logs until the log data criteria is met.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/sed -i.bak 's/^expire-after.*/expire-after:60d OR 5G/' /etc/security/audit_control; /usr/sbin/audit -s
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-11, AU-4 &nbsp;| **800-171r3:** 03.03.03 &nbsp;| **CCI:** CCI-001849 &nbsp;| **SRG:** SRG-OS-000341-GPOS-00132 &nbsp;| **DISA STIG:** APPL-26-001029 &nbsp;| **CMMC:** AU.L2-3.3.1 &nbsp;| **CIS Benchmark:** 3.4 (level 1) &nbsp;| **CIS Controls v8:** 8.1, 8.3 &nbsp;| **CCE:** CCE-95130-1

</details>


### Configure Audit Log Files to be Owned by Root

`audit_files_owner_configure`

Audit log files _MUST_ be owned by root.

The audit service _MUST_ be configured to create log files with the correct ownership to prevent normal users from reading audit logs.

Audit logs contain sensitive data about the system and users. If log files are set to only be readable and writable by system administrators, the risk is mitigated.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/chown -R root /var/audit/*
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001012 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95114-5

</details>


### Enable Security Auditing

`audit_auditd_enabled`

The information system _MUST_ be configured to generate audit records.

Audit records establish what types of events have occurred, when they occurred, and which users were involved. These records aid an organization in their efforts to establish, correlate, and investigate the events leading up to an outage or attack.

The content required to be captured in an audit record varies based on the impact level of an organization's system. Content that may be necessary to satisfy this requirement includes, for example, time stamps, source addresses, destination addresses, user identifiers, event descriptions, success/fail indications, filenames involved, and access or flow control rules invoked.

The information system initiates session audits at system start-up.

NOTE: Security auditing is NOT enabled by default on macOS 14 and later.


<details>
<summary><strong>Remediation</strong></summary>

```bash
if [[ ! -e /etc/security/audit_control ]] && [[ -e /etc/security/audit_control.example ]];then
  /bin/cp /etc/security/audit_control.example /etc/security/audit_control
fi

/bin/launchctl enable system/com.apple.auditd
/bin/launchctl bootstrap system /System/Library/LaunchDaemons/com.apple.auditd.plist
/usr/sbin/audit -i
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-3, AU-3(1), AU-8, AU-12, AU-12(1), AU-12(3), AU-14(1), MA-4(1), CM-5(1) &nbsp;| **800-171r3:** 03.03.02, 03.03.03, 03.03.07 &nbsp;| **CCI:** CCI-000130, CCI-000131, CCI-000132, CCI-000133, CCI-000134, CCI-000135, CCI-000159, CCI-001464, CCI-001487, CCI-001889, CCI-001890, CCI-001914, CCI-002130, CCI-003938, CCI-004188 &nbsp;| **SRG:** SRG-OS-000255-GPOS-00096, SRG-OS-000474-GPOS-00219, SRG-OS-000465-GPOS-00209, SRG-OS-000473-GPOS-00218, SRG-OS-000337-GPOS-00129, SRG-OS-000359-GPOS-00146, SRG-OS-000472-GPOS-00217, SRG-OS-000257-GPOS-00098, SRG-OS-000466-GPOS-00210, SRG-OS-000042-GPOS-00020, SRG-OS-000468-GPOS-00212, SRG-OS-000392-GPOS-00172, SRG-OS-000463-GPOS-00207, SRG-OS-000039-GPOS-00017, SRG-OS-000467-GPOS-00211, SRG-OS-000470-GPOS-00214, SRG-OS-000461-GPOS-00205, SRG-OS-000258-GPOS-00099, SRG-OS-000471-GPOS-00215, SRG-OS-000458-GPOS-00203, SRG-OS-000037-GPOS-00015, SRG-OS-000040-GPOS-00018, SRG-OS-000471-GPOS-00216, SRG-OS-000476-GPOS-00221, SRG-OS-000254-GPOS-00095, SRG-OS-000042-GPOS-00021, SRG-OS-000358-GPOS-00145, SRG-OS-000477-GPOS-00222, SRG-OS-000365-GPOS-00152, SRG-OS-000475-GPOS-00220, SRG-OS-000041-GPOS-00019, SRG-OS-000038-GPOS-00016, SRG-OS-000462-GPOS-00206, SRG-OS-000055-GPOS-00026, SRG-OS-000755-GPOS-00220 &nbsp;| **DISA STIG:** APPL-26-001003 &nbsp;| **CMMC:** AU.L2-3.3.2, AU.L2-3.3.6 &nbsp;| **CIS Benchmark:** 3.1 (level 1) &nbsp;| **CIS Controls v8:** 8.2, 8.5 &nbsp;| **CCE:** CCE-95104-6

</details>


### Configure Audit_Control Owner to Root

`audit_control_owner_configure`

/etc/security/audit_control _MUST_ have the owner set to root.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/chown root /etc/security/audit_control
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-000171, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000063-GPOS-00032, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001120 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95109-5

</details>


### Configure Audit Log Folders to be Owned by Root

`audit_folder_owner_configure`

Audit log folders _MUST_ be owned by root.

The audit service _MUST_ be configured to create log folders with the correct ownership to prevent normal users from reading audit logs.

Audit logs contain sensitive data about the system and users. If log folders are set to only be readable and writable by system administrators, the risk is mitigated.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/chown root /var/audit
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001013 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95125-1

</details>


### Configure Audit_Control to Not Contain Access Control Lists

`audit_control_acls_configure`

/etc/security/audit_control _MUST_ not contain Access Control Lists (ACLs).


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod -N /etc/security/audit_control
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-000171, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000063-GPOS-00032, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001140 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95106-1

</details>


### Configure Audit Log Folders to Mode 700 or Less Permissive

`audit_folders_mode_configure`

The audit log folder _MUST_ be configured to mode 700 or less permissive so that only the root user is able to read, write, and execute changes to folders.

Because audit logs contain sensitive data about the system and users, the audit service _MUST_ be configured to mode 700 or less permissive; thereby preventing normal users from reading, modifying or deleting audit logs.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod 700 /var/audit
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001017 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95126-9

</details>


### Configure Audit Log Folder to Not Contain Access Control Lists

`audit_acls_folders_configure`

The audit log folder _MUST_ not contain access control lists (ACLs).

Audit logs contain sensitive data about the system and users. This rule ensures that the audit service is configured to create log folders that are readable and writable only by system administrators in order to prevent normal users from reading audit logs.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod -N /var/audit
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-000031 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95102-0

</details>


### Configure Audit Log Files Group to Wheel

`audit_files_group_configure`

Audit log files _MUST_ have the group set to wheel.

The audit service _MUST_ be configured to create log files with the correct group ownership to prevent normal users from reading audit logs.

Audit logs contain sensitive data about the system and users. If log files are set to be readable and writable only by system administrators, the risk is mitigated.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/chgrp -R wheel /var/audit/*
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001014 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95112-9

</details>


### Configure Audit_Control Owner to Mode 440 or Less Permissive

`audit_control_mode_configure`

/etc/security/audit_control _MUST_ be configured so that it is readable only by the root user and group wheel.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod 440 /etc/security/audit_control
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-000171, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000063-GPOS-00032, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001130 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95108-7

</details>


### Configure Audit Log Files to Not Contain Access Control Lists

`audit_acls_files_configure`

The audit log files _MUST_ not contain access control lists (ACLs).

This rule ensures that audit information and audit files are configured to be readable and writable only by system administrators, thereby preventing unauthorized access, modification, and deletion of files.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/chmod -RN /var/audit
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-001314, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-000030 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95101-2

</details>


### Configure Audit_Control Group to Wheel

`audit_control_group_configure`

/etc/security/audit_control _MUST_ have the group set to wheel.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/chgrp wheel /etc/security/audit_control
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-9 &nbsp;| **800-171r3:** 03.03.08 &nbsp;| **CCI:** CCI-000162, CCI-000163, CCI-000164, CCI-000171, CCI-001493, CCI-001494, CCI-001495 &nbsp;| **SRG:** SRG-OS-000256-GPOS-00097, SRG-OS-000057-GPOS-00027, SRG-OS-000063-GPOS-00032, SRG-OS-000059-GPOS-00029, SRG-OS-000257-GPOS-00098, SRG-OS-000258-GPOS-00099, SRG-OS-000058-GPOS-00028 &nbsp;| **DISA STIG:** APPL-26-001110 &nbsp;| **CMMC:** AU.L2-3.3.8 &nbsp;| **CIS Benchmark:** 3.5 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95107-9

</details>


---

## System Settings

### Ensure Location Services Is In the Menu Bar

`system_settings_location_services_menu_enforce`

Location Services menu item _MUST_ be enabled.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/defaults write /Library/Preferences/com.apple.locationmenu.plist ShowSystemServices -bool true
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 2.6.1.2 (level 2) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95385-1

</details>


### Disable Guest Access to Shared SMB Folders

`system_settings_guest_access_smb_disable`

Guest access to shared Server Message Block (SMB) folders _MUST_ be disabled.

Turning off guest access prevents anonymous users from accessing files shared via SMB.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/sysadminctl -smbGuestAccess off
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-2(9), AC-2 &nbsp;| **800-171r3:** 03.01.01 &nbsp;| **CMMC:** AC.L1-3.1.2 &nbsp;| **CIS Benchmark:** 2.13.2 (level 1) &nbsp;| **CIS Controls v8:** 3.3 &nbsp;| **CCE:** CCE-95373-7

</details>


### Enforce Session Lock After Screen Saver is Started

`system_settings_screensaver_ask_for_password_delay_enforce`

A screen saver _MUST_ be enabled and the system _MUST_ be configured to require a password to unlock once the screensaver has been on for a maximum of 5 seconds.

An unattended system with an excessive grace period is vulnerable to a malicious user.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - askForPasswordDelay: 5
  PayloadType: com.apple.screensaver

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-11 &nbsp;| **800-171r3:** 03.01.10 &nbsp;| **CCI:** CCI-000056 &nbsp;| **SRG:** SRG-OS-000028-GPOS-00009 &nbsp;| **DISA STIG:** APPL-26-000003 &nbsp;| **CMMC:** AC.L2-3.1.10 &nbsp;| **CIS Benchmark:** 2.11.2 (level 1) &nbsp;| **CIS Controls v8:** 4.7 &nbsp;| **CCE:** CCE-95395-0

</details>


### Ensure Time Machine Volumes are Encrypted

`system_settings_time_machine_encrypted_configure`

Time Machine volumes _MUST_ be encrypted.


<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 2.3.4.2 (level 1) &nbsp;| **CIS Controls v8:** 3.6, 3.11, 11.3 &nbsp;| **CCE:** CCE-95410-7

</details>


### Enforce macOS Updates are Automatically Installed

`system_settings_install_macos_updates_enforce`

Software Update _MUST_ be configured to enforce automatic installation of macOS updates is enabled.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AutomaticallyInstallMacOSUpdates: true
  PayloadType: com.apple.SoftwareUpdate

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 1.3 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4 &nbsp;| **CCE:** CCE-95380-2

</details>


### Require Administrator Password to Modify System-Wide Preferences

`system_settings_system_wide_preferences_configure`

The system _MUST_ be configured to require an administrator password in order to modify the system-wide preferences in System Settings.

Some Preference Panes in System Settings contain settings that affect the entire system. Requiring a password to unlock these system-wide settings reduces the risk of a non-authorized user modifying system configurations.


<details>
<summary><strong>Remediation</strong></summary>

```bash
authDBs=("system.preferences" "system.preferences.energysaver" "system.preferences.network" "system.preferences.printing" "system.preferences.sharing" "system.preferences.softwareupdate" "system.preferences.startupdisk" "system.preferences.timemachine")

for section in ${authDBs[@]}; do
  /usr/bin/security -q authorizationdb read "$section" > "/tmp/$section.plist"

  class_key_value=$(/usr/libexec/PlistBuddy -c "Print :class" "/tmp/$section.plist" 2>&1)
  if [[ "$class_key_value" == *"Does Not Exist"* ]]; then
    /usr/libexec/PlistBuddy -c "Add :class string user" "/tmp/$section.plist"
  else
    /usr/libexec/PlistBuddy -c "Set :class user" "/tmp/$section.plist"
  fi

  key_value=$(/usr/libexec/PlistBuddy -c "Print :shared" "/tmp/$section.plist" 2>&1)  	
  if [[ "$key_value" == *"Does Not Exist"* ]]; then
    /usr/libexec/PlistBuddy -c "Add :shared bool false" "/tmp/$section.plist"
  else
    /usr/libexec/PlistBuddy -c "Set :shared false" "/tmp/$section.plist"
  fi

  auth_user_key=$(/usr/libexec/PlistBuddy -c "Print :authenticate-user" "/tmp/$section.plist" 2>&1)  	
  if [[ "$auth_user_key" == *"Does Not Exist"* ]]; then
    /usr/libexec/PlistBuddy -c "Add :authenticate-user bool true" "/tmp/$section.plist"
  else
    /usr/libexec/PlistBuddy -c "Set :authenticate-user true" "/tmp/$section.plist"
  fi

  session_owner_key=$(/usr/libexec/PlistBuddy -c "Print :session-owner" "/tmp/$section.plist" 2>&1)  	
  if [[ "$session_owner_key" == *"Does Not Exist"* ]]; then
    /usr/libexec/PlistBuddy -c "Add :session-owner bool false" "/tmp/$section.plist"
  else
    /usr/libexec/PlistBuddy -c "Set :session-owner false" "/tmp/$section.plist"
  fi

  group_key=$(/usr/libexec/PlistBuddy -c "Print :group" "/tmp/$section.plist" 2>&1)
  if [[ "$group_key" == *"Does Not Exist"* ]]; then
    /usr/libexec/PlistBuddy -c "Add :group string admin" "/tmp/$section.plist"
  else
    /usr/libexec/PlistBuddy -c "Set :group admin" "/tmp/$section.plist"
  fi

  /usr/bin/security -q authorizationdb write "$section" < "/tmp/$section.plist"
done
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-6, AC-6(2), AC-6(1) &nbsp;| **800-171r3:** 03.01.07 &nbsp;| **CCI:** CCI-002235 &nbsp;| **SRG:** SRG-OS-000324-GPOS-00125, SRG-OS-000480-GPOS-00228 &nbsp;| **DISA STIG:** APPL-26-002069 &nbsp;| **CMMC:** AC.L1-3.1.1, AC.L2-3.1.5, AC.L2-3.1.6 &nbsp;| **CIS Benchmark:** 2.6.8 (level 1) &nbsp;| **CIS Controls v8:** 4.1 &nbsp;| **CCE:** CCE-95408-1

</details>


### Disable Printer Sharing

`system_settings_printer_sharing_disable`

Printer Sharing _MUST_ be disabled.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/cupsctl --no-share-printers
/usr/bin/lpstat -p | awk '{print $2}'| /usr/bin/xargs -I{} lpadmin -p {} -o printer-is-shared=false
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002240 &nbsp;| **CMMC:** CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.3.3 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95391-9

</details>


### Disable Improve Search Information to Apple

`system_settings_improve_search_disable`

Sending data to Apple to help improve search _MUST_ be disabled. This will disable "Improve Search" within Spotlight in System Settings.

The information system _MUST_ be configured to provide only essential capabilities. Disabling the submission of search data will mitigate the risk of unwanted data being sent to Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - Search Queries Data Sharing Status: 2
  PayloadType: com.apple.assistant.support

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002024 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.9.1 &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95378-6

</details>


### Disable Personalized Advertising

`system_settings_personalized_advertising_disable`

Ad tracking and targeted ads _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling ad tracking ensures that applications and advertisers are unable to track users' interests and deliver targeted advertisements.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowApplePersonalizedAdvertising: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002200 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.6.4 (level 1) &nbsp;| **CIS Controls v8:** 4.8 &nbsp;| **CCE:** CCE-95390-1

</details>


### Disable the Guest Account

`system_settings_guest_account_disable`

Guest access _MUST_ be disabled.

Turning off guest access prevents anonymous users from accessing files.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - DisableGuestAccount: true
  - EnableGuestAccount: false
  PayloadType: com.apple.MCX

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-2, AC-2(9) &nbsp;| **800-171r3:** 03.01.01 &nbsp;| **CCI:** CCI-001813 &nbsp;| **SRG:** SRG-OS-000364-GPOS-00151, SRG-OS-000480-GPOS-00228 &nbsp;| **DISA STIG:** APPL-26-002063 &nbsp;| **CMMC:** AC.L1-3.1.2 &nbsp;| **CIS Benchmark:** 2.13.1 (level 1) &nbsp;| **CIS Controls v8:** 5.2, 6.2, 6.8 &nbsp;| **CCE:** CCE-95374-5

</details>


### Disable Server Message Block Sharing

`system_settings_smbd_disable`

Support for Server Message Block (SMB) file sharing is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/launchctl disable system/com.apple.smbd
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000213 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048 &nbsp;| **DISA STIG:** APPL-26-002001 &nbsp;| **CMMC:** AC.L1-3.1.1 &nbsp;| **CIS Benchmark:** 2.3.3.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8, 5.4 &nbsp;| **CCE:** CCE-95401-6

</details>


### Disable Password Hints

`system_settings_password_hints_disable`

Password hints _MUST_ be disabled.

Password hints leak information about passwords that are currently in use and can lead to loss of confidentiality.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - RetriesUntilHint: 0
  PayloadType: com.apple.loginwindow

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-6 &nbsp;| **800-171r3:** 03.05.11 &nbsp;| **CCI:** CCI-000206 &nbsp;| **SRG:** SRG-OS-000079-GPOS-00047 &nbsp;| **DISA STIG:** APPL-26-003012 &nbsp;| **CMMC:** IA.L2-3.5.11 &nbsp;| **CIS Benchmark:** 2.11.5 (level 1) &nbsp;| **CIS Controls v8:** 4.1 &nbsp;| **CCE:** CCE-95389-3

</details>


### Disable Screen Sharing and Apple Remote Desktop

`system_settings_screen_sharing_disable`

Support for both Screen Sharing and Apple Remote Desktop (ARD) is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling screen sharing and ARD helps prevent the unauthorized connection of devices, the unauthorized transfer of information, and unauthorized tunneling.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/bin/launchctl disable system/com.apple.screensharing
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000213 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048 &nbsp;| **DISA STIG:** APPL-26-002050 &nbsp;| **CMMC:** AC.L1-3.1.1 &nbsp;| **CIS Benchmark:** 2.3.3.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95394-3

</details>


### Disable Remote Management

`system_settings_remote_management_disable`

Remote Management _MUST_ be disabled.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002250 &nbsp;| **CMMC:** CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.3.5 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8, 5.4 &nbsp;| **CCE:** CCE-95393-5

</details>


### Enforce Screen Saver Timeout

`system_settings_screensaver_timeout_enforce`

The screen saver timeout _MUST_ be set to 1200 seconds or a shorter length of time.

This rule ensures that a full session lock is triggered within no more than 1200 seconds of inactivity.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - idleTime: 1200
  PayloadType: com.apple.screensaver

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-11, IA-11 &nbsp;| **800-171r3:** 03.01.10, 03.05.01 &nbsp;| **CCI:** CCI-000057 &nbsp;| **SRG:** SRG-OS-000029-GPOS-00010 &nbsp;| **DISA STIG:** APPL-26-000070 &nbsp;| **CMMC:** AC.L2-3.1.10 &nbsp;| **CIS Benchmark:** 2.11.1 (level 1) &nbsp;| **CIS Controls v8:** 4.3 &nbsp;| **CCE:** CCE-95397-6

</details>


### Configure Login Window to Prompt for Username and Password

`system_settings_loginwindow_prompt_username_password_enforce`

The login window _MUST_ be configured to prompt all users for both a username and a password.

By default, the system displays a list of known users on the login window, which can make it easier for a malicious user to gain access to someone else's account. Requiring users to type in both their username and password mitigates the risk of unauthorized users gaining access to the information system.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - SHOWFULLNAME: true
  PayloadType: com.apple.loginwindow

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-2 &nbsp;| **800-171r3:** 03.05.01 &nbsp;| **CCI:** CCI-000764 &nbsp;| **SRG:** SRG-OS-000104-GPOS-00051 &nbsp;| **DISA STIG:** APPL-26-005052 &nbsp;| **CMMC:** IA.L1-3.5.1, IA.L1-3.5.2 &nbsp;| **CIS Benchmark:** 2.11.4 (level 1) &nbsp;| **CIS Controls v8:** 4.1 &nbsp;| **CCE:** CCE-95387-7

</details>


### Enforce Software Update Downloads Updates Automatically

`system_settings_software_update_download_enforce`

Software Update _MUST_ be configured to enforce automatic downloads of updates is enabled.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AutomaticDownload: true
  PayloadType: com.apple.SoftwareUpdate

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 1.2 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4 &nbsp;| **CCE:** CCE-95403-2

</details>


### Disable Siri

`system_settings_siri_disable`

Support for Siri is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowAssistant: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06, 03.04.08 &nbsp;| **CCI:** CCI-000381, CCI-001774 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002020 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.2.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95398-4

</details>


### Disable SSH Server for Remote Access Sessions

`system_settings_ssh_disable`

SSH service _MUST_ be disabled for remote access.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/systemsetup -f -setremotelogin off >/dev/null
/bin/launchctl disable system/com.openssh.sshd
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1), AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CMMC:** AC.L1-3.1.1, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.3.4 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95406-5

</details>


### Disable Internet Sharing

`system_settings_internet_sharing_disable`

If the system does not require Internet sharing, support for it is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling Internet sharing helps prevent the unauthorized connection of devices, unauthorized transfer of information, and unauthorized tunneling.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - forceInternetSharingOff: true
  PayloadType: com.apple.MCX

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-4, AC-20 &nbsp;| **800-171r3:** 03.01.03, 03.01.20 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002007 &nbsp;| **CMMC:** AC.L1-3.1.20, AC.L2-3.1.3 &nbsp;| **CIS Benchmark:** 2.3.3.7 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95382-8

</details>


### Disable External Intelligence Integrations

`system_settings_external_intelligence_disable`

Integration with external intelligence systems _MUST_ be disabled unless approved by the organization. Disabling external intelligence integration will mitigate the risk of data being sent to unapproved third party.

The information system _MUST_ be configured to provide only essential capabilities.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowExternalIntelligenceIntegrations: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8, 15.3 &nbsp;| **CCE:** CCE-95365-3

</details>


### Enforce FileVault

`system_settings_filevault_enforce`

FileVault _MUST_ be enforced.

The information system implements cryptographic mechanisms to protect the confidentiality and integrity of information stored on digital media during transport outside of controlled areas.

NOTE: See the FileVault supplemental to implement this rule.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - dontAllowFDEDisable: true
  PayloadType: com.apple.MCX

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** SC-28, SC-28(1) &nbsp;| **800-171r3:** 03.13.08 &nbsp;| **CCI:** CCI-001199, CCI-002475, CCI-002476 &nbsp;| **SRG:** SRG-OS-000185-GPOS-00079, SRG-OS-000405-GPOS-00184, SRG-OS-000404-GPOS-00183 &nbsp;| **DISA STIG:** APPL-26-005020 &nbsp;| **CMMC:** SC.L2-3.13.16 &nbsp;| **CIS Benchmark:** 2.6.6 (level 1) &nbsp;| **CIS Controls v8:** 3.6, 3.11 &nbsp;| **CCE:** CCE-95367-9

</details>


### Ensure Software Update is Updated and Current

`system_settings_softwareupdate_current`

Make sure Software Update is updated and current.

link:https://support.apple.com/en-us/108382[Update macOS on Mac] or if enrolled in an MDM consult your MDM's documentation for automated methods.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/softwareupdate -i -a
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** SI-2 &nbsp;| **800-171r3:** 03.14.01, 03.14.02 &nbsp;| **CCI:** CCI-002605 &nbsp;| **SRG:** SRG-OS-000439-GPOS-00195 &nbsp;| **DISA STIG:** APPL-26-999999 &nbsp;| **CMMC:** SI.L1-3.14.1, SI.L1-3.14.2, SI.L1-3.14.4 &nbsp;| **CIS Benchmark:** 1.1 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4 &nbsp;| **CCE:** CCE-95405-7

</details>


### Configure Login Window to Show A Custom Message

`system_settings_loginwindow_loginwindowtext_enable`

The login window _MUST_ be configured to show a custom access warning message.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - LoginwindowText: Center for Internet Security Test Message
  PayloadType: com.apple.loginwindow

```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 2.11.3 (level 1) &nbsp;| **CIS Controls v8:** 4.1 &nbsp;| **CCE:** CCE-95386-9

</details>


### Disable External Intelligence Integration Sign In

`system_settings_external_intelligence_sign_in_disable`

The ability to sign into an external intelligence systems _MUST_ be disabled unless approved by the organization. Disabling external intelligence integration will mitigate the risk of data being sent to unapproved third party.

The information system _MUST_ be configured to provide only essential capabilities.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowExternalIntelligenceIntegrationsSignIn: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.5.1.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8, 15.3 &nbsp;| **CCE:** CCE-95366-1

</details>


### Enable macOS Application Firewall

`system_settings_firewall_enable`

The macOS Application Firewall is the built-in firewall that comes with macOS, and it _MUST_ be enabled.

When the macOS Application Firewall is enabled, the flow of information within the information system and between interconnected systems will be controlled by approved authorizations.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - EnableFirewall: true
  PayloadType: com.apple.security.firewall

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-4, SC-7(12), CM-7, CM-7(1), SC-7 &nbsp;| **800-171r3:** 03.01.03, 03.04.06, 03.13.01 &nbsp;| **CCI:** CCI-000366 &nbsp;| **SRG:** SRG-OS-000480-GPOS-00232 &nbsp;| **DISA STIG:** APPL-26-005050 &nbsp;| **CMMC:** AC.L2-3.1.3, CM.L2-3.4.6, CM.L2-3.4.7, SC.L1-3.13.1 &nbsp;| **CIS Benchmark:** 2.2.1 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.5, 13.1 &nbsp;| **CCE:** CCE-95369-5

</details>


### Disable Improve Siri and Dictation Information to Apple

`system_settings_improve_siri_dictation_disable`

The ability for Apple to store and review audio of your Siri and Dictation interactions _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling the submission of Siri and Dictation information will mitigate the risk of unwanted data being sent to Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - Siri Data Sharing Opt-In Status: 2
  PayloadType: com.apple.assistant.support

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002210 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.6.3.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95379-4

</details>


### Disable Bluetooth Sharing

`system_settings_bluetooth_sharing_disable`

Bluetooth Sharing _MUST_ be disabled.

Bluetooth Sharing allows users to wirelessly transmit files between the macOS and Bluetooth-enabled devices, including personally owned cellphones and tablets. A malicious user might introduce viruses or malware onto the system or extract sensitive files via Bluetooth Sharing. When Bluetooth Sharing is disabled, this risk is mitigated.

> **NOTE:**
> The check and fix are for the last logged in user. To get the last logged in user, run the following.
> ```bash
> CURRENT_USER=$( /usr/bin/defaults read /Library/Preferences/com.apple.loginwindow lastUserName )
> ```


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/sudo -u "$CURRENT_USER" /usr/bin/defaults -currentHost write com.apple.Bluetooth PrefKeyServicesEnabled -bool false
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-18(4), CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.04.06 &nbsp;| **CCI:** CCI-000213, CCI-000381 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048, SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002110 &nbsp;| **CMMC:** AC.L1-3.1.1, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.3.10 (level 1) &nbsp;| **CIS Controls v8:** 3.3, 4.1 &nbsp;| **CCE:** CCE-95361-2

</details>


### Disable Sending Diagnostic and Usage Data to Apple

`system_settings_diagnostics_reports_disable`

The ability to submit diagnostic data to Apple _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling the submission of diagnostic and usage information will mitigate the risk of unwanted data being sent to Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AutoSubmit: false
  PayloadType: com.apple.SubmitDiagInfo
- PayloadContent:
  - allowDiagnosticSubmission: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** SI-11, AC-20, SC-7(10) &nbsp;| **800-171r3:** 03.01.20 &nbsp;| **CCI:** CCI-001312, CCI-001314 &nbsp;| **SRG:** SRG-OS-000206-GPOS-00084, SRG-OS-000205-GPOS-00083 &nbsp;| **DISA STIG:** APPL-26-002021 &nbsp;| **CMMC:** AC.L1-3.1.20 &nbsp;| **CIS Benchmark:** 2.6.3.1 (level 1), 2.6.3.4 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95364-6

</details>


### Enforce Critical Security Updates to be Installed

`system_settings_critical_update_install_enforce`

Ensure that security updates are installed as soon as they are available from Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - CriticalUpdateInstall: true
  PayloadType: com.apple.SoftwareUpdate

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** SI-2 &nbsp;| **800-171r3:** 03.14.01 &nbsp;| **CMMC:** SI.L1-3.14.1, SI.L1-3.14.4 &nbsp;| **CIS Benchmark:** 1.5 (level 1) &nbsp;| **CIS Controls v8:** 7.3, 7.4, 7.7 &nbsp;| **CCE:** CCE-95363-8

</details>


### Enforce Screen Saver Password

`system_settings_screensaver_password_enforce`

Users _MUST_ authenticate when unlocking the screen saver.

The screen saver acts as a session lock and prevents unauthorized users from accessing the current user's account.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - askForPassword: true
  PayloadType: com.apple.screensaver

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-11 &nbsp;| **800-171r3:** 03.01.10, 03.05.01 &nbsp;| **CCI:** CCI-000056 &nbsp;| **SRG:** SRG-OS-000028-GPOS-00009 &nbsp;| **DISA STIG:** APPL-26-000002 &nbsp;| **CMMC:** AC.L2-3.1.10 &nbsp;| **CIS Benchmark:** 2.11.2 (level 1) &nbsp;| **CIS Controls v8:** 4.7 &nbsp;| **CCE:** CCE-95396-8

</details>


### Configure macOS to Use an Authorized Time Server

`system_settings_time_server_configure`

Approved time server _MUST_ be the only server configured for use.

This rule ensures the uniformity of time stamps for information systems with multiple system clocks and systems connected over a network.

NOTE: As of macOS 10.13 only one time server is supported.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - timeServer: time.apple.com
  PayloadType: com.apple.MCX

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-12(1), SC-45(1) &nbsp;| **800-171r3:** 03.03.07 &nbsp;| **CCI:** CCI-001891, CCI-002046, CCI-004923, CCI-004923, CCI-004926, CCI-004926 &nbsp;| **SRG:** SRG-OS-000355-GPOS-00143, SRG-OS-000356-GPOS-00144 &nbsp;| **DISA STIG:** APPL-26-000170 &nbsp;| **CMMC:** AU.L2-3.3.7 &nbsp;| **CIS Benchmark:** 2.3.2.1 (level 1) &nbsp;| **CIS Controls v8:** 8.4 &nbsp;| **CCE:** CCE-95411-5

</details>


### Enforce macOS Time Synchronization

`system_settings_time_server_enforce`

Time synchronization _MUST_ be enforced on all networked systems.

This rule ensures the uniformity of time stamps for information systems with multiple system clocks and systems connected over a network.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - com.apple.timed:
      TMAutomaticTimeOnlyEnabled: true
  PayloadType: com.apple.ManagedClient.preferences

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AU-12(1), SC-45(1) &nbsp;| **800-171r3:** 03.03.07 &nbsp;| **CCI:** CCI-001891, CCI-002046, CCI-004923, CCI-004926, CCI-004922 &nbsp;| **SRG:** SRG-OS-000355-GPOS-00143, SRG-OS-000356-GPOS-00144 &nbsp;| **DISA STIG:** APPL-26-000014 &nbsp;| **CMMC:** AU.L2-3.3.7 &nbsp;| **CIS Benchmark:** 2.3.2.1 (level 1) &nbsp;| **CIS Controls v8:** 8.4 &nbsp;| **CCE:** CCE-95412-3

</details>


### Ensure Wake for Network Access Is Disabled

`system_settings_wake_network_access_disable`

Wake for network access _MUST_ be disabled.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/bin/pmset -a womp 0
```

</details>

<details>
<summary><strong>References</strong></summary>

**CIS Benchmark:** 2.10.3 (level 1) &nbsp;| **CIS Controls v8:** 4.8 &nbsp;| **CCE:** CCE-95417-2

</details>


### Disable Unattended or Automatic Logon to the System

`system_settings_automatic_login_disable`

Automatic logon _MUST_ be disabled.

When automatic logons are enabled, the default user account is automatically logged on at boot time without prompting the user for a password. Even if the screen is later locked, a malicious user would be able to reboot the computer and find it already logged in. Disabling automatic logons mitigates this risk.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - com.apple.login.mcx.DisableAutoLoginClient: true
  PayloadType: com.apple.loginwindow

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** IA-2, IA-5(13) &nbsp;| **800-171r3:** 03.05.01 &nbsp;| **CCI:** CCI-000366 &nbsp;| **SRG:** SRG-OS-000480-GPOS-00229, SRG-OS-000104-GPOS-00051, SRG-OS-000480-GPOS-00228 &nbsp;| **DISA STIG:** APPL-26-002066 &nbsp;| **CMMC:** IA.L1-3.5.1, IA.L1-3.5.2 &nbsp;| **CIS Benchmark:** 2.13.3 (level 1) &nbsp;| **CIS Controls v8:** 4.7 &nbsp;| **CCE:** CCE-95356-2

</details>


### Disable Airplay Receiver

`system_settings_airplay_receiver_disable`

Airplay Receiver allows you to send content from another Apple device to be displayed on the screen as it's being played from your other device.

Support for Airplay Receiver is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - allowAirPlayIncomingRequests: false
  PayloadType: com.apple.applicationaccess

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1) &nbsp;| **800-171r3:** 03.04.06 &nbsp;| **CCI:** CCI-000381, CCI-001443 &nbsp;| **SRG:** SRG-OS-000300-GPOS-00118, SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002080 &nbsp;| **CMMC:** CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.3.1.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95354-7

</details>


### Disable Sending Audio Recordings and Transcripts to Apple

`system_settings_improve_assistive_voice_disable`

The ability for Apple to store and review audio of your audio recordings and transcripts of your vocal shortcuts and voice control interactions _MUST_ be disabled. This will disable "Improve Assistive Voice Features" in Privacy & Security within System Settings.

The information system _MUST_ be configured to provide only essential capabilities. Disabling the submission of this information will mitigate the risk of unwanted data being sent to Apple.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - AXSAudioDonationSiriImprovementEnabled: false
  PayloadType: com.apple.Accessibility

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-20, CM-7, CM-7(1), SC-7(10) &nbsp;| **800-171r3:** 03.01.20, 03.04.06 &nbsp;| **CCI:** CCI-000381 &nbsp;| **SRG:** SRG-OS-000095-GPOS-00049 &nbsp;| **DISA STIG:** APPL-26-002023 &nbsp;| **CMMC:** AC.L1-3.1.20, CM.L2-3.4.6, CM.L2-3.4.7 &nbsp;| **CIS Benchmark:** 2.6.3.3 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95377-8

</details>


### Enable Firewall Stealth Mode

`system_settings_firewall_stealth_mode_enable`

Firewall Stealth Mode _MUST_ be enabled.

When stealth mode is enabled, the Mac will not respond to any probing requests, and only requests from authorized applications will still be authorized.

> **IMPORTANT:**
> Enabling firewall stealth mode may prevent certain remote mechanisms used for maintenance and compliance scanning from properly functioning. Information System Security Officers (ISSOs) are advised to first fully weigh the potential risks posed to their organization before opting not to enable stealth mode.


<details>
<summary><strong>Configuration Profile</strong></summary>

```xml
- PayloadContent:
  - EnableStealthMode: true
  - EnableFirewall: true
  PayloadType: com.apple.security.firewall

```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** CM-7, CM-7(1), SC-7(16), SC-7 &nbsp;| **800-171r3:** 03.04.06, 03.13.01 &nbsp;| **CMMC:** CM.L2-3.4.6, CM.L2-3.4.7, SC.L1-3.13.1 &nbsp;| **CIS Benchmark:** 2.2.2 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.5, 4.8 &nbsp;| **CCE:** CCE-95370-3

</details>


### Disable Remote Apple Events

`system_settings_rae_disable`

If the system does not require Remote Apple Events, support for Apple Remote Events is non-essential and _MUST_ be disabled.

The information system _MUST_ be configured to provide only essential capabilities. Disabling Remote Apple Events helps prevent the unauthorized connection of devices, the unauthorized transfer of information, and unauthorized tunneling.


<details>
<summary><strong>Remediation</strong></summary>

```bash
/usr/sbin/systemsetup -setremoteappleevents off
/bin/launchctl disable system/com.apple.AEServer
```

</details>

<details>
<summary><strong>References</strong></summary>

**800-53r5:** AC-3, AC-17 &nbsp;| **800-171r3:** 03.01.02, 03.04.06 &nbsp;| **CCI:** CCI-000213, CCI-000382 &nbsp;| **SRG:** SRG-OS-000080-GPOS-00048, SRG-OS-000096-GPOS-00050 &nbsp;| **DISA STIG:** APPL-26-002022 &nbsp;| **CMMC:** AC.L1-3.1.1 &nbsp;| **CIS Benchmark:** 2.3.3.6 (level 1) &nbsp;| **CIS Controls v8:** 4.1, 4.8 &nbsp;| **CCE:** CCE-95392-7

</details>


---

## Appendix: Quick Reference

| Rule ID | Title | Section | Severity |
|---------|-------|---------|----------|
| os_safari_warn_fraudulent_website_enable | Ensure Warn When Visiting A Fraudulent Website in Safari Is Enabled | Operating System | — |
| os_root_disable | Disable Root Login | Operating System | — |
| os_power_nap_disable | Disable Power Nap | Operating System | — |
| os_notes_transcription_disable | Disable Apple Intelligence Notes Transcription | Operating System | — |
| os_anti_virus_installed | Must Use an Approved Antivirus Program | Operating System | — |
| os_world_writable_system_folder_configure | Ensure No World Writable Files Exist in the System Folder | Operating System | — |
| os_mail_summary_disable | Disable Apple Intelligence Mail Summary | Operating System | — |
| os_safari_open_safe_downloads_disable | Disable Automatic Opening of Safe Files in Safari | Operating System | — |
| os_safari_advertising_privacy_protection_enable | Ensure Advertising Privacy Protection in Safari Is Enabled | Operating System | — |
| os_authenticated_root_enable | Enable Authenticated Root | Operating System | — |
| os_config_data_install_enforce | Enforce Installation of XProtect Remediator and Gatekeeper Updates Automatically | Operating System | — |
| os_notes_transcription_summary_disable | Disable Apple Intelligence Notes Transcription Summary | Operating System | — |
| os_guest_folder_removed | Remove Guest Folder if Present | Operating System | — |
| os_software_update_app_update_enforce | Enforce Software Update App Update Updates Automatically | Operating System | — |
| os_password_hint_remove | Remove Password Hint From User Accounts | Operating System | — |
| os_sudo_log_enforce | Configure Sudo To Log Events | Operating System | — |
| os_writing_tools_disable | Disable Apple Intelligence Writing Tools | Operating System | — |
| os_sudoers_timestamp_type_configure | Configure Sudoers Timestamp Type | Operating System | — |
| os_airdrop_disable | Disable AirDrop | Operating System | — |
| os_nfsd_disable | Disable Network File System Service | Operating System | — |
| os_httpd_disable | Disable the Built-in Web Server | Operating System | — |
| os_gatekeeper_enable | Enable Gatekeeper | Operating System | — |
| os_safari_show_full_website_address_enable | Ensure Show Full Website Address in Safari Is Enabled | Operating System | — |
| os_mobile_file_integrity_enable | Enable Apple Mobile File Integrity | Operating System | — |
| os_sip_enable | Ensure System Integrity Protection is Enabled | Operating System | — |
| os_terminal_secure_keyboard_enable | Ensure Secure Keyboard Entry Terminal.app is Enabled | Operating System | — |
| os_unlock_active_user_session_disable | Disable Login to Other User's Active and Locked Sessions | Operating System | — |
| os_time_server_enabled | Enable Time Synchronization Daemon | Operating System | — |
| os_sudo_timeout_configure | Configure Sudo Timeout Period to 0 | Operating System | — |
| os_software_update_deferral | Ensure Software Update Deferment Is Less Than or Equal to 30 Days | Operating System | — |
| os_system_wide_applications_configure | Ensure Appropriate Permissions Are Enabled for System Wide Applications | Operating System | — |
| os_safari_show_status_bar_enabled | Ensure Show Safari shows the Status Bar is Enabled | Operating System | — |
| os_install_log_retention_configure | Configure Install.log Retention to 365 | Operating System | — |
| os_home_folders_secure | Secure User's Home Folders | Operating System | — |
| os_on_device_dictation_enforce | Enforce On Device Dictation | Operating System | — |
| os_safari_prevent_cross-site_tracking_enable | Ensure Prevent Cross-site Tracking in Safari Is Enabled | Operating System | — |
| pwpolicy_max_lifetime_enforce | Restrict Maximum Password Lifetime to 365 Days | Password Policy | — |
| pwpolicy_account_lockout_timeout_enforce | Set Account Lockout Time to 15 Minutes | Password Policy | — |
| pwpolicy_history_enforce | Prohibit Password Reuse for a Minimum of 15 Generations | Password Policy | — |
| pwpolicy_account_lockout_enforce | Limit Consecutive Failed Login Attempts to 5 | Password Policy | — |
| pwpolicy_minimum_length_enforce | Require a Minimum Password Length of 15 Characters | Password Policy | — |
| audit_folder_group_configure | Configure Audit Log Folders Group to Wheel | Audit | — |
| audit_files_mode_configure | Configure Audit Log Files to Mode 440 or Less Permissive | Audit | — |
| audit_retention_configure | Configure Audit Retention to 60d OR 5G | Audit | — |
| audit_files_owner_configure | Configure Audit Log Files to be Owned by Root | Audit | — |
| audit_auditd_enabled | Enable Security Auditing | Audit | — |
| audit_control_owner_configure | Configure Audit_Control Owner to Root | Audit | — |
| audit_folder_owner_configure | Configure Audit Log Folders to be Owned by Root | Audit | — |
| audit_control_acls_configure | Configure Audit_Control to Not Contain Access Control Lists | Audit | — |
| audit_folders_mode_configure | Configure Audit Log Folders to Mode 700 or Less Permissive | Audit | — |
| audit_acls_folders_configure | Configure Audit Log Folder to Not Contain Access Control Lists | Audit | — |
| audit_files_group_configure | Configure Audit Log Files Group to Wheel | Audit | — |
| audit_control_mode_configure | Configure Audit_Control Owner to Mode 440 or Less Permissive | Audit | — |
| audit_acls_files_configure | Configure Audit Log Files to Not Contain Access Control Lists | Audit | — |
| audit_control_group_configure | Configure Audit_Control Group to Wheel | Audit | — |
| system_settings_location_services_menu_enforce | Ensure Location Services Is In the Menu Bar | System Settings | — |
| system_settings_guest_access_smb_disable | Disable Guest Access to Shared SMB Folders | System Settings | — |
| system_settings_screensaver_ask_for_password_delay_enforce | Enforce Session Lock After Screen Saver is Started | System Settings | — |
| system_settings_time_machine_encrypted_configure | Ensure Time Machine Volumes are Encrypted | System Settings | — |
| system_settings_install_macos_updates_enforce | Enforce macOS Updates are Automatically Installed | System Settings | — |
| system_settings_system_wide_preferences_configure | Require Administrator Password to Modify System-Wide Preferences | System Settings | — |
| system_settings_printer_sharing_disable | Disable Printer Sharing | System Settings | — |
| system_settings_improve_search_disable | Disable Improve Search Information to Apple | System Settings | — |
| system_settings_personalized_advertising_disable | Disable Personalized Advertising | System Settings | — |
| system_settings_guest_account_disable | Disable the Guest Account | System Settings | — |
| system_settings_smbd_disable | Disable Server Message Block Sharing | System Settings | — |
| system_settings_password_hints_disable | Disable Password Hints | System Settings | — |
| system_settings_screen_sharing_disable | Disable Screen Sharing and Apple Remote Desktop | System Settings | — |
| system_settings_remote_management_disable | Disable Remote Management | System Settings | — |
| system_settings_screensaver_timeout_enforce | Enforce Screen Saver Timeout | System Settings | — |
| system_settings_loginwindow_prompt_username_password_enforce | Configure Login Window to Prompt for Username and Password | System Settings | — |
| system_settings_software_update_download_enforce | Enforce Software Update Downloads Updates Automatically | System Settings | — |
| system_settings_siri_disable | Disable Siri | System Settings | — |
| system_settings_ssh_disable | Disable SSH Server for Remote Access Sessions | System Settings | — |
| system_settings_internet_sharing_disable | Disable Internet Sharing | System Settings | — |
| system_settings_external_intelligence_disable | Disable External Intelligence Integrations | System Settings | — |
| system_settings_filevault_enforce | Enforce FileVault | System Settings | — |
| system_settings_softwareupdate_current | Ensure Software Update is Updated and Current | System Settings | — |
| system_settings_loginwindow_loginwindowtext_enable | Configure Login Window to Show A Custom Message | System Settings | — |
| system_settings_external_intelligence_sign_in_disable | Disable External Intelligence Integration Sign In | System Settings | — |
| system_settings_firewall_enable | Enable macOS Application Firewall | System Settings | — |
| system_settings_improve_siri_dictation_disable | Disable Improve Siri and Dictation Information to Apple | System Settings | — |
| system_settings_bluetooth_sharing_disable | Disable Bluetooth Sharing | System Settings | — |
| system_settings_diagnostics_reports_disable | Disable Sending Diagnostic and Usage Data to Apple | System Settings | — |
| system_settings_critical_update_install_enforce | Enforce Critical Security Updates to be Installed | System Settings | — |
| system_settings_screensaver_password_enforce | Enforce Screen Saver Password | System Settings | — |
| system_settings_time_server_configure | Configure macOS to Use an Authorized Time Server | System Settings | — |
| system_settings_time_server_enforce | Enforce macOS Time Synchronization | System Settings | — |
| system_settings_wake_network_access_disable | Ensure Wake for Network Access Is Disabled | System Settings | — |
| system_settings_automatic_login_disable | Disable Unattended or Automatic Logon to the System | System Settings | — |
| system_settings_airplay_receiver_disable | Disable Airplay Receiver | System Settings | — |
| system_settings_improve_assistive_voice_disable | Disable Sending Audio Recordings and Transcripts to Apple | System Settings | — |
| system_settings_firewall_stealth_mode_enable | Enable Firewall Stealth Mode | System Settings | — |
| system_settings_rae_disable | Disable Remote Apple Events | System Settings | — |


---

*Generated by M.A.C.E. (macOS Advanced Compliance Editor)*
