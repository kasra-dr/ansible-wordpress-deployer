# Automated WordPress Deployment with Ansible

This project automates the entire process of provisioning a server and deploying a complete, containerized WordPress site using Ansible. The playbook configures a bare Debian server, installs all necessary dependencies, and deploys WordPress along with its MySQL database using Docker.

The entire workflow is defined using **Ansible Roles** for modularity and reusability, and sensitive data is secured using **Ansible Vault**.

---

## Key Concepts Demonstrated

* **Infrastructure as Code (IaC):** Using Ansible to define and manage server configuration.
* **Ansible Roles:** Structuring the project in a clean, reusable, and professional manner.
* **Secrets Management:** Securing sensitive data like database passwords with Ansible Vault.
* **Container Management:** Deploying and managing multi-container applications directly with Ansible's native Docker modules, bypassing the need for the `docker-compose` library.

---

## Technologies Used

* **Automation/Configuration Management:** Ansible
* **Containerization:** Docker
* **Application:** WordPress
* **Database:** MySQL
* **Base OS:** Debian 12

---

##  Project Structure

The project is organized into three main roles:
* **`common`:** Handles basic server setup, like updating packages, configuring DNS, and installing essential/build tools.
* **`docker`:** Installs and configures Docker Engine and its Python SDK dependencies.
* **`wordpress`:** Deploys the WordPress and MySQL containers using Ansible's `docker_container` module and connects them via a dedicated Docker network.

---

## How to Run

1.  Clone this repository.
2.  Install Ansible and the `community.docker` collection: `ansible-galaxy collection install community.docker`.
3.  Update the `inventory` file with your server's IP and user.
4.  Run the playbook using your vault password:
    ```bash
    ansible-playbook -i inventory playbook.yml --ask-vault-pass
    ```
