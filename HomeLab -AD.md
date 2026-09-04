Active Directory Home Lab
What it is

A small practice version of the kind of system many companies use to manage employee accounts and logins across their network, built on a virtual computer running inside my own laptop.

Why I built it

I wanted real hands-on experience with this kind of system rather than just reading about it. It's a big part of how a lot of company networks are actually run, and I hadn't worked with it directly before.

What I used
My own laptop (a Mac, running Windows through dual-boot)
VirtualBox, free software that lets you run a whole separate "virtual" computer inside your real one
Windows Server, the version of Windows built to run this kind of network management system
What I actually did
Installed VirtualBox and set up a virtual computer inside it, running Windows Server
Made sure that virtual computer could be seen and reached by other devices on my home network, the same as any real computer would be
Gave it a fixed, permanent address on the network so it wouldn't change later and stop working
Turned that virtual computer into what's called a "Domain Controller" — this is the moment it stopped being just a regular Windows computer and became the system in charge of managing user accounts and logins for the network
Tested it by connecting to it from a few other devices, to make sure it was actually reachable
What went wrong (and what I learned)

Windows, installed through dual-boot on my Mac, was missing a piece of software that VirtualBox needed to run properly. I tracked down what was missing (a small Microsoft software package) and installed it, which fixed the issue.

What's next
Practice creating groups of users and setting rules for what different people are allowed to access
Connect a real device to this system and log in with an account I create on it, to see the whole process work end to end
