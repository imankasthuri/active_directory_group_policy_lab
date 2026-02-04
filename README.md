# Active Directory Group Policy Lab

## Installing Windows Server 2022

I installed Windows Server 2022 on a VMware virtual machine and selected the Windows Server 2022 Datacenter edition during installation.

![vmware_oUYd51ViEu](https://github.com/user-attachments/assets/6e01f108-5674-48c8-b083-3bb94919a452)

## Basic Server Configuration

### Configure a Static IP Address on a Server

We configure a static IP address on a server because servers are meant to be reliable and always reachable. Clients, users, and other systems need to know exactly where to find the server. If a server uses DHCP, its IP address could change after a reboot, which would break network connections.

- IP Address - `192.168.0.10`
- Subnet Mask - `255.255.255.0`
- Default Gateway - `192.168.0.1`
- Prefered DNS Server - `127.0.0.1`
- Alternate DNS Server - `8.8.8.8`

<img width="1282" height="804" alt="image" src="https://github.com/user-attachments/assets/bce77092-de04-4781-b832-4d5b0694aaee" />


## Adding the Active Directory Domain Services

I installed Active Directory Domain Services to centrally manage users, computers, and security within a network, which allows the server to function as a Domain Controller.

![vmware_YywYqIFQhG](https://github.com/user-attachments/assets/49102d6a-32d8-430d-bf06-96bd9aae9c80)

## Installing Windows 10

I installed Windows 10 to act as a domain client, allowing me to test Active Directory functionality such as logging in with domain user accounts, resetting passwords, and verifying that Group Policy settings are applied correctly.

![vmware_6RK8QNCWUB](https://github.com/user-attachments/assets/cd69ddcb-f389-4bbe-be30-bef4a2e0051d)

## Joining a Windows 10 Computer to a AD Domain

To connect to the Domain Controller, I configured the IPv4 settings on the Windows

- IP Address - `192.168.0.100`
- Subnet Mask - `255.255.255.0`
- Default Gateway - `192.168.0.1`
- Prefered DNS Server - `192.168.0.10`

<img width="1024" height="772" alt="image" src="https://github.com/user-attachments/assets/11486cff-887c-46ed-9326-c6c3fd951213" />


The preferred DNS server was set to `192.168.0.10` since the Domain Controller functions as the DNS server. Client computers rely on DNS records stored on the Domain Controller to locate domain services during logon, domain joining, and Group Policy processing.


![vmware_NSIMkUgbQJ](https://github.com/user-attachments/assets/3e6674c4-f991-4a3f-87e8-90ea0366cf1f)


## Creating User Accounts with AD

I created a user account named kasthuri.mudiyanselage under the Domain Users organizational unit that I created.


<img width="1277" height="800" alt="image" src="https://github.com/user-attachments/assets/1f3f1eee-7d64-4445-a730-2ee668a4ed0a" />


I used a Windows 10 client to log in to the user account that I created earlier. The screenshot below shows a successful login using the Windows 10 client.


![vmware_YLa9FGJHFz](https://github.com/user-attachments/assets/7f008dcc-8c44-44de-bc9b-4f3c1f2f4efe)

## Searching for Objects in Active Directory

In a real network, there can be hundreds or thousands of objects, making it very difficult to manually search through them. Therefore, searching is mainly used to efficiently manage users and computers, reset passwords, modify group memberships, and check object properties.

<img width="1282" height="799" alt="image" src="https://github.com/user-attachments/assets/b02b6b9e-feb8-480f-898d-e5e7d61c1f25" />

## Resetting User Passwords in Active Directory Users and Computers

Usually, we reset passwords for a few common reasons. Most of the time, a user has forgotten their password. Passwords are also reset when adding a new user so they can change it on first login, or in case of an account being locked out.

For maximum security, passwords must include:**

- Uppercase letters
- Lowercase letters
- Numbers
- Special characters

This ensures that passwords are strong and compliant with Active Directory policies.

![vmware_9QdJWUnHvg](https://github.com/user-attachments/assets/52c3caa8-4b6b-47e8-a92c-5f41d2cc059b)

### Unclock Account 

When a user is locked out due to multiple failed login attempts, an administrator can unlock the account without changing the existing password, allowing the user to log in again while keeping their current credentials.

![vmware_oCxaUD7hex](https://github.com/user-attachments/assets/6bb13db1-0860-4e31-a15d-9b6a5e529a8e)

After resetting the password, I tried to log in to the account using the new temporary password. Active Directory then prompted me to change the password again, because users are required to set their own password after an admin reset.


![vmware_4rLWWxEexX](https://github.com/user-attachments/assets/c4b20167-42ed-4431-b187-8caf2b22dcf2)








 
