## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Azure Infrastructure.png and Azure Infrastructure.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting overload to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs and view their system logs.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| VM Name  | Function               | IP Address | Operating System |
|----------|------------------------|------------|------------------|
| Jump Box | Gateway                | 10.0.0.4   | Ubuntu 18.04     |
| DVWA-1   | Hosts DVWA App         | 10.0.0.5   | Ubuntu 18.04     |
| DVWA-2   | Hosts DVWA App         | 10.0.0.6   | Ubuntu 18.04     |
| ELK      | Hosts ELK Stack Server | 10.1.0.4   | Ubuntu 18.04     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the DVWA container can accept connections from the Internet.

Machines within the network can only be accessed by the Jump Box.

The Jump Box can only be accessed by my local machine.

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it can be started and configured automatically. 
The entire infrastructure can also be scaled to desired size due to automation.

The ELK playbook implements the following tasks:
- Changes VRAM to needed size to run the ELK server
- Downloads/installs Docker
- Downloads/installs the ELK container
- Auto-starts the server

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA-1: 10.0.0.5
- DVWA-2: 10.0.0.6
We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to see system logs on the DVWA machines.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to /etc/ansible.
- Update the hosts file to include the ip correct ip address of the machine under the 'elk' group
- Run the playbook, and in your browser navigate to the IP address of the elk machine at port 5601 to check that the installation worked as expected.
