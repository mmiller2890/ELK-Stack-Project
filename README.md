## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/81493590/112739042-e0f79b80-8f3e-11eb-8fe1-0d5f924edbee.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/mmiller2890/ELK-Stack-Project/blob/95f2d5fe1316c8d0f6b805d2c2839a8f25051833/install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancing offers protection against DDos attacks, one thing that sets the Jump Box apart is that it works to provide a gateway router to the users private network. So essentially the users virtual machines within the network are not directly connecting to the internet allowing for more secure network 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filbeat moniters the file system and provides data about file changes 
- Metricbeat provides machine metrics data, ie uptime

The configuration details of each machine may be found below.

| Name       | Function       | IP Address | Operating Systemn |
|------------|----------------|------------|-------------------|
| Jump Box   | Gateway        | 10.0.0.4   | Linux             |
| Web-1      | DVWA Container | 10.0.0.7   | Linux             |
| Web-2      | DVWA Container | 10.0.0.8   | Linux             |
| Elk-Server | Server         | 10.1.0.4   | Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 98.24.172.61

Machines within the network can only be accessed by Jump Box.
- The ELK server can be accessed by Web1, Web2, and the Jump Box

A summary of the access policies in place can be found in the table below.

| Jump Box   | Publicly Accessible  | Allowed IP Address    |
|------------|----------------------|-----------------------|
| Jump Box   |          NO          | 10.0.0.4/98.24.172.61 |
| Web-1      |          NO          | 10.0.0.4/98.24.172.61 |
| Web-2      |          NO          | 10.0.0.4/98.24.172.61 |
| Elk-Server | NO                   | 98.24.172.61          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because when you automate anything it allows for the creator to focus and put time into other responsiblities 


The playbook implements the following tasks:
- Configure Elk VM with Docker
- Install docker.io
- Install pip3
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![image](https://user-images.githubusercontent.com/81493590/112738031-ba813280-8f35-11eb-97d9-9ba2d8434fa5.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.7
- Web-2 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filbeat moniters the file system and provides data about file changes Metricbeat provides machine metrics data, ie uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to /etc/ansible.
- Update the hosts file to be as follows. This will assign the VM servers to their server groups for the ansible Playbooks.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.


