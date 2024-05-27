# Active Directory

## Objective

This project simulates a scenario in which an Active Directory environment is configured to generate telemetry for ingesting related events into a SIEM. The main objective is to create a Domain Controller (Windows Server 2022) and a computer (Windows 10) that will be the target of the attacks. Both machines will be subscribed to the DC, and they will send events to a [Splunk](https://www.splunk.com/) server that will act as the SIEM. Additionally, a Kali Linux machine will be used to simulate the attacks through brute force logins. Along with these attacks, some security tests will be executed using the [Atomic Red Team](https://atomicredteam.io/learn-more/) library. This setup allows for a comprehensive simulation of an Active Directory environment under attack, providing valuable insights into the detection capabilities of the SIEM system.

### Skills Learned

- Comprehensive understanding and practical application of SIEM concepts.
- Configuration of an Active Directory environment.
- Installation and setup of a Windows Server 2022 machine.
- Conducting brute force password guessing attacks.
- Execution of security tests on a Windows 10 machince.

### Tools Used

- Splunk as the SIEM system for log ingestion and analysis.
- Windows Server 2022 as the Active Directory Domain Controller.
- Atomic Red Team library to run security tests on a Windows 10 machine.
- Kali Linux as the attacker machine.

## Steps

Example below.

*Ref 1: Network Diagram*
