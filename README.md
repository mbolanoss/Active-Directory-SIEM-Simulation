# Active Directory

## Objective

This project simulates a scenario in which an Active Directory environment is configured to generate telemetry for ingesting related events into a SIEM. The main objective is to create a Domain Controller (Windows Server 2022) and a computer (Windows 10) that will be the target of the attacks. Both machines will be subscribed to the DC, and they will send events to a [Splunk](https://www.splunk.com/) server that will act as the SIEM. Additionally, a Kali Linux machine will be used to simulate the attacks through brute force logins. Along with these attacks, some security tests will be executed using the [Atomic Red Team](https://atomicredteam.io/learn-more/) library. This setup allows for a comprehensive simulation of an Active Directory environment under attack, providing valuable insights into the detection capabilities of the SIEM system.

### Skills Learned

- Comprehensive understanding and practical application of SIEM concepts.
- Configuration of an Active Directory environment.
- Installation and setup of a Windows Server 2022 machine.
- Execution of brute force password guessing attacks.
- Conducting security tests on a Windows 10 machince.

### Tools Used

- Splunk as the SIEM system for log ingestion and analysis.
- Windows Server 2022 as the Active Directory Domain Controller.
- Atomic Red Team library to run security tests on a Windows 10 machine.
- Kali Linux as the attacker machine.

## Steps
To provide a general overview of the project, here is the network diagram that represents the environment developed in this project:

![Diagrama](https://github.com/mbolanoss/Active-Directory/assets/53063734/23cce258-43d0-4297-8065-2bc2e5882e22)

*Ref 1: Network Diagram*

Now, here is the general workflow of the project:
1. The Active Directory Domain Controller (DC) is hosted on a Windows Server 2022 machine.
2. A Windows 10 machine subscribes to the Active Directory DC and acts as the target of the attacks.
3. Both the DC and Windows 10 machines have Sysmon installed to generate telemetry.
4. A Splunk Server is configured to receive events from the DC and Windows 10 machines.
5. A brute force password guessing attack against the target machine is executed from the Kali Linux machine.
6. A security test is executed on the Windows 10 machine, related to the [T1136.001 MITRE ATT&CK](https://attack.mitre.org/techniques/T1136/001/) technique, which attempts to create a rogue local account.
