# Automated Web Server Deployment and Configuration Management Using Ansible

## Project Overview

This project demonstrates the implementation of DevOps practices and configuration management using **Ansible**. It automates the installation, configuration, and deployment of an Nginx web server on Fedora Linux.

The project uses an Ansible inventory and YAML-based playbook to automate server configuration, deploy website files, and manage the Nginx service.

## Objectives

- Understand the DevOps lifecycle and workflow.
- Implement configuration management using Ansible.
- Create and configure an Ansible inventory.
- Develop an Ansible playbook for automated server configuration.
- Automate Nginx installation and website deployment.
- Verify successful execution and demonstrate idempotency.

## Technologies Used

| Technology | Purpose |
|---|---|
| Fedora Linux | Operating System |
| Ansible | Configuration Management |
| Nginx | Web Server |
| YAML | Playbook Configuration |
| HTML | Website Development |
| Git & GitHub | Version Control |
| Python 3 | Ansible Runtime |

## Project Architecture

The project uses Fedora Linux as both the Ansible control node and managed host.

**Workflow:**

1. Administrator creates an Ansible inventory.
2. Ansible reads the inventory.
3. Ansible executes the playbook.
4. Nginx is installed automatically.
5. Website files are deployed to the web directory.
6. Nginx service is started and enabled.
7. Website functionality is verified using a browser.

## Project Structure

```text
ansible-devops-project/
│
├── ansible.cfg
├── inventory.ini
├── site.yml
│
├── files/
    └── index.html

```

## Prerequisites

- Fedora Linux
- Python 3
- Ansible
- Git
- Internet connection

## Installation and Setup

### 1. Update the system

```bash
sudo dnf update -y
```

### 2. Install Ansible

```bash
sudo dnf install ansible-core -y
```

### 3. Verify Ansible installation

```bash
ansible --version
```

### 4. Install Git and curl

```bash
sudo dnf install git curl -y
```

## Configuration

### Ansible Inventory

The `inventory.ini` file defines the managed host and its connection configuration.

```ini
[webservers]
localhost ansible_connection=local ansible_python_interpreter=/usr/bin/python3
```

### Ansible Configuration

The `ansible.cfg` file specifies the inventory location and other default settings.

### Ansible Playbook

The `site.yml` playbook automates the following tasks:

1. Installs the Nginx web server.
2. Deploys the HTML website.
3. Starts the Nginx service.
4. Enables Nginx to start automatically during system boot.
5. Restarts Nginx when website content changes.

## Execution Instructions

Navigate to the project directory:

```bash
cd ~/ansible-devops-project
```

### 1. Verify Inventory

```bash
ansible-inventory --list
```

### 2. Test Host Connectivity

```bash
ansible webservers -m ping
```

### 3. Validate Playbook Syntax

```bash
ansible-playbook site.yml --syntax-check
```

### 4. Execute the Playbook

```bash
ansible-playbook site.yml --ask-become-pass
```

### 5. Verify Nginx Service

```bash
sudo systemctl status nginx
```

### 6. Verify Website Deployment

Open the following address in a web browser:

```text
http://localhost
```

Alternatively, execute:

```bash
curl http://localhost
```

### 7. Test Idempotency

Execute the same playbook again:

```bash
ansible-playbook site.yml --ask-become-pass
```

Ansible should report zero changes if the system is already in the desired state.

## DevOps Lifecycle

The project follows these DevOps lifecycle stages:

| Stage | Description |
|---|---|
| Plan | Identify deployment requirements |
| Code | Develop HTML and Ansible configuration files |
| Build | Prepare application and automation files |
| Test | Validate playbook syntax and configuration |
| Release | Prepare configuration for deployment |
| Deploy | Automate Nginx installation and website deployment |
| Operate | Manage the Nginx web server |
| Monitor | Verify service status and website accessibility |

## Expected Results

After successful execution:

- Nginx is installed on Fedora Linux.
- Website files are deployed automatically.
- Nginx service is running.
- Nginx is enabled at system startup.
- The website is accessible through `http://localhost`.
- Repeated playbook execution avoids unnecessary configuration changes.

## Learning Outcomes

- Understanding the DevOps lifecycle.
- Practical experience with Ansible configuration management.
- Understanding inventory files and YAML playbooks.
- Automating Linux server administration.
- Learning idempotency and infrastructure automation.
- Using Git and GitHub for version control.

## Conclusion

This project demonstrates how Ansible simplifies server configuration and application deployment through automation. By implementing an inventory and a reusable playbook, the installation and configuration of an Nginx web server can be performed efficiently with minimal manual intervention.

The project highlights the importance of automation, consistency, and configuration management in modern DevOps workflows.

---

**Project:** Automated Web Server Deployment and Configuration Management Using Ansible

**Operating System:** Fedora Linux

**Configuration Management Tool:** Ansible
