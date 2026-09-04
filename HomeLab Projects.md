# Active Directory Home Lab

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


# Network Wide DNS/Adblocker via Pi-Hole 

### What it is

A Raspberry Pi running Pi-hole, which blocks ads and trackers for every device on my home network by filtering them out at the DNS level (DNS is basically the phone book the internet uses to turn a website name into an address your device can actually connect to).

### Why I built it

I wanted real, hands-on practice with Linux and networking, not just reading about it. This felt like a good first project: useful once it's done, but with enough steps involved that I'd actually run into real problems and have to work through them.

### What I used
A Raspberry Pi 4 (small, cheap computer about the size of a deck of cards)
Ubuntu Server, a version of Linux made to run without a normal desktop screen
 Pi-hole, free software that blocks ads network-wide
 What I actually did
Installed the operating system onto a USB drive and got the Pi booting from it
Gave the Pi a permanent, unchanging address on my home network (so it doesn't randomly get a new one later and stop working)
 Installed Pi-hole and pointed it at Cloudflare, a fast public DNS service, to handle anything it doesn't block
Set my devices to use the Pi as their DNS instead of my router's default
    
### What went wrong (and what I learned from it)

The memory card broke. Literally snapped. I switched to booting from a USB drive instead, which turned out to be a better option anyway — more reliable long-term than a memory card.

The Pi wouldn't boot from the USB drive at all. I learned that Raspberry Pis have a setting, saved on the device itself, that controls where they're allowed to look for their operating system. Mine wasn't set to check USB drives. I had to boot from a spare memory card just once, flip that one setting, and then I could switch back to the USB drive for good.

I couldn't log into the Pi over the network. The tool I was using to set up the memory card was supposed to also set a username and password for me, but it silently failed to save those settings, more than once. I eventually found the exact file where that information is supposed to live and typed it in myself instead of trusting the tool to do it.

My "permanent" network address kept undoing itself every time the Pi restarted. Something running in the background was quietly resetting my settings back to default on every reboot. Once I found what was doing that and told it to stop, the address finally stuck.

The Pi-hole installer kept freezing partway through. A few different things caused this at different points, but the pattern I learned was: don't just keep re-running the same command and hoping. I checked whether anything was actually happening in the background (using the top command), and when nothing was, I knew it had actually died rather than just being slow. As it turned out - it was a combination of lack of root permissions on the install, and bad piping on the install command that were causing it.

Once installed, the website that manages Pi-hole gave me a "Forbidden" error. This one taught me the most, honestly. Two different pieces of software both wanted to use the same "door" (a network port) to talk to my browser, and only one of them was supposed to still be around. I found a command that tells you exactly which program is using which port. Once I saw which one shouldn't have been there, I turned it off, and the correct one took over the door and started working.

### What's next
Set up a second small project to practice using a support ticket system
Look into adding remote access to my home network as another project
