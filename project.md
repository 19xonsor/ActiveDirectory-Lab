# Windows Active Directory Lab
Through the Windows and Active Directory room on TryHackMe, I’ve developed a foundational understanding of how Active Directory (AD) operates within a Windows environment. This hands-on lab introduced me to essential AD components such as domains, organizational units, group policy, Kerberos authentication, and user/group management. I gained experience with enumeration techniques, common misconfigurations, and practical exploitation tools that simulate real-world scenarios. This knowledge is highly relevant for roles in IT support and systems administration, as Active Directory is a core technology for managing users, computers, and access across enterprise networks. Documenting this lab allows me to reinforce what I’ve learned and demonstrate my technical growth in a structured and professional way.

## Knowledge that I learned from this project:
* Windows Domains
* Domain Controller, the server that runs active directory services.
* Centralised identity management
* Managing security policies
* Organizational Units.
* Managing Users in AD

## Notes
- Learned that both groups and OUs are used to classify users amd computers, but their purposes are entirely different:
* OUs are handy for applying policies to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. 
* Security Groups, on the other hand, are used to grant permissions over resources. For example, I will use groups if I want to allow some users to access a shared folder or network printer.
## Project walk-through
To access and configure users, groups or machine in Active Directory, I log in to the Domain Controller and run "Active Directory Users and Computers" from the start menu:
<img width="982" height="700" alt="image" src="https://github.com/user-attachments/assets/74633d6f-afe0-44cc-a220-6b0668ad4292" />

Inside the Active Directory Users and Computers, I can see users, computers and groups that exist in the domain. These objects are organised in Organizational Units which are container objects that allow me to classify users and machines. 
<img width="888" height="555" alt="image" src="https://github.com/user-attachments/assets/6dc76a4e-1c50-4ba5-a5ab-34a58cc308df" />

THIS IS A VIDEO -- 
Under THM unit, I created a new Organizational Unit called Students to add as new department of organisation.

![Untitledvideo-MadewithClipchamp2-ezgif com-crop](https://github.com/user-attachments/assets/55ca789a-191a-4189-9972-fc2a5d32f064)

Inside each Organizational Unit, I performed simple tasks like creating, deleting or modifying the users as need. Also, reset passwords if needed which is pretty useful for helpdesk.
<img width="942" height="572" alt="Screenshot 2025-08-05 154915" src="https://github.com/user-attachments/assets/965ec14d-f2ee-41d9-8d94-81a2c04a4bc7" />


## Managing Users in AD
There was changes have happended to the business. As a domain administrator, I checked the existing AD OUs and users. I noticed that there was extra OUs and users, I have been told to remove it from the domain.
To delete them I went to the Advance Features in the View menu to enable it.
<img width="967" height="528" alt="image" src="https://github.com/user-attachments/assets/11121d50-cc9d-4061-b0d4-9625c1013da6" />

Then I went to the Organizational Unit "Students" properties, in object I disabled the accidental deletion in order to delete it.
<img width="512" height="580" alt="Screenshot 2025-08-05 162205" src="https://github.com/user-attachments/assets/a4f3d1b1-7470-424e-8b39-13f4b69ef837" /> <img width="492" height="192" alt="Screenshot 2025-08-05 162349" src="https://github.com/user-attachments/assets/c99248f8-634c-4283-871b-cb7ecd7e69b4" />

I grant IT SUPPORT the privileges to reset other low-privilege Users Passwords. According to my organisational chart, I put the IT support in charge of resetting passwords over sales, marketing and Management OUs. By delegate the control over OU to IT SUPPORT.
<img width="404" height="493" alt="image" src="https://github.com/user-attachments/assets/60afada0-3cf9-43d0-b11c-b7b90b5acdd7" /> <img width="751" height="730" alt="image" src="https://github.com/user-attachments/assets/3641571f-8760-44c2-bed1-66fd6495e791" /><img width="637" height="499" alt="Screenshot 2025-08-05 163514" src="https://github.com/user-attachments/assets/d6012355-e4bd-47f0-97c4-afad06839670" />

I remote connect to Phillip (IT SUPPORT) and test Phillip's privilege to reset Sophie's password. I used Powershell to do a password reset because he doesn't have the privileges to open Active Directory Users and Computers.   
<img width="884" height="123" alt="image" src="https://github.com/user-attachments/assets/269324c2-3337-4971-9186-b2582acbfe11" />

## Managing Computers in AD

By managing Computers in AD, I learned how servers work and how to locate laptops and PCs in the network.
<img width="971" height="537" alt="image" src="https://github.com/user-attachments/assets/dc7386d2-a783-4f06-9f34-b6510af9f768" />

To organize the machines in the active directory domain, I made an excellent starting point is to segregate the devices according to their use. I divided into three following categories: 
*  Workstations: it is most common in AD. Each user in the domain will likely be logging into a workstation.
*  Servers: The second most common device within AD. Servers are generally used to provide services to users or other servers.
*  Domain Controllers: Third common within an AD and already in an OU created by Windows. Domain controller allow you to manage the active directory domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.
<img width="967" height="472" alt="image" src="https://github.com/user-attachments/assets/1673ff1c-ac55-4b9f-980a-e9bd172df9f5" />

After I made the OUs, I moved the personal computers and laptops to the Workstations OU and the servers to the Servers OU from the Computers container. Doing so will allow us to configure polices for each OU later.
<img width="721" height="288" alt="image" src="https://github.com/user-attachments/assets/4ad0c331-8faa-469b-aacd-e73f51c95044" />
<img width="797" height="264" alt="Screenshot 2025-08-09 193138" src="https://github.com/user-attachments/assets/b89294db-9950-48dc-a5e3-003ca5084368" />

## Group Policies 
After organised users and computers in OUs. Now we can able to deploy different policies for each OU individually. That way, we can push different configurations and security baselines to users depending on their department.

Windows Managers such policies as Group Policy Objects allow me to set a baseline on specific machines and identities.
