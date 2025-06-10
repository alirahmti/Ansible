# 🚀 Ansible Installation and Verification on Ubuntu 22.04, 24.04

Ansible is an open-source IT automation tool that helps you automate tasks such as software installation, system configuration, and deployment across multiple machines. 🌐

It is primarily used for:
- **Configuration Management** 🔧
- **Application Deployment** 📦
- **Task Automation** 🛠️

Ansible works by using **Playbooks**, written in YAML, and **Modules** to automate tasks. One of its best features is that it doesn't require agents to be installed on the target machines — it simply uses SSH to communicate with the nodes. 🚀

---

## 🛠 Prerequisites

Before we begin, ensure you have the following:
- **Operating System**: Ubuntu 20.04
- **Internet Access** 🌍
- **Root or Sudo Access** 👨‍💻

---

## 📦 Installation Steps for Ansible

### 1️⃣ Update Your System

Start by updating your package index and upgrading your system to the latest available versions:

```bash
sudo apt update && sudo apt upgrade -y
````

### 2️⃣ Install Required Dependencies

Install `software-properties-common` which helps in managing repositories:

```bash
sudo apt install -y software-properties-common
```

### 3️⃣ Add Ansible PPA (Personal Package Archive)

Ansible provides an official PPA (Personal Package Archive) for Ubuntu to get the latest stable version:

```bash
sudo add-apt-repository ppa:ansible/ansible
```

### 4️⃣ Update Package Index

After adding the PPA, update your package index again:

```bash
sudo apt update
```

### 5️⃣ Install Ansible

Now, you can install Ansible using the package manager:

```bash
sudo apt install -y ansible
```

### 6️⃣ Verify Installation

To verify that Ansible was installed correctly, check its version by running:

```bash
ansible --version
```

You should see output like this, confirming the version of Ansible:

```
ansible 2.x.x
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/usr/share/ansible']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.x.x (default, ...)
```

---

## ✅ Test Ansible Installation

### 1️⃣ Create a Simple Ansible Inventory

First, create an **inventory file** that lists the hosts Ansible will manage. You can use the default file at `/etc/ansible/hosts` or create your own. For this example, create a new inventory file `myinventory` in your home directory:

```bash
touch ~/myinventory
```

Add the following content to the `myinventory` file:

```
[local]
localhost ansible_connection=local
```

### 2️⃣ Run a Simple Ansible Command

Now, test Ansible by pinging the localhost using the command:

```bash
ansible -i ~/myinventory local -m ping
```

If everything is set up correctly, you should see output like this:

```
localhost | SUCCESS | rc=0 >>
pong
```

This confirms that Ansible can successfully communicate with the local machine.

---

## 🎉 You're Ready to Use Ansible!

Now that you’ve installed and verified Ansible, you can start using it to automate tasks on your systems. Enjoy automating! ⚡

---

## 🔗 Helpful Links

* [Ansible Official Documentation](https://docs.ansible.com/)
* [Ansible GitHub Repository](https://github.com/ansible/ansible)
* [Ansible Tutorials](https://www.ansible.com/resources/get-started)

Happy automating! 😎




## **Author** ✍️

Created by [Ali Rahmati](https://github.com/alirahmti). If you find this repository helpful, feel free to fork it or contribute!
