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

RDP is a Microsoft proprietary protocol that allows remote control of a remote computer using a GUI. It is as if you were sitting in front of a remote computer from your own device. It runs a client-server remote connection where one computer where we will be connecting from will run RDP client and the device we want to connect has to configured as an RDP server to recieve incoming connections. This example will be done over a LAN.

1.  Log in your Windows machine > Search System > Scroll down until you see "Remote Desktop", Click on it > Turn on remote desktop.
 <br/>
<img width="1025" height="749" alt="image" src="https://github.com/user-attachments/assets/4279204e-37b7-4f21-a0a4-8650f6d54fd8" />
<br />
<br />

2. Open command prompt and type "ipconfig" to get IP adress of Windows machine. We will use IP to connect.
 <br/>
<img width="975" height="626" alt="image" src="https://github.com/user-attachments/assets/4f9c1bb3-7757-42a2-9b7f-bc1471c72d68" />
<br />
<br />

3. Login to your Ubunutu machine. We need to download an RDP client called Remnina that will allow the Ubuntu machine to connect to the Windows machine via RDP. Open Terminal and type command shown below.
 <br/>
<img width="814" height="581" alt="image" src="https://github.com/user-attachments/assets/23b236c5-b239-4c2a-b068-36d215a273e8" />
<br />
<br />

4. Launch remnina client by searching in your applications.
 <br/>
<img width="1298" height="710" alt="image" src="https://github.com/user-attachments/assets/a4c6b2f0-1065-408e-b63e-465bb3f6935a" />
<br />
<br />

5. Select "RDP" and type the IP address of your Windows machine at the top of the page. You will be prompted to type in your username and password.
 <br/>
<img width="1298" height="711" alt="image" src="https://github.com/user-attachments/assets/51408787-5041-47d1-ac94-b8d0e9da8cf3" />
<br />
<br />

6. Once finished, you can see that you are logged into the Windows machine from your Ubunutu machine via RDP. You are able to fully control the Windows machine from the other machine. IF a user is logged into the Windows machine they will be kicked out once you connect through RDP. Make sure to close connection once you are finished.
 <br/>
<img width="1298" height="711" alt="image" src="https://github.com/user-attachments/assets/4ad05cd8-698c-4848-8e60-b1d3dd6c1f23" />
<br />
<br />

7. If you are on a windows machine and you want to connect to another windows machine you press the Windows key + r to open run command > Type "mstsc" to launch RDP.
 <br/>
<img width="1022" height="771" alt="image" src="https://github.com/user-attachments/assets/921aacb0-ad37-4888-b943-445689ac0d44" />
<br />
<br />

8. Type the IP address of the machine you want to connect to. Type in credentials for the account. Once verfied, you will be connected to the remote machine through RDP.
 <br/>
<img width="407" height="247" alt="image" src="https://github.com/user-attachments/assets/5203b7be-f567-4f0d-b2f3-af105cb31113" />
<br />
<br />

VNC

Virtual Network Computing is a protocol that is used for GUI remote control of a remote computer and it is different from RDP because it just uses a password to connect. It uses a server and client connection, the server would be installed on remote computer we want to connect to and use remote connection client to connect to remote server. User at remote device would able to see all of the actions you make from your end on thier screen as well like mouse movements and opening apps.

1. First, we will set up VNC server on Windows machine. Log in to your windows machine > Open an internet browser > Type "tightvnc" which is a popular open spurce VNC software. > Download on to your device.
 <br/>
<img width="933" height="698" alt="image" src="https://github.com/user-attachments/assets/88a3d863-c6ec-4cec-9329-7b3d634c68f7" />
<br />
<br />

2. Once downloaded, open the file so we can go through the setup. Accept License Terms, Click Next > Click "Typical Setup" > Click Install.
 <br/>
<img width="498" height="390" alt="image" src="https://github.com/user-attachments/assets/418b5ab1-1827-45dd-bb33-a75ee07f257d" />
<br />
<br />

4. Now we need to set-up password for login. Type in a password.
 <br/>
<img width="443" height="398" alt="image" src="https://github.com/user-attachments/assets/506e2d4a-286f-4611-be43-4fb644a75d22" />
<br />
<br />

5. We have VNC configured on our Windows machine, so now will head over to our Ubuntu machine. We will be using Remnina again for our remote connnection cleint. Open remnina app.
 <br/>
<img width="1301" height="735" alt="image" src="https://github.com/user-attachments/assets/3c6f5ed1-1132-431e-a4ff-820f425c4a32" />
<br />
<br />

6. In the box at the top of the page, change the protocol to VNC and type in the IP address of your Windows machine. You will be prompted to type in the password you previously created. Type it in and you will see you are connected to the Windows machine.
 <br/>
<img width="1303" height="739" alt="image" src="https://github.com/user-attachments/assets/7446f333-f608-497b-9ba2-cd48cd4d7669" />
<br />
<br />

7. To show that all the actions you make on your remote machine will show up on the client's machine, put the two machine side by side on your screen and open a notepad. From your Ubunutu machine type in your notepad and see the same actions being made on the Windows machine.
 <br/>
<img width="1902" height="950" alt="image" src="https://github.com/user-attachments/assets/88713b99-8238-41a3-8e4c-c5e2cba3bbe6" />
<br />
<br />

Third-Party Remote Support Tools

When using VNC, RDP and SSH we need to be able to route traffic from cleint to server and back in order for the protocols to work. In a lot of scenario's it is not possible for users to be on the same LAN when using remote support tools. One way to allow remote support over the internet without using a VPN is to use a third-party application like Team Viewer and AnyDesk
Team Viewer
