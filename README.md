# active_directory_group_policy_lab

## Installing Windows Server 2022

I installed Windows Server 2022 on a VMware virtual machine and selected the Windows Server 2022 Datacenter edition during installation.

![vmware_oUYd51ViEu](https://github.com/user-attachments/assets/6e01f108-5674-48c8-b083-3bb94919a452)

## Basic Server Configuration

### Configure a Static IP Address on a Server

We configure a static IP address on a server because servers are meant to be reliable and always reachable. Clients, users, and other systems need to know exactly where to find the server. If a server uses DHCP, its IP address could change after a reboot, which would break network connections.

- IP - `192.168.0.10`
- Subnet Mask - `255.255.255.0`
- Default Gateway - `192.168.0.1`
- Preferred DNS Server - `8.8.8.8`

![vmware_5iMUEUrHP9](https://github.com/user-attachments/assets/dfd4b033-44a0-4641-8b50-98bb84c9712a)

