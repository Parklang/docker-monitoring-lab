# docker-monitoring-lab
# Virtualization System Support Lab

**Author:** System Support Intern
**Date:** October 2023
**Status:** Work in Progress (Learning Phase)

## 1. Introduction & Objectives

Welcome to my Virtualization Support Lab repository. As a System Support Intern, my primary goal for this project is to bridge the gap between theoretical IT knowledge and practical, hands-on server management.

This lab serves as a safe sandbox environment where I can practice and document the core responsibilities of a System Administrator. The main objectives are:

- **Virtualization Proficiency:** Gain hands-on experience managing hypervisors (Oracle VirtualBox) and understanding how virtual resources (CPU, RAM, storage) are allocated.
- **OS Installation & Configuration:** Practice the installation and initial configuration of both Linux (Ubuntu Server) and Windows (Windows Server) environments from scratch. This includes partitioning, setting hostnames, and configuring user accounts.
- **System Monitoring:** Learn how to monitor system performance, resource usage, and service health using command-line tools and basic dashboards.
- **Documentation:** Develop a habit of documenting every step, error, and resolution—a crucial skill for any support role.

## 2. System Architecture

The lab is designed to run on a standard corporate laptop, utilizing a Type-2 hypervisor. This setup allows me to run multiple "server" environments without needing dedicated physical hardware.

```text
+-----------------------------------------------------+
|         Physical Host (Windows Laptop)               |
|         OS: Windows 10/11 Pro                        |
|         RAM: 16GB+ Recommended                       |
|                                                      |
|         +---------------------------------------+   |
|         |   Hypervisor: Oracle VirtualBox        |   |
|         |                                        |   |
|         |   +----------+   +-----------------+  |   |
|         |   |          |   |                 |  |   |
|         |   |  Ubuntu  |   |   Windows       |  |   |
|         |   |  Server  |   |   Server        |  |   |
|         |   |  VM      |   |   VM            |  |   |
|         |   | (Linux)  |   |  (Windows)      |  |   |
|         |   +----+-----+   +-------+---------+  |   |
|         |        |                  |            |   |
|         +--------|------------------|------------+   |
|                  |                  |                |
|                  +-------v----------+                |
|                          |                           |
|                 Virtual Network (NAT/Host-Only)      |
+-----------------------------------------------------+
