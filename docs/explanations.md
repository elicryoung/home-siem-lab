## What is a SIEM?

Before starting this project, I wanted to understand what a SIEM actually is and why organisations use it.

SIEM stands for Security Information and Event Management. In simple terms, it's a platform that collects logs and security events from different systems and brings them together in one place. Instead of checking multiple devices individually, security analysts can use a SIEM to monitor activity, investigate suspicious behaviour, and detect potential threats.

I think of a SIEM as a central hub for security monitoring. It collects information from computers, servers, applications, and network devices, then helps analysts search through that data and identify unusual activity.

In this project, I'll be using Splunk as my SIEM. The goal is to collect logs, analyse events, and gain a better understanding of how security teams monitor and investigate activity within a network.

# Splunk

Splunk is a Security Information and Event Management (SIEM) platform used to collect, store, search, and analyse logs from different systems. These logs can come from computers, servers, applications, firewalls, and network devices.

The main purpose of Splunk is to help security analysts investigate events and detect suspicious activity. Once logs are collected, Splunk indexes the data so it can be searched quickly using its query language. Analysts can also create dashboards, visualisations, and automated alerts.

For example, if a user repeatedly fails to log in to a system, Splunk can help identify the event and alert an analyst that a potential brute-force attack may be occurring.

## Pros

- Widely used in industry
- Powerful search capabilities
- Excellent dashboards and visualisations
- Large community and learning resources
- Valuable skill for cybersecurity careers

## Cons

- Expensive for large deployments
- Resource intensive
- Can be difficult for beginners to configure
- Many advanced features require paid licences