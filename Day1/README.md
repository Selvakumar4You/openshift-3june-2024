# Day 1

## What is Boot Loader ?
- When we boot Laptop/Desktop/Workstation/Server, the BIOS it will perform POST (Power On Self Test)
- Once the BIOS POST operations are completed, the BIOS will instruct the CPU to load the Boot Loader utility that is installed on the Master Boot Record (MBR - Sector 0 Byte 0 on the Hard disk).
- It is tiny appliction which has to fit within 512 bytes
- Boot loader is the one which scans your hard disks looking for Operating systems installed and boots the OS
- Every OS whether it is Windows/Linux it will install the Boot Loader at the end of the OS installtion
- In case the MBR is corrupted then your OS will not boot at all
- Examples
  - LILO ( Linux Loader )
  - GRUB 2 - Stable boot loader generally used in all Linux Distributions
  - BootCamp - commercial boot loader used on the Mac Laptops/Desktops

## What is Dual/Multi-booting?
- In case, you have installed 2 or more OS on the same laptop/desktop, then the boot loader utility gives a menu asking which OS you want to boot into
- In case you have multiple OS, only one OS can be active at any point of time
- If you wish to boot into the other OS, you need to shutdown the currently running OS

## What is Hypervisor?
- is virtualization technology
- we can run multiple OS on the same laptop/desktop/workstation/server
- many OS can be actively running at the same time on the same machine
- AMD Processor
  - the virtualization feature set is called AMD-V
- Intel Processor
  - the virtualization feature set is called VT-X
- need hardware and BIOS support to install Hypervisor(Virtualization) software
- each Virtual Machine represents 1 OS
- In case laption/desktop/workstation, we generally install Type 2 Hypervisor
- Type 2 Hypervisors require a Host OS installed on the machine
- The Virtualization software is installe on top of the Host OS
- The additional OS that we install are called Guest OS, which runs within a Virtual Machine
- In case of Servers, we can install Type 1 Hypervisor a.k.a Bare metal hypervisors
- Bare metal hypervisors doesn't require a OS to be installed to create virtual machine
- Type 1 Hypervisor Example
  - VMWare vSphere/vCenter
- Type 2 Hypervisors Examples
  VMWare (Paid - Commercial Product )
    - Fusion ( installed top of Mac OS-X )
    - Workstation ( installed on top of Windows/Linux )
  Oracle Virtualbox ( installed on top of Mac/Windows/Linux - Free but not opensource )
- KVM - Free & Opensource Hypervisor works on all Linux Distributions
- This type of virtualization is called heavy-weight Virtualization
  - the reason for saying heavy-weight is because each Virtual Machines has to be allocated with dedicated hardware resources
    - CPU Cores (virtual cores )
    - RAM - Actual size
    - Network Card ( virtual )
    - Graphics Card ( virtual )
    
## What is the deciding factor that limits the maximum number of Virtual Machines we can create on a machine?
- Processor - supports multiple CPU Cores
- depends on how many virtual CPU cores your system supports
- modern Processor with 4 Physical Cores are seen as 8 Virtual Cores by the Virtualization software
- Which mean on a laptop with 4 Physical CPU Cores, you can run 1 Host OS and 7 Virtual Machine

## Docker Overview

## Podman Overview

## Container Orchestration Overview


