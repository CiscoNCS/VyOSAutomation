# VyOS Automation Ansible

VyOS + Ansible Playbooks for different kinds of setup.

* ZeroTouchVyOS Playbook
* DMVPN Playbook
* DMVPN (BGP) Playbook
* IPSEC and BGP Playbook
* IPSEC and GRE Playbook
* LAN Playbook
* User Creation and SSH Key Playbook


# Read the requirements to have a successful runtime. 

## Requirements

* Pip3 
* Python3 
* Openssh Server
* SSH Keys
* paramiko
* Ansible
* VyOS


# ZeroTouchVyOS Playbook
## Phase 1.1 System Configuration

* Configure Hostname
* Configure DNS
* Configure NTP
* Configure Domain Name

## Phase 1.2 System Monitoring Netflow

* Enables Netflow on eth0 interface
* Enables Netflow egress 
* Configure Netflow version
* Configure Netflow server with port (commonly 2055)
* Enables Netflow sample rate flow at 100
* Enables Netflow timeout interval for 30 seconds 


## Phase 1.3 System Hardening v1

* Sets new username and password
* Deletes default user (vyos)
* Enables SSH key authentication for the user you specify and have created in Phase 1.1
* Sets SSH key type to SSH-RSA which is by default used

## Cleanup Process

* Removes pre-configured NTP servers
# DMVPN Playbooks

## Hub

 All groups can be changed in the playbook.

ESP group = ESP-HUB
IKE group = IKE-HUB
IPSEC Profile = NHRPVPN 
* Configures tunnel interface (Tun1)
* Configure tunnel IP
* Configures tunnel IP key to 1
* Configure tunnel authentication (8 Character long)
* Enables multicast on the tunnel interface
* Configures tunnel interface holdtime to 600
* Enables NHRP redirection (cisco styled NHRP packets.)
* Enables NHRP Shortcut (Creates shortcut routes received by NHRP traffic.)
* Disables compression in the ESP Group
* Configures ESP lifetime to 28800
* Configures ESP in transport mode
* Configures PFS to DH group 21
* Configures ESP proposal 1 to AES256 and proposol 2 to SHA256
* Disables IKEv1 reauth 
* Configures IKE lifetime to 86400
* Configures IKE proposal 1 DH group to 21
* Configures IKE proposal 1 encryption to AES256 and Hash to SHA265 (Same applies to IKE proposal 2)
* Configures IPSEC interface to the WAN
* Configures IPSEC profile with ESP and IKE group 
* Configures IPSEC profile to use preshared key
* Configures IPSEC profile with the preshared key
* Binds the IPSEC profile to the tunnel interface

## Spoke

All groups can be changed in the playbook.

ESP group = ESP-HUB
IKE group = IKE-HUB
IPSEC Profile = NHRPVPN 
* Configures tunnel interface (Tun1)
* Configure tunnel IP
* Configures tunnel IP key to 1
* Configure tunnel authentication (8 Character long)
* Enables multicast on the tunnel interface
* Configures tunnel interface holdtime to 600
* 