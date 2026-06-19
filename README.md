---
title: Home SIEM Lab
subtitle: Build a functional SIEM system to collect logs, create rules, and investigate alerts
author: Eli Young
project: 3 of 4
---

# Contents

1. Phase 1 — Deploy SIEM Platform
2. Phase 2 — Deploy Log Sources
3. Phase 3 — Create Detection Rules
4. Phase 4 — Simulate Attacks & Investigate

---

# Phase 1 — Deploy SIEM Platform

After comparing Wazuh and Splunk, I decided to use Wazuh for this project. Splunk is a strong platform, but Wazuh made more sense for this lab because it is free, open source, and gives me the SIEM features I need without dealing with licensing costs.

The goal for this phase is to deploy the main SIEM server. This server will eventually collect logs from other machines, store security events, and provide a dashboard for viewing alerts and investigating activity.

## VM Setup

Since I am using a Mac with Apple Silicon, I used **UTM** to create a Linux virtual machine. I downloaded UTM from:

https://mac.getutm.app/

For the operating system, I downloaded the standard **Ubuntu Server ARM64** ISO from:

https://ubuntu.com/download/server/arm

I chose the ARM64 version because Apple Silicon uses ARM architecture. I used the standard Ubuntu Server image rather than the 64k page size version because the normal ARM64 image is the better fit for this home lab VM.

I created a VM named `Wazuh-Server`.

### Virtual Machine Settings

| Setting | Value | Why I used it |
|---|---:|---|
| Engine | QEMU | UTM uses QEMU to run the virtual machine. |
| Architecture | ARM64 / aarch64 | This matches the Apple Silicon architecture on my Mac. |
| Operating System | Linux | Ubuntu Server is a Linux operating system. |
| Memory | 4 GB | Enough memory to run Ubuntu and begin setting up Wazuh. |
| CPU | 4 cores | Gives the VM enough processing power without taking over the Mac. |
| Storage | 40 GB | Gives enough space for Ubuntu, Wazuh, logs, and lab data. |
| Boot Image | Ubuntu Server ARM64 ISO | Used as the installer disk for Ubuntu Server. |

This VM is separate from my main Mac, which makes the lab safer and easier to rebuild if something goes wrong. (see img 1.1 and img 1.2)

## Ubuntu Server Installation

I installed Ubuntu Server onto the `Wazuh-Server` VM using the default guided installation options.

During the install, I used the standard Ubuntu Server option instead of the minimized version. I left networking on DHCP, used the full 40 GB virtual disk, and enabled OpenSSH server.

The VM automatically received this IP address:

`192.168.64.2`

I enabled SSH so I can connect to the server from my Mac terminal later. This will make the Wazuh installation easier because I can copy and paste commands instead of typing everything directly into the UTM console.

After Ubuntu finished installing, I removed the Ubuntu ISO from the VM settings so the machine would boot from the installed system instead of returning to the installer.

## System Update

After logging into Ubuntu, I updated the server using:

`sudo apt update && sudo apt upgrade -y`

This updated the package lists and installed available updates before adding Wazuh.

At this point, the Ubuntu Server VM is installed, updated, and ready for the Wazuh installation.

The next step is to install Wazuh and confirm that the Wazuh dashboard is reachable from my Mac browser.