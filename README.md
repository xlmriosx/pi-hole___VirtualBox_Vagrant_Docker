# Pi-Hole Setup 👨‍💻🛠️

Welcome to the one click deployment pi-hole.

## Index 📑

1. [Installation](#install-applications-🔽)
2. [Software Requirements](#software-requirements-⭕)
3. [Getting Started Environment](#getting-started-environment-✨)
4. [Verifying Correct Installation](#verifying-correct-installation-🆗)
5. [Resources](#resources-📚)
6. [Cheat Sheet Commands](#cheat-sheet-commands-📃)
7. [Additional Notes](#additional-notes-📝)

## Pre-requeriments ⛳

> Verify you have the correct `.rsa` key to enter differents servers.

- `dir ~\.ssh` In our case use `vagrant.rsa`

> Don't forget clone this repo and enter where is this file (README.md)

- `git clone <repo>`
- `cd <repo>`

If is your first time you will need install the following.

### Install applications 🔽

Before you begin, ensure you have Vagrant installed. If not, follow these steps:

1. **Install Vagrant**:
   - 🌐 [Download Vagrant](https://www.vagrantup.com/downloads)
   - Follow the installation instructions for your operating system.

2. **Install Vagrant Plugins**:
   - Open your terminal or command prompt.
   - Run the following commands:
     ```
     vagrant plugin install vagrant-vbguest
     vagrant plugin install vagrant-virtualbox_WSL2
     ```

3. **Install VirtualBox**:
   - 🌐 [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)
   - Follow the installation instructions for your operating system.

## Software Requirements ⭕

- **Operating System**: Windows 10 Pro N 64-bit
- **Virtualization Software**: VirtualBox 7.0
- **Version Control System**: Git

## Getting Started Pi-Hole ✨

In terminal:

1. Clone the repository for your Ansible project.

   `git clone <repo>`

2. Navigate to the project directory in your terminal.

   `cd <repo>`

3. Open your favorite IDE.

   `code .`

4. Aprovision the virtual machine.

   `vagrant up`

5. (Optional) Enter in VM need run.

   `vagrant ssh`

## Verifying Correct Installation 🆗

1. Navigate in your browser

   `http://10.10.10.10/admin/`

2. Enter the password that appear in your console in the web platform.

   `[i] Assigning random password: XXXXX`

## Resources 📚

Is strongly recommended read the following documentation.

[Ansible collections and molecule](https://www.virtualbox.org/wiki/Downloads)

## Additional Notes 📝

- Make sure virtualization is enabled in your BIOS settings for optimal performance.

> Happy blocking! ⚠️🔐