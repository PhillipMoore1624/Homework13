## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/PhillipMoore1624/Homework13/blob/main/Diagram/PhillipMoore_Week13_Network.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __playbook__ file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/PhillipMoore1624/Homework13/blob/main/Ansible/install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly __available__, in addition to restricting __access__ to the network.
A loadbalancer is meant to serve as a specific point of access for a service that is served by multiple machines. This allows high availability models to function properly without issue. 
A jumpbox serves as a gateway to gain entry into a remote network. Many times the primary mode of access is ssh and without the key access is restricted if not outright forbidden.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __log files__ and system __resources__.
Filebeat is meant primarily to watch for system logs and forward any changes to the Elasticsearch Host.
Metricbeat is used only for gathering metrics and system resources usage for display in Elasticsearch.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function            | IP Address | Operating System |
|----------|---------------------|------------|------------------|
| Jump Box | Gateway             | 10.0.0.4   | Linux            |
| Web 1    | Web Server          | 10.0.0.5   | Linux            |
| Web 2    | Web Server          | 10.0.0.6   | Linux            |
| Elk      | ElasticSearch Stack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __jump box__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
At time of submission IP Address is 68.231.176.209.

Machines within the network can only be accessed by the __jump box__.
Jump Box
Public IP: 40.117.83.223
Private IP: 10.0.0.4
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 68.231.176.209       |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
| Elk      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can configure multiple machines with little effort. 

The playbook implements the following tasks:
install: docker.io
install: python3-pip
install: docker
increase virtual memory
download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/PhillipMoore1624/Homework13/blob/main/Diagram/PhillipMoore_DockerPS_Proof.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web 1: 10.0.0.4
Web 2: 10.0.0.5

We have installed the following Beats on these machines:
Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects what changes are done and when while Metricbeat collects metrics and statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __filebeat-configuration.yml__ file to __/etc/ansible/files/filebeat-configuration.yml.___.
- Update the __/etc/ansible/host__ file to include the Web Server and ELK IP???s. 
- Run the playbook, and navigate to __http://40.117.83.223:5601/app/kibana__ to check that the installation worked as expected.
