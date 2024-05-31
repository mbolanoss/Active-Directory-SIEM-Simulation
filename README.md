# Active Directory SIEM Simulation

## Objective

This project simulates a scenario in which an Active Directory environment is configured to generate telemetry for ingesting related events into a SIEM. The main objective is to create a Domain Controller (Windows Server 2022) and a computer (Windows 10) that will be the target of the attacks. Both machines will be subscribed to the DC, and they will send events to a [Splunk](https://www.splunk.com/) server that will act as the SIEM. Additionally, a Kali Linux machine will be used to simulate the attacks through brute force password guessing. Along with these attacks, some security tests will be executed using the [Atomic Red Team](https://atomicredteam.io/learn-more/) library. This setup allows for a comprehensive simulation of an Active Directory environment under attack, providing valuable insights into the detection capabilities of the SIEM system.

### Skills Learned

- Comprehensive understanding and practical application of SIEM concepts.
- Configuration of an Active Directory environment.
- Installation and setup of a Windows Server 2022 machine.
- Execution of brute force password guessing attacks.
- Conducting security tests on a Windows 10 machine.

### Tools Used

- Splunk Server as the SIEM system for log ingestion and analysis, hosted in a Ubuntu Server machine.
- Windows Server 2022 as the Active Directory Domain Controller.
- Atomic Red Team library to run security tests on a Windows 10 machine.
- Kali Linux as the attacker machine.
- [Crowbar]([https://www.kali.org/tools/crowbar/](https://github.com/galkan/crowbar)) as the brute forcing tool.

## Steps
To provide a general overview of the project, here is the network diagram that represents the environment developed in this project:

![Diagrama](https://github.com/mbolanoss/Active-Directory/assets/53063734/23cce258-43d0-4297-8065-2bc2e5882e22)

*Ref 1: Network Diagram*

Now, here is the general workflow of the project:
1. The Active Directory Domain Controller (DC) is hosted on a Windows Server 2022 machine.
2. A Windows 10 machine subscribes to the Active Directory DC and acts as the target of the attacks.
3. Both the DC and Windows 10 machines have Sysmon installed to generate telemetry.
4. A Splunk Server is configured to receive events from the DC and Windows 10 machines (Universal Forwarders).
5. A brute force password guessing attack against the target machine is executed from the Kali Linux machine.
6. A security test is executed on the Windows 10 machine, related to the [T1136.001 MITRE ATT&CK](https://attack.mitre.org/techniques/T1136/001/) technique, which attempts to create a rogue local account.

Now, here are some screenshots of the process and the obtained results:

### Splunk Server and Universal Forwarders setup

![splunk server running](https://github.com/mbolanoss/Active-Directory/assets/53063734/973518ee-2bc2-4023-a6bd-ecb71edcf1f0)

*Ref 2: Splunk Server running on a Ubuntu server machine.*

![splunk initial dashboard](https://github.com/mbolanoss/Active-Directory/assets/53063734/ef7ddbde-e4f6-448e-b87d-ffdfed49d288)

*Ref 3: Splunk Server dashboard.*

![splunk dashboard 2 hosts](https://github.com/mbolanoss/Active-Directory/assets/53063734/910dc4a0-cdf4-4f05-9f94-0027b54dddc6)

*Ref 4: Both Active Directory DC and target PC are ingesting events into the Splunk Server.*

### Active Directory configuration

![AD configured](https://github.com/mbolanoss/Active-Directory/assets/53063734/d211c0e2-5759-4527-b795-92fea04b7f36)

*Ref 5: Configured AD on a Windows Server 2022 machine.*

![2 org unit created](https://github.com/mbolanoss/Active-Directory/assets/53063734/9424bda1-861a-404e-9019-aa27630e56be)

*Ref 6: HR and IT Organizational Units are created with 1 user each.*

![joined mbolanoss local from win10](https://github.com/mbolanoss/Active-Directory/assets/53063734/8d864248-ba45-4717-bb9a-9a98f4d8b2a4)

![sign in as msmith](https://github.com/mbolanoss/Active-Directory/assets/53063734/95877bf9-ace8-4e6b-b516-6725ba7bd27e)

*Ref 7: The Windows 10 machine joins the AD server so one of the created users can log in.*

### Bruteforce password guessing attack

![rdp users](https://github.com/mbolanoss/Active-Directory/assets/53063734/2bd5b2a9-e487-4160-8058-69d663d6d15f)

*Ref 8: Before the attack is executed, both users are given permissions to connect remotely using RDP.*

![bruteforce passwords](https://github.com/mbolanoss/Active-Directory/assets/53063734/f55f7442-4f75-47a7-bb62-fbc67248a6ad)

*Ref 8: On the Kali Linux machine, a password list is created to attempt logging in using Crowbar.*

![rdp bruteforce success](https://github.com/mbolanoss/Active-Directory/assets/53063734/07f71081-5195-4b4f-845f-55507021da2b)

*Ref 9: Brute force attack against the Windows 10 machine is successful.*

![splunk successful login](https://github.com/mbolanoss/Active-Directory/assets/53063734/d4f8cdaf-2962-4e6e-8f24-e7866ed46b29)

*Ref 10: Finally, the successful attack is displayed in the Splunk dashboard.*

### Atomic Red Team test execution

![atomic red team create local account](https://github.com/mbolanoss/Active-Directory/assets/53063734/ba6c64b7-82e0-45c1-8a52-63a0503b50f2)

*Ref 10: Using the Atomic Red Team library, a script is executed to create a rogue local account with "NewLocalUser" as user.*

![splunk atomic red team account](https://github.com/mbolanoss/Active-Directory/assets/53063734/2b8971fe-9c48-4640-8ca9-236d5647b229)

*Ref 11: Now, the account creation can be seen in the Splunk dashboard.*
