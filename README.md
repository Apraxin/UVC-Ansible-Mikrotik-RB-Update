# MikroTik-RouterOS-Update-Ansible
Updating MikroTik RouterOS Devices using Ansible (both CHR and RB)

<h1>What?</h1>

- Updating RouterOS using Ansible

<h1>Where?</h1>

- Tested on Ansible 2.9.1
- RouterOS version not lower than 6.45 due to the use of sftp to transfer files

<h1>How?</h1>

- Just start playbook <b>RouterOS-Update.yml</b>
- Playbooks <b>BackupRouterOS.yml</b>, <b>UpdateRouterOS-RB.yml</b>, <b>UpdateRouterOS-CHR.yml</b> are needed for work

<h1>Warning!</h1>

- I use ssh keys for authentication in example (and strictly recommend it)
- Before using, check the RouterOS latest version and type it in <b>RouterOS-Update.yml</b> playbook in three places (strings № 7, 40, 46)

<h1>How does it work?</h1>

General Steps:
1. Doing export and backup files of RouterOS
2. Copying these files to "bk" folder
3. Checking and Printing if it's CHR or RB
4. Checking and Printing RouterOS Version (both CHR and RB)
5. Updating CHR RouterOS, if needed  (when current RouterOS version != {{ version }})
6. Updating RB RouterOS + RB Firmware, if needed (when current RouterOS version != {{ version }})
7. Checking and Printing RouterOS Version after Updating (both CHR and RB)
8. Checking and Printing Firmware Version after Updating (refers to RB only)
9. Some cleaning on every steps

Due to scripting (delays and pauses) durations of RB and CHR updating are 6 min 25 sec and 2 min 15 sec respectively

<h1>What to do?</h1>

- Just enjoy!
