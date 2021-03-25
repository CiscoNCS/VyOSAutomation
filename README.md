# VyOS_Automation
Ansible playbooks to configure almost all different kinds of VyOS deployments.

# Read the requirements to have a successful runtime. 

## Requirements

* Pip3 
* Python3 
* Openssh Server
* SSH Keys
* paramiko
* Ansible


# ZeroTouchVyOS Playbook
## Phase 1.1 System Configuration

* Hostname
* DNS
* NTP
* Domain Name

## Phase 1.2 System Monitoring Netflow

* Enables Netflow on eth0 interface
* Enables Netflow egress 
* Netflow Version
* Netflow Server with Port (commonly 2055)
* Enables Netflow Sample Rate flow at 100
* Enables Netflow Timeout Interval for 30 seconds 


## Phase 1.3 System Hardening v1

* New Username and Password
* Deletes default User (vyos)
* Enables SSH key authentication for the user you specify and have created in Phase 1.1
* Sets SSH key type to SSH-RSA which is by default used

## Cleanup Process

* Removes pre-configured NTP servers