# Autologon Dependency Discovery

The Autologon Account Discovery will find accounts in the registry, and Autologon.exe. This script is essential for finding these accounts, and making them a dependency

| Environment | Version |
| ------ | ------ |
| Secret Server | 10.0+ |
| Operating System | Any Supported |
| PowerShell | Windows Management Framework 3+ |

## Prerequisites

- Machines with Autologon preconfigured
- Autologon.exe added to all compatible machines
- Powershell remoting enabled on these machines

## Installation

1. Apply Discover Autologon script:
   - **ADMIN** > **Scripts**
2. Configure Scan Template:
    - **ADMIN** > **Discovery** > **Extensible Discovery** > **Configure Scan Templates** >
    - **Dependencies** > **Create New Scan Template**

    ![Scan Template Designer](imgs/scanner-1.PNG)

3. Configure Discovery Scanner:
    - **ADMIN** > **Discovery** > **Extensible Discovery** > **Configure Discovery Scanners** >
    - **Dependencies** > **Create New Scanner**
    - **Input Template**: Windows Computer
    - **Output Template**: Select scan template from step 2
    - **Script**: Select  script from step 1
    - **Arguments**: $[1]$USERNAME $[1]$PASSWORD $[1]$DOMAIN $target

    ![Create New Scanner](imgs/scanner-2.PNG)

4. Adding the Scanner
    - **ADMIN** > **Discovery** > **Edit Discovery Sources** and select your source
    - Click on **Scanner Settings** Tab
    - Scroll down to **Find Dependencies** > **Add New Dependency Scanner**
    - Select **Autologon** from the scanner list

    ![Add Scanner](imgs/scanner-3.PNG)

5. Run Discovery
    - The new scanner will find the Dependencies
    - You will not be able to import without a Dependency template
    - Please follow the guide in [Remote Password Changing repo](https://github.com/thycotic/PasswordChangers/tree/master/Dependencies/Autologon "Autologon Changer")
