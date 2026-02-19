# Active Directory Group Policy Lab

## Installing Windows Server 2022

- I installed Windows Server 2022 on a VMware virtual machine and selected the Windows Server 2022 Datacenter edition during installation.

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

- I installed Active Directory Domain Services to centrally manage users, computers, and security within a network, which allows the server to function as a Domain Controller.

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


- The preferred DNS server was set to `192.168.0.10` since the Domain Controller functions as the DNS server. Client computers rely on DNS records stored on the Domain Controller to locate domain services during logon, domain joining, and Group Policy processing.

- I checked the Windows Server connectivity using the ping command, and it successfully connected to my Domain Controller.

- This confirms that the client computer can communicate with the Domain Controller over the network, which is essential for domain login, Group Policy application, and other Active Directory operations. A successful ping indicates that the IP configuration, subnet mask, gateway, and basic network connectivity are all correctly set up.

![vmware_87vkpXJfJ2](https://github.com/user-attachments/assets/16a2802c-9d46-4b0a-8d6e-75ec9159a7b9)


## Creating User Accounts with AD

- I created a user account named kasthuri.mudiyanselage under the Domain Users organizational unit that I created.


<img width="1277" height="800" alt="image" src="https://github.com/user-attachments/assets/1f3f1eee-7d64-4445-a730-2ee668a4ed0a" />


- I used a Windows 10 client to log in to the user account that I created earlier. The screenshot below shows a successful login using the Windows 10 client.


![vmware_YLa9FGJHFz](https://github.com/user-attachments/assets/7f008dcc-8c44-44de-bc9b-4f3c1f2f4efe)

## Searching for Objects in Active Directory

- In a real network, there can be hundreds or thousands of objects, making it very difficult to manually search through them. Therefore, searching is mainly used to efficiently manage users and computers, reset passwords, modify group memberships, and check object properties.

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

### Unlock Account 

- When a user is locked out due to multiple failed login attempts, an administrator can unlock the account without changing the existing password, allowing the user to log in again while keeping their current credentials.

![vmware_oCxaUD7hex](https://github.com/user-attachments/assets/6bb13db1-0860-4e31-a15d-9b6a5e529a8e)

- After resetting the password, I tried to log in to the account using the new temporary password. Active Directory then prompted me to change the password again, because users are required to set their own password after an admin reset.


![vmware_4rLWWxEexX](https://github.com/user-attachments/assets/c4b20167-42ed-4431-b187-8caf2b22dcf2)


## Disabling and Deleting User Accounts with Active Directory

- In the video below, I created a separate Organizational Unit (OU) for disabled accounts. I then disabled a user account and moved it into the Disabled OU. After that, I attempted to log in using that account to verify that access was successfully blocked.

![vmware_Ymdy7sV8M2](https://github.com/user-attachments/assets/6298bb60-9864-4fe2-9f1f-c9a87a5e6136)

## Creating and Linking Group Policy Objects (GPOs)

- I created a Group Policy Object (GPO) and linked it to the relevant Organizational Units (OUs), specifically Domain Computers and Domain Users. I also added the Administrators group to the security filtering, ensuring the settings apply to them as well.

![vmware_sOLe9yaQHy](https://github.com/user-attachments/assets/6aec8baf-da76-4bd8-9467-73f48464a721)

- By using the Delegation method, I can grant read, write, and delete permissions to standard users for a specific GPO without adding them to the Administrators group.

![vmware_rMcL8eUAzq](https://github.com/user-attachments/assets/aeea5671-0952-4905-9acb-0a602b859371)

## Deploying a Desktop Background to domain with a GPO (Group Policy Object)

- I Created a folder on the C: drive to store desktop background images. Configured advanced sharing permissions on the folder to allow access for Authenticated Users, ensuring all domain users can read the files.

<img width="1911" height="919" alt="image" src="https://github.com/user-attachments/assets/3d73ff99-e99e-44d4-92be-e47676747e46" />

- I created a new GPO named ‘Desktop Background’ under my domain, edited it, and enabled the desktop wallpaper setting, ensuring that users had the necessary permissions to access the image.

<img width="1910" height="917" alt="image" src="https://github.com/user-attachments/assets/6ae9a286-a59c-47cb-9684-54cef69bbfed" />

- After editing the GPO, I ran `gpupdate /force` in Command Prompt to immediately apply the changes. I then signed out of the Administrator account and logged in as the test user to verify that the Group Policy settings were applied correctly.

![vmware_UFWd6jcxFy](https://github.com/user-attachments/assets/67fa4b5b-3352-42d9-bb03-c6a3591d6d0f)

## Setting up an Logon Banner (Interactive Logon)

- Created a new GPO named ‘Interactive Logon’ and configured the Interactive Logon title and message to display a custom security banner before user sign-in.

<img width="1550" height="917" alt="image" src="https://github.com/user-attachments/assets/f9395109-7f68-47ac-90b5-bdb89360474e" />

<img width="1545" height="919" alt="image" src="https://github.com/user-attachments/assets/24bc14a0-846c-4e93-9ba7-657d1222d480" />

## Deploying Software with Group Policy

- Deployed 7-Zip (v17.01) to the Administrator account using Group Policy to verify successful software installation.

<img width="1550" height="876" alt="image" src="https://github.com/user-attachments/assets/3ebbb871-b6aa-4f98-9b8c-2c0f40c14c8f" />

## Configuring Domain Password and Account Lockout Policies with Group Policy

- Configured password policies: the system remembers the last 24 passwords to prevent reuse, requires users to change their password every 90 days, allows users to change their password at any time if forgotten, and enforces a minimum password length of 14 characters for enhanced security.

<img width="1374" height="728" alt="image" src="https://github.com/user-attachments/assets/7d404ab7-c910-4b1e-a9ed-ddfdabab4cbc" />

- In the account lockout policy, a user is allowed 3 login attempts. If the user fails all 3, they must wait 15 minutes before trying again. With the ‘Reset account lockout counter’ setting, if the user fails 2 attempts and returns after the reset time (e.g., 10 minutes), the counter resets, and they have 3 full attempts again.

<img width="1243" height="715" alt="image" src="https://github.com/user-attachments/assets/2053e411-b525-4d03-b643-042ba1485d1c" />

I tested the account lockout policy by entering an incorrect password three times. After the third failed attempt, the account was successfully locked out, confirming that the policy is working correctly.

<img width="1080" height="741" alt="image" src="https://github.com/user-attachments/assets/ba0a6958-d17e-428d-bb07-326ef1a59610" />

After the account was locked, I used the Administrator account to unlock the user account in Active Directory. The user was then able to log in successfully without any issues.

<img width="1018" height="782" alt="image" src="https://github.com/user-attachments/assets/b9f13326-82c6-4d48-af66-193144b1852b" />















 
