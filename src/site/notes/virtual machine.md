---
{"dg-publish":true,"permalink":"/virtual-machine/"}
---


**Virtual Machine (VM)**
  - A virtual machine is a software-based simulation of a [[physical computer\|physical computer]]. It runs on a [[host machine\|host machine]] but behaves like a completely independent computer with its own virtual CPU, memory, storage, and [[network interface\|network interface]]. This allows you to run multiple, isolated operating systems (like Windows, Linux, or macOS) simultaneously on a single physical server or desktop.

**How It Works**
  - A special software layer called a **hypervisor** (or virtual machine monitor) creates and manages VMs. It sits between the [[physical hardware\|physical hardware]] and the virtual machines, allocating [[physical resource\|physical resource]]s (CPU, RAM, disk) to each VM. The [[hypervisor\|hypervisor]] ensures that VMs are isolated from each other, so a crash or issue in one VM does not affect the others running on the same host.

**Key Benefits**
  - The primary advantages are **consolidation** (running many systems on one [[physical machine\|physical machine]]), **isolation** (for security and testing), and **portability**. A VM's entire state is stored in files, making it easy to back up, clone, or move to a different physical host with minimal downtime.

