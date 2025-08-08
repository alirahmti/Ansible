# Ansible Installation Script for Ubuntu Server 🐧🔧

## Overview 🎉

This **Bash script** is designed to **automatically install Ansible** on **Ubuntu 22.04/24.04** and verify the installation with a simple test. It updates the system, installs required dependencies, adds the Ansible PPA, installs Ansible, and performs a test ping command to ensure everything is set up correctly. If any step fails, the script will stop and show an error message.

## What This Script Does 🛠️

1. **Update the system** 🛑: Ensures your system is up to date by running `apt update` and `apt upgrade`.
2. **Install required dependencies** 💻: Installs `software-properties-common`, which is needed to add PPAs.
3. **Add Ansible PPA** 🔑: Adds the official Ansible PPA to your system.
4. **Install Ansible** ⚙️: Installs Ansible using `apt install`.
5. **Verify Installation** ✅: Checks if Ansible is correctly installed by displaying the Ansible version.
6. **Create Ansible Inventory** 📁: Sets up a simple Ansible inventory file.
7. **Run a Test Command** 🧪: Runs a test Ansible command to verify that everything is working.



## Prerequisites ⚠️

* You must have **Ubuntu 22.04 or 24.04** installed.
* You should have **sudo** privileges.



## How to Use 📝

### 1️⃣ Download the Script

Copy the following bash script into a file on your Ubuntu server, e.g., `install_ansible.sh`:

```bash
#!/bin/bash

# Script to install Ansible on Ubuntu and verify the installation

# Function to handle errors
function error_exit {
    echo "$1"
    exit 1
}

# 1️⃣ Update the System
echo "Updating the system..."
sudo apt update && sudo apt upgrade -y || error_exit "System update failed!"

# 2️⃣ Install Required Dependencies
echo "Installing required dependencies..."
sudo apt install -y software-properties-common || error_exit "Failed to install dependencies!"

# 3️⃣ Add Ansible PPA
echo "Adding Ansible PPA..."
sudo add-apt-repository ppa:ansible/ansible || error_exit "Failed to add Ansible PPA!"

# 4️⃣ Update Package Index
echo "Updating package index after adding PPA..."
sudo apt update || error_exit "Failed to update package index!"

# 5️⃣ Install Ansible
echo "Installing Ansible..."
sudo apt install -y ansible || error_exit "Failed to install Ansible!"

# 6️⃣ Verify Installation
echo "Verifying Ansible installation..."
ansible --version || error_exit "Ansible installation verification failed!"

# ✅ Test Ansible Installation

# 1️⃣ Create a Simple Ansible Inventory
echo "Creating inventory file..."
touch ~/myinventory || error_exit "Failed to create inventory file!"
echo -e "[local]\nlocalhost ansible_connection=local" > ~/myinventory || error_exit "Failed to add inventory configuration!"

# 2️⃣ Run a Simple Ansible Command
echo "Running a test Ansible command..."
ansible -i ~/myinventory local -m ping || error_exit "Ansible ping test failed!"

# Success Message
echo "Ansible installation and test successful!"
```

### 2️⃣ Make the Script Executable

Give the script execution permissions:

```bash
chmod +x install_ansible.sh
```

### 3️⃣ Run the Script

Now, execute the script to install and test Ansible:

```bash
./install_ansible.sh
```


## What Happens During Execution 🏃‍♂️

1. **System Update** 🖥️: The script will update your system to the latest version.
2. **Installing Dependencies** ⚙️: It installs the `software-properties-common` package needed for adding PPAs.
3. **Adding Ansible PPA** 🔑: The official Ansible PPA is added to your system to get the latest version of Ansible.
4. **Installing Ansible** 🚀: Ansible will be installed via `apt install`.
5. **Installation Verification** ✅: The script checks if Ansible was installed successfully by running `ansible --version`.
6. **Inventory Creation** 🗂️: A simple inventory file is created to configure Ansible.
7. **Test Command** ⚡: The script runs a simple `ping` command to verify that Ansible is working.


## Troubleshooting 🛠️

If the script fails at any point, an error message will be displayed indicating the failure reason. Common issues include:

* **Network problems** 🌐: Make sure your system has a working internet connection.
* **Missing dependencies** ⚠️: If the script fails to install required packages, you might need to manually install them.
* **Permission issues** 🔒: Ensure you're running the script with `sudo` privileges.

## Conclusion 🎯

This script provides a simple, automated way to install Ansible on your Ubuntu server and verify the installation. By running this script, you ensure a quick and smooth setup for managing your servers with Ansible. Happy automating! 🌟

> ## 📝 About the Author
> #### Crafted with care and ❤️ by [Ali Rahmati](https://github.com/alirahmti). 👨‍💻
> If this repo saved you time or solved a problem, a ⭐ means everything in the DevOps world. 🧠💾
> Your star ⭐ is like a high five from the terminal — thanks for the support! 🙌🐧