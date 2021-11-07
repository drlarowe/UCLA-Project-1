# UCLA-Project-1
UCLA Project 1


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/drlarowe/UCLA-Project-1/blob/8969973f32263b2130fad43320f6777c7584eca8/AzureNetworkDiagram/AzureNetworkDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - /ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure and available, in addition to restricting access and/or threats to the network.
- Load Balancers protect availability via redundancy. 
- 
- The advantage of a JumpBox is that it allows access and mangagement of devices in a particular network while in a different security zone or even remotely.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat collects and monitors log files. It forwards this data which can then be indexed and reviewed.
- Metricbeat records system and service metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | IP Address | Operating System |   |
|-----------|----------|------------|------------------|---|
| JumpBox   | Gateway  | 10.0.0.4   | Linux            |   |
| Web1 VM   | DVWA     | 10.0.0.7   | Linux            |   |
| Web2 VM   | DVWA     | 10.0.0.8   | Linux            |   |
| Web3 VM   | DVWA     | 10.0.0.9   | Linux            |   |
| BRASIL-VM | ELK      | 10.1.0.4   | Linux            |   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Local Host (My Public IP)

Machines within the network can only be accessed by JumpBox.
- Which machine did you allow to access your ELK VM? JumpBox IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Address        |   |   |
|-----------|---------------------|---------------------------|---|---|
| JumpBox   | Yes                 | Local Host (My Public IP) |   |   |
| Web1 VM   | No                  | 10.0.0.4                  |   |   |
| Web2 VM   | No                  | 10.0.0.4                  |   |   |
| Web3 VM   | No                  | 10.0.0.4                  |   |   |
| BRASIL-VM | Yes                 | 10.0.0.4                  |   |   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automating configuration with Ansible is that this allows time to be freed from tedious manual tasks. In sum, it allows for better efficiency.

The playbook implements the following tasks:
- Install Python3-pip
- Install Docker
- Install ELK
- Create and launch Docker container
- Enable Docker service on restart

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/drlarowe/UCLA-Project-1/blob/3eab42bc56aadda896292fe84a30456ba04432e7/Images/docker_ps_output.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.7, 10.0.0.8, 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Fielbeat collects log information and then forwards this to Logstash or Elasticsearch for indexing.
- Metricbeat collects information on the Operating System and also from services running on servers. This data can be forwarded to Logstash or Elastisearch as well.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/roles.
- Update the /ansible/hosts file to include the IPs of the 3 virtual machines created (Web1-10.0.0.7, Web2-10.0.0.8, Web3-10.0.0.9)
- Run the playbook, and navigate to http://20.197.178.215:5601/app/kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?
  
  The playbook file is filebeat-playbook.yml and it is copied to /etc/ansible/files.
  
- _Which file do you update to make Ansible run the playbook on a specific machine?
 
  The /ansible/hosts file must be updated
  
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
  
  By specificying the name of the group which the server falls under
  
- _Which URL do you navigate to in order to check that the ELK server is running? 
 
  http://20.197.178.215:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
