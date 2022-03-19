# Author's Note

The tagline for this whole GLP is "Dynamic Defense", meaning that we look to apply physical and cyber defense concepts in an environment, but that both environments affect the other in some way. This GLP would be primarily focused on base defense, but would include some side missions that pop up outside the base.

A lot of defense, as you know, isn't a matter of how fast you can counter-type against an attacker. Instead, it's how well you set up services or use tools to protect your infrastructure. So what I want to do is focus on a small handful of services and tools for the cadets to either deploy or use in some fashion. A list of potential options include:

1. Firewall rules
2. Snort/Suricata
3. Policies (i.e. passwords, number of user accounts)
4. Anything from Sysinternals
5. Vulnerability scanner (i.e. Nessus)
6. Basic networking (i.e. PacketTracer, Wireshark)

As the GLP continues, there may be a list of cyber-related tasks that need doing. For example, getting the IP address of each cadet's phones and allowing traffic from them to the main computer via firewalls. Or, comms just went down, so cyber has to complete some short task (i.e. "find the malware with X tool") to get them back up, and until they do people on the ground are not allowed to communicate. They would be very simple tasks, but there would be enough of them that the cyber operator needs to prioritize what needs doing as the GLP goes along.

At the same time, the people guarding the cyber operator would need to conduct base defense procedures. There may be people moving in and out, or they may have to go question/detain someone sketchy-looking. Maybe during the GLP, the cyber operator loses the use of some tool or service, but intel has located the source of the disturbance (an enemy hacker nearby). It would be a matter of covering each other's backs, and having a direct, tangible impact on both of their tactical missions.

# CTX1 - Operation Diamondhouse

Welcome to Operation Diamondhouse, a Cyber Training Exercise (CTX) designed for AFROTC cadets.

This CTX was designed to test cadets for leadership competencies in a high intensity simulation, while also acting as a follow-up to CTX0. This simulation will be carried out in both the land domain and in the cyber domain.

If you would like to perform this CTX you will need the following:

1. Someone who is technically skilled to setup the scenario.
2. The following equipment:
    - FTX simulation equipment such as rubber duckies.
    - Two computers or virtual machines.
    - Basic networking capability between these machines.

### Expected Design

The CTX is a timed trial, where the duration is partially on the cyber team's ability to complete their tasks. However, the land domain will have opportunities to not only protect their techy allies, but also to support and expedite their mission with additional objectives.

The CTX admin will be expected to use a space that is suitable for base defense. It can be performed in indoor or outdoor locations, as long as there is wireless Internet connection (a single laptop can suffice for the cyber domain). When implementing the CTX, keep the following in mind:

1. The cyber domain assumes that some of the skills learned in CTX1 can be applied here, namely SSH.
    - If you do not feel confident that the cadets have retained that knowledge, feel free to include additional reminders or resources for it.
2. The land domain should have a variety of scenarios ready to be deployed against the trainees as they protect their team and their base.
    - Upset locals, enemy scouts, social engineers, guns-blazing OPFOR, etc.
3. When giving the additional objectives to the land domain, make it so that urgency is needed to complete them.
    - It should challenge the commander to quickly respond to a situation, while also encouraging the defenders to stay alert at all times.

Augment the scenario as you see fit.

### Objectives

For: POC
Time: 40 mins
 - 10 for planning
 - 30 for execution

Technical Objectives:
1. Intro to Ubuntu
2. Intro to iptables
3. Intro to netcat

Tools:
1. Two Ubuntu machines
2. Network connection between the two (Internet access not required)

### Setup

**NOTE:** "PC1" will refer to the machine that the cadets will have direct access to. "PC2" will refer to the machine that they will have to SSH into.

1. Download and configure Ubuntu onto two computers, or two virtual machines
    - https://ubuntu.com/download/desktop
2. Download iptables on both computers, and download netcat on PC1
3. Ensure that the SSH port is open on both machines
    - Configure SSH: https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/
    - iptables -A INPUT -p tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
    - iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT
