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

- After the account was locked, I used the Administrator account to unlock the user account in Active Directory. The user was then able to log in successfully without any issues.

<img width="1018" height="782" alt="image" src="https://github.com/user-attachments/assets/b9f13326-82c6-4d48-af66-193144b1852b" />

## Deploying Fine Grained Password Policies (PSOs)

- I created an Active Directory group named “7 Day Password Age” and added specific users to it. This group will be targeted by a Fine-Grained Password Policy, allowing these users to have a different password age than the default domain policy.

<img width="951" height="657" alt="image" src="https://github.com/user-attachments/assets/55d5ba32-3293-4afa-b7b7-a2cd02e0e317" />

- To implement a custom password policy for a particular group, I used ADSI Edit to create a 7-Day Password Settings Object (PSO). Within the Password Settings Container, I configured the password requirements and applied the PSO to the targeted users, overriding the default domain password policy while leaving other users unaffected.

When creating an object, I used these values:

- Common Name: 7DaysPasswordAge
- Password Settings Precedence: 1 (If we create more than one PSO, Active Directory needs to know which PSO to apply; lower number = higher priority)
- Password Reversible Encryption for user accounts: FALSE (The user’s password is stored as a hash and is not decryptable)
- Password History Length for user accounts: 24
- Password Complexity Status for user accounts: TRUE
- Minimum Password Length for user accounts: 14
- Minimum Password Age for user accounts: 00:00:00:00
- Maximum Password Age for user accounts: 07:00:00:00
- Lockout Threshold for user accounts: 3
- Observation Window for lockout of user accounts: 00:00:15:00
- Lockout Duration for locked-out user accounts: 00:00:15:0015:00

<img width="1036" height="774" alt="image" src="https://github.com/user-attachments/assets/f32a3b23-0cbb-48fe-81bc-03e61272609f" />

- The Fine-Grained Password Policy (PSO) was applied to the “7 Day Password Age” group, ensuring that all users in this group follow the custom password settings instead of the default domain policy.

<img width="1550" height="909" alt="image" src="https://github.com/user-attachments/assets/1eba855a-9802-4be6-ba76-2cd2bb697998" />

- Successfully verified that the Fine-Grained Password Policy (7-day maximum password age) is applied by checking the password expiration date using PowerShell.

```powershell
Import-Module ActiveDirectory

Get-ADUser -Filter {GivenName -like "Kaiser"} -Properties "msDS-UserPasswordExpiryTimeComputed" |
Select-Object Name, @{
    Name="ExpiryDate";
    Expression={[datetime]::FromFileTime($_."msDS-UserPasswordExpiryTimeComputed")}
}
```
<img width="997" height="289" alt="image" src="https://github.com/user-attachments/assets/44d4d616-48f8-4e6f-8bde-266296a17abe" />

## Configuring Windows Firewall with Group Policy

- First, I created a new Group Policy Object (GPO) called “Firewall Test 1.” Within this GPO, I created a new Inbound Firewall Rule and selected the Port option.

<img width="1225" height="765" alt="Screenshot 2026-03-01 220424" src="https://github.com/user-attachments/assets/87ee8e19-35f4-4bbb-a9c2-4f8642ad3882" />

- In my lab, I troubleshooted TCP inbound traffic on port 1234. For this exercise, port 1234 was chosen purely as an example to demonstrate how to create and test Windows Defender Firewall inbound rules.

<img width="1198" height="746" alt="Screenshot 2026-03-01 220924" src="https://github.com/user-attachments/assets/a123ce68-9989-4d85-abe5-dd9ef9fdbf98" />

- After configuring the firewall rule in the “Test 1234” Group Policy Object (GPO) and linking it to the appropriate Organizational Unit (OU), I verified that the policy was successfully applied to the target computer by opening Command Prompt and running the gpresult /r command, then confirming that the “Test 1234” GPO appeared under the Applied Group Policy Objects section in Computer Settings, which indicated that the firewall rule was successfully applied.

<img width="1499" height="862" alt="Screenshot 2026-03-03 190939" src="https://github.com/user-attachments/assets/20abc717-009e-4cd7-87f5-1f478419f1b8" />

## Configuring Windows Registry Settings with Group Policy (GPOs)

- In this GPO, I am configuring a registry setting that allows users to right-click any file and select “Open with Notepad.” Adding this option makes it faster and reduces the number of clicks required to open files. This is especially useful for administrators, who frequently open log files, scripts, and configuration files. Having “Open with Notepad” directly available in the context menu improves efficiency and convenience during troubleshooting and system management tasks.

- `HKCR` - Controls file types in windows
- `*` - Means all files
- `Shell` - The right click menue
- `Open With Notepad` - The menu item name you see when you right-click.
- `command` - In the registry, command is the key that actually tells Windows what to do when you click a right-click menu item.
- `notepad.exe` - the program to run
- `%1` - the file you right-clicked

<img width="1232" height="698" alt="image" src="https://github.com/user-attachments/assets/86f0621c-1653-4162-9bc7-79a427267bbb" />
                                                      
- After applying this registry setting, I successfully verified that it was working by right-clicking a file and confirming that the “Open With Notepad” option appeared in the context menu and opened the selected file in Notepad.

<img width="435" height="451" alt="image" src="https://github.com/user-attachments/assets/9ec41405-77cb-4914-ae40-e73437fcadce" />

## Configuring Roaming Profiles for User Accounts

- I created a shared folder named Profiles$ and added the dollar sign ($) at the end of the share name to configure it as a hidden share. This prevents it from appearing when users browse available network shares, while still allowing access to authorized users.

<img width="1546" height="880" alt="image" src="https://github.com/user-attachments/assets/39076ba7-0383-4df0-a39a-c80017e67f34" />

