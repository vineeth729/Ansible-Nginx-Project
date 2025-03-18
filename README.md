# Ansible-Nginx-Project
Step 1: Set Up Two AWS Linux 2 EC2 Instances
Launch two AWS EC2 instances with AWS Linux 2:
Control Node (for running Ansible)
Web Server (for hosting the blog)
Security Group Rules:
Control Node: Allow EC2 Instance Connect.
Web Server:
Allow SSH (port 22) from Control Node’s IP.
Allow HTTP (port 80) for public access.


Step 2: Install Ansible on the Control Node
Connect to the Control Node using EC2 Instance Connect.

Update packages:
sudo yum update -y

Install Ansible
sudo amazon-linux-extras enable ansible2
sudo yum install -y ansible


Verify Ansible installation

ansible --version


Step 3: Set Up SSH Access from Control Node to Web Server

ssh-keygen -t rsa -b 2048


cat ~/.ssh/id_rsa.pub

Copy the output.
Connect to Web Server using EC2 Instance Connect.
Run:

mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys

Paste the copied key → Save (Ctrl+X → Y → Enter).

Set permissions:
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh

Test SSH Access from Control Node:

ssh ec2-user@your-web-server-ip

If you can log in without a password, SSH is correctly configured.

Step 4: Configure Ansible Inventory
On the Control Node, create an inventory file:


nano ~/hosts.ini

Add Web Server details:

[webserver]
172.31.94.45 ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/id_rsa


Test Connection:


ansible -i hosts.ini all -m ping

If "pong" is returned, Ansible can access the web server.


Step 5: Create the Ansible Playbook
Create a playbook file:

nano ~/deploy.yml

Add the following Ansible script:

Step 6: Create Nginx Configuration

Create the Nginx configuration template:

nano ~/nginx_config.j2

Enable the Nginx repository on web server:

sudo amazon-linux-extras enable nginx1


Run the Playbook:
ansible-playbook -i hosts.ini deploy.yml


Ensure the Blogging Page Exists on the Control Node
On your Control Node, check if the blogging page files exist:

ls -l /home/ec2-user/blogging-page/
If the directory does not exist, create it:

mkdir -p /home/ec2-user/blogging-page/

cd /home/ec2-user/blogging-page/
nano index.html  # Add sample HTML content
