---

# **Ansible-Nginx Deployment Project**  

🚀 **Automate Nginx Installation & Configuration Using Ansible**  

![Project Status](https://img.shields.io/badge/status-active-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-AWS_Linux_2-orange)

![Ansible](https://img.shields.io/badge/Ansible-Automation-red?logo=ansible)
![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green?logo=nginx)
![AWS](https://img.shields.io/badge/Deployed%20on-AWS-232F3E?logo=amazon-aws)



This project provides **Ansible playbooks** to automate the deployment and management of **Nginx web servers** on remote Linux machines.  

## **Key Features**  
✔ **Automated Nginx Installation** – Installs and configures Nginx with minimal manual intervention.  
✔ **Customizable Templates** – Supports Jinja2 templates for dynamic Nginx configurations.  
✔ **Idempotent Playbooks** – Ensures safe re-runs without unintended side effects.  
✔ **Inventory Management** – Easily define target servers in an `inventory.ini` file.  
✔ **Handlers for Service Management** – Automatically restarts Nginx on config changes.  

## **Use Cases**  
- Quickly set up **web servers** across multiple hosts.  
- Deploy **reverse proxies** or **load balancers**.  
- Automate **SSL/TLS setup** (if integrated with Let’s Encrypt).  

## **Getting Started**  
1. Clone the repo:  
   ```sh
   git clone https://github.com/vineeth729/Ansible-Nginx-Project.git
   ```
2. Configure your `inventory.ini` file.  
3. Run the playbook:  
   ```sh
   ansible-playbook -i inventory.ini playbook.yml
   ```  

🔧 **Customizable** – Modify `vars/` and `templates/` to fit your needs.  

---

### **Why This Project?**  
This playbook is ideal for **DevOps engineers, sysadmins, or developers** who want to:  
- **Save time** by automating Nginx deployments.  
- **Ensure consistency** across environments.  
- **Learn Ansible** for infrastructure automation.  

---