- I removed the Users group from the share permissions for security reasons. Allowing general user access could enable users to view other users’ files and documents, which would pose a security risk.

<img width="764" height="519" alt="image" src="https://github.com/user-attachments/assets/9b689361-a4a9-47a2-99b2-a4fb592fd990" />

- I created a group called Roaming Profile Users to simplify user management. Instead of configuring permissions for each user individually, I added them to a single group, allowing me to manage access centrally and more efficiently.
  
<img width="922" height="658" alt="image" src="https://github.com/user-attachments/assets/695f4823-6da9-4aef-b5db-4454a1602d10" />

- I added the user account Kasthuri Mudiyanselage Iman Malsha Kasthuri to the Roaming Profile Users group.

<img width="844" height="552" alt="image" src="https://github.com/user-attachments/assets/72d83ec6-6bfe-46c3-9ddf-58adc9aec4ba" />

- I configured advanced permissions for the profile folder, granting List Folder / Read Data and Create Folders / Append Data, and set them to apply to this folder only.

<img width="1400" height="838" alt="image" src="https://github.com/user-attachments/assets/e9a542da-9b0b-4fc3-83e6-814e1644a97e" />

<img width="765" height="520" alt="image" src="https://github.com/user-attachments/assets/ffbcb7c6-8515-417c-9400-e11e079cd123" />

- I specified the profile path for the user Kasthuri Mudiyanselage Iman Malsha Kasthuri as `\\ITFDC01\Profile$\%username%`. This tells Windows where to store the user’s profile data on the network. The `%username%` variable automatically creates a separate folder for each user.

<img width="920" height="799" alt="image" src="https://github.com/user-attachments/assets/b8f29e90-8ce6-4f1f-9e10-1c3fdca64cc5" />

Problem:

- When I initially troubleshooted the roaming profile, it did not appear in System Settings → User Profiles on my user account.

Solution:

- I discovered that changes to roaming profiles do not take effect until the current session is signed out. After signing out of the administrator account and logging back in, the changes were applied, and the roaming profile appeared correctly.

<img width="1548" height="879" alt="image" src="https://github.com/user-attachments/assets/f0179d4f-0228-4f37-8527-d1842831adcb" />

- I tried to access the user profile using my administrator account, but it showed Access Denied, which indicates that my security configuration is working correctly. This ensures that each user’s data remains private and secure.

<img width="1122" height="592" alt="image" src="https://github.com/user-attachments/assets/883d7eba-069a-4d5e-8d95-0a7ca87db7b1" />

## How to automatically map network share drives with Group Policy

- First, I created two groups, Group A and Group B, and added users to each group.

<img width="908" height="631" alt="image" src="https://github.com/user-attachments/assets/305d1ba1-945c-43c2-812f-c58bf2cc950f" />

- I created two network file shares, Share A and Share B, and configured permissions so that Group A has access to Share A, and Group B has access to Share B. This ensures that only the intended users in each group can access their respective shares.
  
<img width="855" height="579" alt="image" src="https://github.com/user-attachments/assets/750f3e60-6abd-41a2-9f4b-0b94acd4202d" />

- I confirmed that Group A users cannot access Share B, and Group B users cannot access Share A, ensuring that the file permissions are working as intended.

<img width="1124" height="590" alt="image" src="https://github.com/user-attachments/assets/9b6fd6de-5fa4-4857-8081-6ef7550c8b7f" />

- I configured a Group Policy Object (GPO) to map network drives for the two domain groups. Users in Group A will automatically have the Group A shared folder mapped, and users in Group B will automatically have the Group B shared folder mapped upon login. This ensures correct access and convenience for users.

<img width="1547" height="881" alt="image" src="https://github.com/user-attachments/assets/556b8eca-d548-4cc3-91b1-90c8b7dec7bc" />

- I assigned Read-only permissions to Authenticated Users. This allows all users in the domain to see and access the folder, but they cannot make any changes to the files.

<img width="1546" height="880" alt="image" src="https://github.com/user-attachments/assets/42521af3-f080-4b6b-b15e-46fbfc886ec0" />

I successfully mapped the shared folder \\ITFDC01\Group A to a network drive, so that members of Group A can access it automatically.

<img width="1546" height="489" alt="image" src="https://github.com/user-attachments/assets/1f805345-a5fa-48f2-acc6-ea920230a353" />

## Listing AD Users with Powershell

- The screenshot and PowerShell code below show how to list users from Active Directory. The Get-ADUser cmdlet is used with a filter to select all users, and the -ResultSetSize 100 parameter limits the output to 100 users. This is especially useful in larger domains to prevent flooding the console with too many results at once, making it easier to read and manage the output.
```powershell
# Import the active directory module
Import-Module ActiveDirectory

# List all AD users (Were a max limit of 100 users - this is important for larger domain)
Get-ADUser -Filter * -ResultSetSize 100
```
<img width="1135" height="823" alt="image" src="https://github.com/user-attachments/assets/098ec0e7-3587-4d9b-a9cc-fcf61f83ad2a" />

- This PowerShell script imports the Active Directory module and lists up to 100 AD users. It retrieves key properties including Name, UserPrincipalName, Enabled status, and LastLogon. Limiting the result set to 100 users prevents overwhelming the console in larger domains, making the output easier to review and manage.

```powershell
# Import the active directory module
Import-Module ActiveDirectory

# List all AD users (Were a max limit of 100 users - this is important for larger domain)
Get-ADUser -Filter * -ResultSetSize 100 -Properties lastLogon | Select-Object Name, UserPrincipalName, Enabled, lastLogon
```
<img width="996" height="579" alt="image" src="https://github.com/user-attachments/assets/a10ea3d6-b8c7-421f-819e-5546804b5412" />
















































 
