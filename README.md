# Enterprise-multisite-network-simulation
Multi-Site Enterprise Network Simulation (VLANs &amp; OSPF Routing)

🏗️ Network Architecture & Topology

[ Site A: Headquarters (HQ) ]                 [ Site B: Branch Office ]
       
         +-------------------+                         +-------------------+
         |    HQ-Router      |=========================|   Branch-Router   |
         |  (Cisco 2911)     |     WAN Link (10.0.0.0) |    (Cisco 2911)   |
         +---------+---------+                         +---------+---------+
                   | (Trunk Port)                                |
         +---------+---------+                         +---------+---------+
         |    HQ-Switch      |                         |  Branch-Switch    |
         | (Cisco 2960-24TT) |                         | (Cisco 2960-24TT) |
         +----+---------+----+                         +----+---------+----+
              |         |                                   |         |
      [VLAN 10]        [VLAN 20]                    [Local Subnet]   [Local Subnet]
     (HR Department)  (Engineering)                 (Branch Staff)   (Branch Staff)
   `192.168.10.0/24` `192.168.20.0/24`             `192.168.30.0/24` `192.168.30.0/24`



   ⚡ Core Technical Features
Advanced VLAN Segmentation: Isolated sensitive departmental traffic at Layer 2 (HQ split into HR and Engineering domains).

Router-on-a-Stick (RoaS): Configured 802.1Q encapsulation on sub-interfaces to route traffic between isolated VLANs efficiently through a single physical router port.

Dynamic Routing via OSPF (Area 0): Implemented Open Shortest Path First protocol to automatically propagate routing tables and maintain fault-tolerant paths across the WAN link.

Point-to-Point WAN Connectivity: Established a dedicated high-efficiency /30 subnet linking HQ and Branch routers.

Rigorous Fault-Finding & Verification: Validated interface states (no shutdown), gateway parameters, and telemetry metrics using end-to-end ICMP echo requests.

📂 Repository Structure

├── topology/
│   └── enterprise_network.pkt      # Cisco Packet Tracer simulation file
├── docs/
│   └── network_diagram.png         # Visual layout of the multi-site setup
├── README.md                       # Project documentation
└── LICENSE                         # MIT open-source license

🚀 Quick Start Guide
Prerequisites: Download and install Cisco Packet Tracer.

Clone the Repo: git clone https://github.com/Mariyan-Nikov/Enterprise-multisite-network-simulation.git

Open Simulation: Launch enterprise_network.pkt inside Cisco Packet Tracer.

Verify Connectivity: Open the terminal on any endpoint and test telemetry:

Inter-VLAN Test (HQ): ping 192.168.20.10

Cross-WAN Test (HQ to Branch): ping 192.168.30.10
