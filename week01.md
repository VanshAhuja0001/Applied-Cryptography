# Week 1

### I am using mac Book. I am using 2 virtual machine. One is UTM and another is oracle virtual machine.

In UTM i have installed windows ad putty and in Oracle virtual machine i have installed ubuntu.

## UTM windows
<img width="924" alt="Screenshot 2025-03-27 at 10 53 33 am" src="https://github.com/user-attachments/assets/4df1ebd3-ab3d-46f0-b32a-e9e14f763e9a" />

## Oracle Virtual Machine 
<img width="787" alt="Screenshot 2025-03-27 at 10 54 52 am" src="https://github.com/user-attachments/assets/0146453d-4405-4e4b-8296-1312a71f0b69" />

## Using Bridge Adapter Network
Network adapter is Attached to: Bridged Adapter, using en0: Wi-Fi.
This is good — it allows your Ubuntu VM to share your Mac’s actual Wi-Fi IP range.
Problem: Bridged adapters may not work properly when connected to some public or enterprise Wi-Fi networks, because the router blocks multiple MAC addresses.
i was unable to connect Putty with the ubuntu through the NAT port forwarding. so i used the bridge adapter to connect. 
<img width="988" alt="Screenshot 2025-03-27 at 10 55 34 am" src="https://github.com/user-attachments/assets/f9346b3a-1e18-4bd8-bc5b-8ef8bf8a1213" />

## Ubuntu server
<img width="775" alt="Screenshot 2025-03-27 at 11 00 06 am" src="https://github.com/user-attachments/assets/b18322ea-deaa-4821-9fa5-162f38dd67e9" />

## Putty in UTM Windows
<img width="1470" alt="putty" src="https://github.com/user-attachments/assets/60e23ed4-85a8-4a75-be78-bcd1dc712586" />
This figure displays the PuTTY client open on the Windows UTM VM. I attempted to connect to the Ubuntu VM using the IP address 192.168.1.123 on port 22 via SSH. The configuration seems correct for local network access. However, this connection only works if both VMs are on the same network segment, which failed when I switched to a different (external) Wi-Fi network due to how the bridged adapter was handled.

## Before ssh in Putty
<img width="1470" alt="before ssh" src="https://github.com/user-attachments/assets/1b8d51f3-e595-47c8-994d-74da3ba04a59" />
This image shows that I successfully added the SSH public key (from the Ubuntu VM) to my GitHub account under the name "Rubuntu". The key is correctly listed under my GitHub SSH keys, confirming that GitHub now recognizes the key and allows secure operations like cloning and pushing to repositories via SSH from the VM.

## Clonning
<img width="1470" alt="clonning" src="https://github.com/user-attachments/assets/a0bd0a06-e1d5-4d99-810c-5fdcb0f9c8e0" />
This screenshot captures the Ubuntu terminal after successfully cloning the course repository from GitHub using SSH. This confirms that the SSH key previously added to GitHub is properly working from the Ubuntu VM as well. It proves that both virtual machines (Windows and Ubuntu) can independently communicate with GitHub using SSH.


## SSH key in GIT
<img width="1470" alt="ssh key in Git" src="https://github.com/user-attachments/assets/d99f3235-acf0-44ff-b9e4-4b12d9d9c758" />

## Command Prompt

<img width="1470" alt="Screenshot 2025-03-27 at 11 06 50 am" src="https://github.com/user-attachments/assets/f827330d-499e-4270-9425-cfa571e3ea37" />

## Command prompt Python installation, py cipher
<img width="1470" alt="Screenshot 2025-04-02 at 12 16 24 pm" src="https://github.com/user-attachments/assets/d864624b-0503-46a4-bdea-83a8444c6e02" />
In this figure, I attempted to set up Python and pip on the Windows VM. Initially, there were issues with using pip commands, but I resolved them by updating pip and successfully installing the pycipher library. This was a separate configuration task to ensure my Windows VM could run Python-based cryptography exercises, and it confirms that pip is now working properly in the environment.



## Week 1 QUIZ
<img width="1470" alt="Screenshot 2025-03-27 at 11 04 56 am" src="https://github.com/user-attachments/assets/dbf9fb39-8f2f-4ff0-b2fc-67da8fd046f5" />







[Return to contents](./README.md)


