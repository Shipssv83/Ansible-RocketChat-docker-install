Hi, ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)my name is Serhii Shypylov
=========================================================================================================================================

💛 I am a Linux System administrator engineer with DevOps practices. I have several certificates in Linux, Docker, Ansible and Terraform and continue to learn more. I like everything related to Docker, containers and IT technologies in general. I love solving complex IT solutions.
-------------------------------

* 💼 Looking for a job
* 🌍 I'm based in Poznan
* 🖥️ See my [LinkedIn](https://github.com/Shipssv83) profile 
* 👾 Chat with IT pros on [Discord](https://discord.com/shipssv_19055)\
* 📧 Reach me at ships@ukr.net
* 🧠 I'm learning DevOps Practices

### Socials

<p align="left"> <a href="https://github.com/Shipssv83" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" width="32" height="32" /> </picture> </a> <a href="https://www.linkedin.com/in/sergey-shipilov-7262a31b4/" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" width="32" height="32" /> </picture> </a></p>

# Ansible Playbook for Server and Rocket.Chat Docker Installation

This repository contains an Ansible playbook for setting up a server, installing Docker, and deploying Rocket.Chat in a Docker container with firewall configuration (UFW).

## Playbook Overview

The playbook includes the following steps:
1. **Server Setup**: Initializes basic server settings.
2. **Docker Installation**: Installs Docker and Docker Compose for container management.
3. **Rocket.Chat Installation**: Deploys Rocket.Chat in a Docker container and configures it with UFW rules.

## Playbook Structure

### 1. Server Setup (`server-install.yml`)
The `server-install.yml` playbook installs necessary server dependencies and configures the system environment (e.g., timezone).

### 2. Docker Installation (`docker-install.yml`)
The `docker-install.yml` playbook installs Docker and Docker Compose on the server to prepare the system for running containers.

### 3. Rocket.Chat Docker Installation (`rocketchat-docker-install.yml`)
This playbook sets up Rocket.Chat within a Docker container, configures the web route, and allows traffic through UFW.

## Requirements

Before running the playbook, make sure the following requirements are met:
- Ansible 2.9+ installed on the control node.
- SSH access to the target hosts.
- A Linux server (Ubuntu, CentOS, etc.) with internet access.

## Roles Used

- **roles/server-install**: Sets up server environment and system-level configurations.
- **roles/docker-install**: Installs Docker and Docker Compose.
- **roles/rocketchat-docker-install**: Deploys Rocket.Chat in a Docker container.

## Variables

You can customize the playbook with the following variables:

- `fqdn`: The fully qualified domain name (FQDN) of the server (e.g., `example.com`).
- `server_name`: The name of the server where Rocket.Chat will be hosted (default: `rocket.example.com`).
- `rocket_root_url`: The root URL of Rocket.Chat, which can be accessed through a web browser.
  
### Example Variable Configuration:

```yaml
vars:
  fqdn: ecxexample.com
  server_name: "rocket.{{ fqdn }}"
  rocket_root_url: "https://rocket.{{ fqdn }}"
```

# ansible galaxy roles

```
### install role ansible galaxy
ansible-galaxy install -r roles/requirements.yml

### upgrade role ansible galaxy 
ansible-galaxy install -g -f -r roles/requirements.yml
```

# Run the Playbook install
Run the playbook by specifying your inventory file and variable file:

```
ansible-playbook -i inventory --user root --extra-vars "host=host_name" playbooks/rocketchat-install.yml
```

License
This project is licensed under the MIT License