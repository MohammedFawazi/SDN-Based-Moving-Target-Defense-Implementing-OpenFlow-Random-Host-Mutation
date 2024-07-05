# SDN Based Moving Target Defense Implementing OpenFlow Random Host Mutation

## Overview

This project implements a Moving Target Defense (MTD) mechanism using Software Defined Networks (SDN) to enhance network security. By dynamically changing IP addresses of network hosts through OpenFlow Random Host Mutation (OF-RHM), the system makes it difficult for attackers to target specific hosts. This approach conceals real IP addresses from unauthorized entities while maintaining transparency for legitimate users.

## Data

The project leverages SDN architecture, particularly focusing on the OpenFlow protocol and Ryu controller. The key components include:
- Virtual and Real IP Mappings
- Authorized Entities
- Resource Pool for IP Allocation

## Defensive Mechanism

### Architecture

The architecture utilizes the OpenFlow protocol to manage network devices, with the Ryu controller facilitating IP mutation. The controller dynamically assigns virtual IP addresses to real hosts and changes these virtual IPs frequently using a pseudo-random number generator.

### Implementation

The core implementation includes:
- **Mapping Virtual to Real IPs**: Virtual IPs are mapped to real IPs and mutated periodically.
- **Random IP Selection**: New virtual IPs are selected from a pool of unassigned addresses.
- **Event Handling**: Custom events for timeouts are generated to trigger IP mutations.

## Methods

### Data Handling
- **Start Method**: Initializes the mutation process and spawns a thread to handle timed events.
- **TimerEventGen**: Generates timeout events every 30 seconds to trigger IP mutations.

### Security Measures
- **Authorized Access**: Only authorized entities can access real IPs via virtual IPs obtained through DNS.
- **IP Mutation**: Ensures high unpredictability in IP address mutation, complicating scanning efforts by attackers.

## Model Implementation

The implementation involves the following steps:
1. **Initialization**: Set up mappings and authorized entities.
2. **Event Generation**: Custom events for handling timeouts and triggering IP mutations.
3. **Packet Handling**: Manage ARP, ICMP, and IP packets to ensure smooth network operations while maintaining security.

## Results

The project demonstrates the viability of using OF-RHM within an SDN framework to defend against network scanning attacks. The dynamic IP mutation significantly enhances security by preventing attackers from reliably mapping network hosts.

## Key Findings

- **Effective IP Concealment**: Successfully hides real IP addresses from both internal and external scans.
- **Enhanced Security**: Dynamic IP mutation introduces significant hurdles for attackers.
- **Scalability**: The approach can be scaled for larger networks with more resources.

## Usage

To use this project:

1. **Clone the repository**:
    ```sh
    git clone https://github.com/yourusername/Moving_Target_Defense_SDN.git
    ```
2. **Install dependencies**:
    Ensure you have Ryu and other necessary libraries installed. You can install Ryu using:
    ```sh
    pip install ryu
    ```
3. **Run the application**:
    Execute the script to start the Moving Target Defense mechanism:
    ```sh
    ryu-manager Moving_Target_Defense_using_Software_defined_network.py
    ```

## Conclusion

The Moving Target Defense using SDN with OpenFlow Random Host Mutation provides a robust mechanism to enhance network security. By making it difficult for attackers to map network hosts, this approach significantly reduces the risk of successful network attacks.


Let me know if any clarification is needed on this README or project!
