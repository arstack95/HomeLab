### Active Directory Home Lab

### What it is
    A self-contained Active Directory environment running as a virtual machine on my Mac, used to get hands-on practice with Windows Server administration and virtualization.

### Why
    To get real, hands-on experience with Active Directory and virtualization rather than relying on coursework alone — this is core infrastructure for a lot of IT support and sysadmin roles, and I hadn't touched it directly before this.

### Stack
    2020 MacBook Air, dual-booted into Windows 10 Pro
    VirtualBox
    Windows Server 2025 (evaluation ISO)

### Setup
    Installed VirtualBox and downloaded the Windows Server 2025 ISO
    Set the VM's network adapter to Bridged Adapter mode, so the VM gets its own address on the home network and is reachable from other devices, rather than being isolated behind NAT
    Installed Windows Server inside the VM
    Set a static IP address on the server for a consistent, predictable connection
    Installed the Active Directory Domain Services role
    Promoted the server to a Domain Controller — the point where it stopped being a standalone Windows machine and became the system responsible for managing accounts, logins, and permissions for the      network
    Verified it was reachable by pinging the server from multiple other devices on the network

### Problems & fixes
    The dual-booted Windows installation was missing dependencies required by VirtualBox. Fixed by installing the Microsoft Visual C++ Redistributable.

### Next
    Set up Organizational Units, security groups, and Group Policy to simulate a small fictional corporate environment
    Join a real client machine to the domain to practice logins and permissions end-to-end
