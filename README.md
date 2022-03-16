WIP

The tagline for this whole GLP is "Dynamic Defense", meaning that we look to apply physical and cyber defense concepts in an environment, but that both environments affect the other in some way. This GLP would be primarily focused on base defense, but would include some side missions that pop up outside the base.
A lot of defense, as you know, isn't a matter of how fast you can counter-type against an attacker. Instead, it's how well you set up services or use tools to protect your infrastructure. So what I want to do is focus on a small handful of services and tools, no more than 3, for the cadets to either deploy or use in some fashion. A list of potential options include:

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

The CTX is a timed trial, where the duration is partially on the cyber team's ability to complete their tasks. However, the land domain will have opportunities to not only protect their techy allies, but also to support and expedite their mission with optional objectives.

The CTX admin will be expected to use a space that is suitable for base defense. It can be performed in indoor or outdoor locations, as long as there is wireless Internet connection (a single laptop can suffice for the cyber domain). When implementing the CTX, keep the following in mind:

1. The cyber domain assumes that some of the skills learned in CTX1 can be applied here, namely SSH.
    - If you do not feel confident that the trainees have retained that knowledge, feel free to include additional reminders or resources for it.
2. The land domain should have a variety of scenarios ready to be deployed against the trainees as they protect their team and their base.
    - Upset locals, enemy scouts, social engineers, guns-blazing OPFOR, etc.
3. When giving the optional objectives to the land domain, make it so that urgency is needed to complete them.
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
1. Two Ubuntu machines (with iptables installed but not configured)
2. 

### Setup

1. -
2. -
3. -

### Scenario

Team is briefed with the following or using the presentation found in `Presentation/`':

    Intel has located a nefarious hacking group, known only as Hexfall, in a nearby facility. Hexfall was brought to the the governments attention after they opened an online weapons marketplace. Due to increasing demand of black market guns, the store is shipping thousands of dollars worth of weapons daily. It is believed they have two crates of weapons onsite as well as the hardware to run their own online weapons marketplace. You are being tasked with taking down the operation. You must take down the online weapon marketplace and take control of both weapons crates.

    Additionally, it is believed Hexfall has a small infrastructure of computers. But, due to the sensitive nature of their network, it cannot be moved until the website is disabled. Therefore, you will be tasked with taking Hexfall's website offline on location.

    To do this it is believed Hexfall's lead hacker has a flash drive where he stores the passwords to all their computers. You must obtain the flash drive, get the passwords, login to the remote server, and takedown the website.

    Your mission is complete when you take down the Hexfall website and take control of both weapons crates.

    Below is a list of helpful guides a technical specialist has prepared for you.

Print out the following and hand the useful information to them:

1. Crack a password protected file: https://linuxconfig.org/how-to-crack-zip-password-on-kali-linux

2. Guide on how to SSH into a remote server: https://linuxconfig.org/Ssh

3. Shutting down the server: `systemctl -poweroff`

### Opfor Guidance

Provide moderate resistance in Hexfall HQ shootout.

Provide mild attacks during hacking campaign.

Provide moderate resistance at second crate point.

Provide mild resistance during evacuation.

### Onsite Setup
1. Plug in Server
2. Verify website is runing, see `url.txt.` for site url
3. Verify Server IP address, ssh into `pi@hexfallserver.student.rit.edu`
4. Get IP address
5. Load IP address and weapon crate (#2) location onto zip file `zip -e secret_files.zip file1.txt`
6. Setup Kali box and optional LED lights
7. Setup presentation and have print outs (and optionally: phone) ready
8. Present presentation
9. Hand out print outs and optionally the phone with tor browser installed
