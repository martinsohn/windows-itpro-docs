---
title: Enhancing cache performance
manager: aaroncz
description: How to enhance performance on a virtual machine used with Microsoft Connected Cache for ISPs
ms.prod: windows-client
author: amyzhou
ms.author: amyzhou
ms.topic: reference
ms.technology: itpro-updates
ms.date: 12/31/2017
---

# Enhancing cache performance

To make sure you're maximizing the performance of your cache node, review the following information:

#### OS requirements

The Microsoft Connected Cache module is optimized for Ubuntu 20.04 LTS. Install Ubuntu 20.04 LTS on a physical server or VM of your choice.

#### NIC requirements

- Multiple NICs on a single MCC instance are supported using a *link aggregated* configuration.
- 10 Gbps NIC is the minimum speed recommended, but any NIC is supported.

#### Drive performance

The maximum number of disks supported is 9. When configuring your drives, we recommend SSD drives as cache read speed of SSD is superior to HDD. In addition, using multiple disks is recommended to improve cache performance. 

RAID disk configurations are discouraged as cache performance will be impacted. If using RAID disk configurations, ensure striping.

### Hardware configuration example

There are many hardware configurations that suit Microsoft Connected Cache. As an example, a customer has deployed the following hardware configuration and is able to achieve a peak egress of about 35 Gbps:

**Dell PowerEdge R330**

- 2 x Intel(R) Xeon(R) CPU E5-2630 v3 @ 2.40 GHz, total 32 core
- 48 GB, Micron Technology 18ASF1G72PDZ-2G1A1, Speed: 2133 MT/s
- 4 - Transcend SSD230s 1 TB SATA Drives
- Intel Corporation Ethernet 10G 2P X520 Adapter (Link Aggregated)

## Enhancing virtual machine performance

In virtual environments, the cache server egress peaks at around 1.1 Gbps. If you want to maximize the egress in virtual environments, it's critical to change two settings.

### Virtual machine settings

Change the following settings to maximize the egress in virtual environments:

1. Enable **Single Root I/O Virtualization (SR-IOV)** in the following three locations:

    - The BIOS of the MCC virtual machine
    - The network card properties of the MCC virtual machine
    - The hypervisor for the MCC virtual machine

    Microsoft has found these settings to double egress when using a Microsoft Hyper-V deployment.

2. Enable high performance in the BIOS instead of energy savings. Microsoft has found this setting to also nearly double egress in a Microsoft Hyper-V deployment.
