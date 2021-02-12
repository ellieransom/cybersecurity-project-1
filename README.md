## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
- Load balancers protect against a service being unavailable because one or more servers are unavailable. If one server goes down or is unavailable due to too much traffic (possible DDoS attack), then the load balancer is able to direct traffic to any other webserver without distrupting the service. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function   | IP Address | Operating System |
|----------------------|------------|------------|------------------|
| Jump-Box-Provisioner | Gateway    | 10.0.0.4   | Linux            |
| Web-1                | Webserver  | 10.0.0.5   | Linux            |
| Web-2                | Webserver  | 10.0.0.6   | Linux            |
| ELK-VM               | SIEM       | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.193.27.251

Machines within the network can only be accessed by the jump box.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses             |
|----------------------|---------------------|----------------------------------|
| Jump-Box-Provisioner | No                  | 24.193.27.251:22                 |
| Web-1                | No                  | 10.0.0.4:22                      |
| Web-2                | No                  | 10.0.0.4:22                      |
| ELK-VM               | No                  | 10.0.0.4:22  24.193.27.251:5601  |
| Red-Team-LB          | No                  | 24.193.27.251:80                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/roles/.
- Update the filebeat-config.yml file to include the IP address of your ELK server. Update the filebeat-playbook.yml to run on the webservers (hosts: webservers).
- Run the playbook, and navigate to ELK-VM to check that the installation worked as expected.
  - http://<ELK.VM.External.IP>:5601/app/kibana
  - http://40.75.114.96:5601/app/kibana


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

Download playbook:
- curl #TODO > /etc/ansible/roles/filebeat-playbook.yml

Edit playbook:
- nano /etc/ansible/roles/filebeat-playbook.yml

Run playbook:
- ansible-playbook /etc/ansible/roles/filebeat-playbook.yml