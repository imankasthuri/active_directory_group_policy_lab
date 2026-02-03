# Active Directory Group Policy Lab

## Installing Windows Server 2022

I installed Windows Server 2022 on a VMware virtual machine and selected the Windows Server 2022 Datacenter edition during installation.

![vmware_oUYd51ViEu](https://github.com/user-attachments/assets/6e01f108-5674-48c8-b083-3bb94919a452)

## Basic Server Configuration

### Configure a Static IP Address on a Server

We configure a static IP address on a server because servers are meant to be reliable and always reachable. Clients, users, and other systems need to know exactly where to find the server. If a server uses DHCP, its IP address could change after a reboot, which would break network connections.

- IP - `192.168.0.10`
- Subnet Mask - `255.255.255.0`
- Default Gateway - `192.168.0.1`
- Prefered DNS Server - `127.0.0.1`
- Alternate DNS Server - `8.8.8.8`

<img width="1022" height="774" alt="image" src="https://github.com/user-attachments/assets/7d927509-d817-4871-b9c3-608bda05bacf" />

## Adding the Active Directory Domain Services

I installed Active Directory Domain Services to centrally manage users, computers, and security within a network, which allows the server to function as a Domain Controller.

![vmware_YywYqIFQhG](https://github.com/user-attachments/assets/49102d6a-32d8-430d-bf06-96bd9aae9c80)

## Installing Windows 10

I installed Windows 10 to act as a domain client, allowing me to test Active Directory functionality such as logging in with domain user accounts, resetting passwords, and verifying that Group Policy settings are applied correctly.

![vmware_6RK8QNCWUB](https://github.com/user-attachments/assets/cd69ddcb-f389-4bbe-be30-bef4a2e0051d)








