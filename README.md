---
title: Home SIEM Lab
subtitle: Build Function SIEM system to collect logs, create rules and investigate alerts
author: Eli Young
project: 3 of 4
---

# Contents

1. Phase 1 — Deploy SIEM Platform
2. Phase 2 — Deploy Log Sources
3. Phase 3 — Create Detection Rules
4. Phase 4 - Simulate Attacks & Investigate

---

# Phase 1 - Deploy SIEM Platform

After comparing both options, I decided to use Wazuh for this project because it is free, open source, and provides the security monitoring capabilities needed for a home SIEM lab without the licensing costs associated with Splunk.

## Preparing the Virtualisation Environment

Before installing Wazuh, I needed a way to run a separate Linux server on my Mac. Since my host machine uses Apple Silicon, I chose **UTM** as the virtualisation tool.

I downloaded UTM from the official website:

https://mac.getutm.app/

UTM allows me to create and run virtual machines on macOS. This is useful for the SIEM lab because I can keep the Wazuh server separate from my main Mac system. If something goes wrong, I can rebuild the virtual machine without affecting my actual computer.

## Downloading Ubuntu Server ARM64

For the SIEM server VM, I downloaded Ubuntu Server for ARM from the official Ubuntu website:

https://ubuntu.com/download/server/arm

I chose the standard **Ubuntu Server ARM64** ISO because my host machine is a Mac with Apple Silicon. Apple Silicon uses the ARM64 architecture, so the ARM64 version of Ubuntu is the correct version to run inside UTM.

I downloaded the standard **Ubuntu Server** option, not the **64k page size** version, because the 64k page size image is intended for specific ARM server hardware with different memory requirements. For this home lab VM, the normal Ubuntu Server ARM image is the appropriate choice.

The downloaded file was an `.iso` file, which acts like a virtual installer disk. UTM will use this ISO to install Ubuntu Server inside the virtual machine.