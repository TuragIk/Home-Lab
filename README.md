# Home Lab

## Objective

The Home Lab project allows the user to set up a controlled environment to simulate real-world scenarios to further understanding within the field of cybersecurity. It provides a foundation for hands-on-learning and experimentation within the field. Future projects will reference this as a setup for labs.

---

### Skills Learned

- Setting up and configuring virtualization platforms.
- Designing segmented networks for secure communication.
- Deploying and integrating key cybersecurity tools.
- Basic automation techniques for efficient setup and scaling.

---

### Tools Used

- **Virtualization:** VirtualBox (or alternatives like VMware Workstation).
- **Networking:** Virtual network adapters and custom routing configurations.
- **Operating Systems:** 
  - Kali Linux (attacker/analysis machine).
  - Windows Server/Client (target/victim).
- **Infrastructure Requirements:** 
  - A host machine with at least 16 GB of RAM, quad-core CPU, and ~50 GB free storage.
 
---

## Steps to Set Up the Home Lab

### **1. VirtualBox Installation**
- Install VirtualBox on your host machine.
- Download it from [VirtualBox Official Site](https://www.virtualbox.org/).

*Ref 1: VirtualBox installer on a Windows machine.*
![VirtualBox Installation](https://via.placeholder.com/800x400)

---

### **2. Virtual Machine Creation**
#### **Step 2.1: Creating the Kali Linux VM**
1. Download the Kali Linux ISO from the [Official Kali Site](https://www.kali.org/get-kali/).
2. Open VirtualBox, click **New**, and follow the prompts to:
   - Allocate 2 GB of RAM and 20 GB of disk space for the VM.
   - Attach the downloaded ISO to the VM.
3. Start the VM and follow the Kali Linux installation steps.

*Ref 2: VirtualBox settings for Kali Linux VM.*
![Kali Linux VM Settings](https://via.placeholder.com/800x400)


#### **Step 2.2: Creating the Windows VM**
1. Download the Windows ISO from the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/).
2. Repeat the same process as Kali, allocating at least 4 GB of RAM and 30 GB of disk space.
3. Install Windows and set up a user account.

*Ref 3: VirtualBox settings for Windows VM.*
![Windows VM Settings](https://via.placeholder.com/800x400)

---

### **3. Networking Configuration**
#### **Step 3.1: Private Network Setup**
1. In VirtualBox, configure the network adapters for both VMs:
   - Adapter Type: **Internal Network**.
   - Network Name: `CyberLab` (or any custom name).
2. Assign static IP addresses to the VMs:
   - **Kali Linux**: 
     ```bash
     sudo nano /etc/network/interfaces
     ```
     Add the following configuration:
     ```bash
     auto eth0
     iface eth0 inet static
     address 192.168.56.101
     netmask 255.255.255.0
     gateway 192.168.56.1
     ```
   - **Windows**: 
     Configure the IP manually in the Network Settings as `192.168.56.102`.

*Ref 4: Network Adapter Settings in VirtualBox.*
![VirtualBox Network Adapter Settings](https://via.placeholder.com/800x400)

**Here is a diagram of the current network configuration**
*Ref 5: Network Configuration Diagram.*
![Network Configuration Diagram](https://via.placeholder.com/800x400)

---

### **4. Test the Connection**
1. Start both VMs.
2. From Kali Linux, ping the Windows VM:
   ```bash
   ping 192.168.56.102
   ```
   - *If Windows Firewall blocks communication, stop the ping test using Ctrl+C*
3. From Windows, test the connection to Kali Linux:
   - Open Command Prompt (`cmd`) and run:
     ```bash
     ping 192.168.56.101
     ```
4. Ensure both VMs can ping each other successfully.

*Ref 6: Successful ping results from Windows to Kali Linux*
![Successful Ping Windows to Kali](https://via.placeholder.com/800x400)

---

### **5. Related Projects**
Here are some of my projects that use this home lab:

---

### **Conclusion**
Congratulations on setting up a home lab! Future projects will reference this lab as a setup, and feel free to check out Related Projects for some exemplar labs to use!

### **License**
This project is licensed under the MIT License. See the `LICENSE` file for details.
