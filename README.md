# Project_1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Images/project_diagram.gliffy](https://github.com/WildRose900/Project_1/blob/master/Diagrams/project_diagram.gliffy)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire
deployment pictured above. Alternatively, select portions of the Beats Playbook file may be used to install only certain pieces of it, such as Filebeat.
    -[Ansible/Beats PlayBook.txt](https://github.com/WildRose900/Project_1/blob/master/Ansible/Beats%20Playbook.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting traffic to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics and statistics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA-VM1 | PHP/MySQL| 10.0.0.5   | Ansible          |
| DVWA-VM2 | PHP/MySQL| 10.0.0.6   | Ansible          |
| ELK      | Elk Stack| 10.1.0.4   | Ansible          |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 99.141.145.50

Machines within the network can only be accessed by the ansible container within the Jumpbox.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 99.141.145.50        |
| DVWA-VM1 | No                  |                      |
| DVWA-VM2 | No                  |                      |
| ELK      | No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is simple, agentless, and efficient.

The playbook implements the following tasks:
- Installs Docker.io
- Installs Python-pip
- Installs Docker Python Module
- Increases Virtual Memory
- Downloads and Launches a Docker Elk Container

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files, collects log events, and sends them to Elasticsearch and/or Logstash for indexing. 
- Metricbeat collects the metrics and statistics from the system and the services running and sends them to the output you choose.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the .yml file to your ansible container.
- Update the /etc/ansible/hosts file to include the private IP addresses of your servers under either [webservers] or [elkservers].
- Run the playbook, then navigate to http://[your.VM.IP]:5601 to check that the installation worked as expected.
