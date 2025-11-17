<h1>Remote Support Tools</h1>
Remote support tools allow IT professionals to access, troubleshoot, and manage devices from anywhere — a critical capability in modern, distributed environments like school districts, enterprises, and hybrid workforces.
<h2>Description</h2>
In this lab, we will demonstrate the use of serveral remote support tools such as ssh, rdp, vnc and Team Viewer. We will show how to set up each of these tools and how to connect from seperate clients. We are going be using the Windows 11 VM and Ubunutu VM from previous labs.
<br />

<h2>Technologies Used</h2>

- <b>VirtualBox</b> 
- <b>Ubuntu Linux</b>
- <b>Windows 11</b>

<h2>Lab walk-through:</h2>
SSH 

SSH(Secure Shell) is a command-line cryptographic protocol used to securely access and manage remote devices. It replaced insecure remote access tools like Telnet. Typically used for server administration, file transfer, automation and scripting in CLI environments. Uses default port 22.

1. First, we need to install SSH on the Ubuntu VM. Login into Ubunutu VM > Open Terminal > Type command shown below.
 <br/>
<img width="822" height="589" alt="image" src="https://github.com/user-attachments/assets/9610e88c-7a0d-4e42-a7c8-e52fd9ac2d73" />
<br />
<br />

2. Once downloaded, we need to enable SSH on the machine. Type command shown below.
 <br/>
<img width="813" height="584" alt="image" src="https://github.com/user-attachments/assets/8ee7dd48-c009-45bc-b5ac-d8f23032a3b0" />
<br />
<br />

3. Linux firewalls block by default. We need to change a rule to explicitly allow SSH traffic. Type command below. 
 <br/>
<img width="813" height="582" alt="image" src="https://github.com/user-attachments/assets/5f3bcffb-32a6-4ed8-a1ad-b0f7b0517415" />
<br />
<br />


4. We can check if this rule has been added by typing command below.
 <br/>
<img width="817" height="573" alt="image" src="https://github.com/user-attachments/assets/0482ef97-c94e-41db-b5d8-c46e2212b869" />
<br />
<br />

5. Now, we have to get the IP address of the Ubuntu machine because it is required for the remote machine to connect to it. Type command "ip a" to get network information.
 <br/>
<img width="822" height="581" alt="image" src="https://github.com/user-attachments/assets/a4bb1af0-bd78-453b-b45d-359aa70a52af" />
<br />
<br />

6. Boot up Windows 11 machine, Open Command Prompt. Now will connect to Ubuntu machine from Windows machine using SSH. The command for connecting via SSH is username + "@" + IP address of remote machine.
 <br/>
<img width="1006" height="625" alt="image" src="https://github.com/user-attachments/assets/4df9d5bb-f46e-441f-81c2-aadb7e7ec7a2" />
<br />
<br />

7. You will know you are logged in if the username in the bottom left corner is the username of the remote account. You can also type command "whoami" to check which user you are logged in as.
 <br/>
<img width="997" height="631" alt="image" src="https://github.com/user-attachments/assets/97e51810-e4f2-4c04-915d-462b602134df" />
<br />
<br />

8. If you don't want to authenticate using a password you can also use a key pair. This is more secure than using password. On the Windows machine, open Terminal and generate SSH key pair with command "ssh-keygen". This command creates a rsa key pair which is an asymmetric encryption algorithm meaning we have one public key and one private key.
 <br/>
<img width="953" height="521" alt="image" src="https://github.com/user-attachments/assets/606828df-8401-4c71-a47e-d4284ca62f83" />
<br />
<br />

9. We will check if the keys have been created by navigating to the ssh key pairs. You can see a public and private key has been generated. Make sure your private key is secure and not available to anyone. The public key will be copied onto the machines that we want to connect to.
 <br/>
 <img width="955" height="617" alt="image" src="https://github.com/user-attachments/assets/a2370de9-72ac-4762-88cf-f46ebea2e2ae" />
<br />
<br />

10. Now we need to copy the public key over to the Ubunutu machine. First we will connect to Ubuntu machine using SSH. Then we will add the public key to the authorized key file. Navigate to this file in command like by typing command "cd .ssh".
 <br/>
<img width="778" height="689" alt="image" src="https://github.com/user-attachments/assets/e9f57a0f-0497-47c2-b900-bfe75304392d" />
<br />
<br />

11. Once we are at the authorized key file we will add the public key using the vi editor. Type "vi "authorized_keys" to open text editor > Open another command prompt and type "type id_rsa.pub" to get public key, copy it > Paste public key into file > Save it > Type "cat authorized_keys" to see if key has been added correctly.
 <br/>
<img width="785" height="700" alt="image" src="https://github.com/user-attachments/assets/310a4121-8273-4d5e-b50a-4f16efb47c89" />
<br />
<br />

12. Exit out of SSH connection. Try to SSH again and you will see to don't need a password to connect to the Ubuntu machine.
 <br/>
<img width="778" height="699" alt="image" src="https://github.com/user-attachments/assets/13a321c4-0dc1-4929-b332-61fbdb638867" />
<br />
<br />

RDP

Remote Desktop Protocol



