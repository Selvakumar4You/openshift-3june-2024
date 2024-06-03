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
- is an application virtualization technology
- unlinke the Hypervisor technology, this is light weight virtualization
- why light-weight?
  - because container's don't use dedicated hardware resources
  - all the containers that runs on the same host machine shares the hardwares on the host OS
  - containers are not Operating System
  - containers doesn't have their own OS Kernel
- containers get's their own IP Address
- each container represents one application or one application component ( backend, frontend, web/app server, db server, etc )
- each container runs in a separate namespace
- containers are otherwise a normal application process
- Docker comes 2 flavours
  1. Docker Community Edition - Docker CE
  2. Docker Enterprise Edition - Docker EE
- Docker is developed in Go language by the company Docker Inc
- follows client/server architecture
- the server runs in the OS Kernel context (administrator), hence most container we create we will gain admin access within the containers, even in the case the user who created the container is a non-admin user

## Podman Overview
- Podman is alternate to Docker
- Podman is also opensource maintained by Community headed by Red Hat
- stand-alone tool unlike Docker
- supports creating root-less container i.e running application as normal user ( non-admin users )

## Container Orchestration Overview
- though containerized application workloads can be manually managed, in real-world no organization manages containers manually
- generally containerized applications are managed by Container Orchestration Platforms
- Examples
  - Docker SWARM
  - Google Kubernetes
  - AWS EKS - Elastic Kubernetes Service ( Managed K8s Cluster from Amazon AWS)
  - Azure AKS - Azure Kubernetes Service ( Managed K8s Cluster from Microsoft Azure)
  - Rancher Kubernetes ( Kubernetes + Rancher Webconsole )
  - Red Hat OpenShift
  - AWS ROSA - Managed Red Hat OpenShift Cluster from Amazon AWS 
  - Azure ARO - Managed Red Hat OpenShift cluster from Microsoft Azure

## Docker SWARM
- Docker Inc's native Orchestration Platform
- supports only Docker containerized application workloads
- easy to install on regular laptops/desktops
- light-weight
- good for learning purpose, dev/qa environment
- not used in production

## Google Kubernetes
- opensource and free Container Orchestration Platform developed and maintained by Opensource community led by Google
- supports many different Container Runtimes - e.g Docker, containerd, Podman
- also supports extending Kubernetes API by adding your own Custom Resources and Custom Controller
- supports packaging Custom Resources and Custom Controllers as Kubernetes Operators to extend Custom Kubernetes additional features
- generally Command-line only
- there is minimal Kubernetes Dashboard (webconsole) which doesn't support user management hence result in security issue, so normally organizations disable the Kubernetes dashboard
- Kubernetes doesn't support internal container registry out of the box, but can be configured to use external container registry

## Red Hat OpenShift
- Red Hat's Kubernetes distribution
- Kubernetes + Many additional features developed on top of opensource Kubernetes
- all the features supported in Kubernetes also works in OpenShift
- OpenShift added many additional features on top of Kubernetes
- supports CLI and Web Console(GUI)
- comes with Internal Openshift Container Registry
- supports CI/CD within Openshift
- supports additional Custom Resources in Openshift
  - DeploymentConfig
  - Route