4. Have an easy set of credentials for the PC1, but have a much more difficult one for PC2 (examples below)
    - PC1
        • Username: _user1_
        • Password: _password_
    - PC2
        • Username: _user2_
        • Password: _Y0uW1llNev3rGue$$!_

### Scenario

Team is briefed with the following:

    FOB Bravo has been established along the border of a near-peer nation. However, an internal vulnerability scan has reported that the physical and cyber defenses are in need of reinforcing. Your team has been assigned to provide added security to a portion of the FOB, while also configuring the firewalls on two sensitive devices to ensure that they are better protected against attacks. There have been OPFOR sighted within the region, and they may attempt to undermine both physical and cyber operations. Swift, decisive action will be needed to counteract these efforts. Allied military and civilian personnel are also active in the region, and proper care must be taken to ensure their objectives are not unnecessarily hindered.
    Your mission is complete once the firewalls have been properly configured, and you have verified it with the proper scanning technology. You must also keep the base secure for 30 minutes. Ensure that OPSEC is maintained at all times, and that details of the firewall configurations are kept away from any unauthorized personnel.
    For base entry:
        - The challenge phrase is "Wire"
        - The normal response is "Chip"
        - The duress response is "Port"

Print out the following and hand the useful information to them:

1. Guide on how to write iptables rules: https://www.digitalocean.com/community/tutorials/iptables-essentials-common-firewall-rules-and-commands
2. Guide on how to SSH into a remote server: https://linuxconfig.org/Ssh
3. Guide on how to use netcat: https://www.varonis.com/blog/netcat-commands

They will have to write firewall rules on both PC1 and PC2 for the following (SOLUTION KEY, DO NOT SHOW TRAINEES):
1. Block HTTP traffic both ways (port 80)
    - iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW,ESTABLISHED -j DROP
    - iptables -A OUTPUT -p tcp --sport 80 -m conntrack --ctstate ESTABLISHED -j DROP
2. Block POP3 traffic both ways (ports 110 and 995)
    - iptables -A INPUT -p tcp --dport 110 -m conntrack --ctstate NEW,ESTABLISHED -j DROP
    - iptables -A OUTPUT -p tcp --sport 110 -m conntrack --ctstate ESTABLISHED -j DROP
    - iptables -A INPUT -p tcp --dport 995 -m conntrack --ctstate NEW,ESTABLISHED -j DROP
    - iptables -A OUTPUT -p tcp --sport 995 -m conntrack --ctstate ESTABLISHED -j DROP
3. Block Telnet traffic both ways (port 23)
    - iptables -A INPUT -p tcp --dport 23 -m conntrack --ctstate NEW,ESTABLISHED -j DROP
    - iptables -A OUTPUT -p tcp --sport 23 -m conntrack --ctstate ESTABLISHED -j DROP

### OPFOR Guidance
1. Feel free to sandbox some approaches to the FOB, ranging from benign to outright aggressive. While cyber is a decent portion of this GLP, the cadets are still being evaluated on their base defense abilities.
2. For at least one of the friendly civilian personnel to approach the FOB, try to tailgate behind them. 
3. Do not assume that you know the challenge and response phrases unless you can overhear it and reasonably guess it.

### Onsite Setup
1. Have a large enough FOB where digital communications (i.e. radios, phone calls, texts, etc) are required, due to distance
2. Have the laptop and VMs already set up on-site
3. Test to ensure the VMs can communicate with each other

### Injects
Every 10 minutes after the briefing phase, include one of the following challenges (max 15 minutes to complete):
1. An RPG has been launched into the base, but it did not detonate. The ground team must perform the 5Cs and call in a 9-Line. Failure results in at least one of the cyber team and one of the ground team becoming wounded by it.
2. A DDoS attack has been launched, and all the cadets' cell phones are a part of the botnet. The cyber team must acquire the IPv4 addresses of their cell phones and must add rules to block them on the firewall. Failure results in the ground team only being able to use non-digital communications for the rest of the GLP.
(OPTIONAL FOR EXTRA TIME) 3. Unidentified forces are spotted tampering with cables just outside of the base's premises. The ground team must deal with the sabotagers while maintaining security. Failure results in a 2-minute hands off period for the cyber team.
