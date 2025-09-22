# Common Considerations 
- Identify the vulnerability and discover an exploit that can be use to gain a shell by delivering a payload.
- When considering how to establish a shell session on a Unix/Linux system, consider the following:
	- What Distribution of the Linux is the system running ?
	- What shell & programming language exist on the system ?
	- What function is the system serving for the network environment it is on ?
	- What application is the system hosting ?
	- Are there any known vulnerabilities ?
### Gaining a Shell Through Attacking a Vulnerable Application:
##### Initial enumeration of the system using nmap:

- ###### Enumerate the Host:

	- `nmap -sC -sV <Target_IP>`
		- Gaining a shell should be the priority 
		- use the nmap script output as a way to get it, 
			- look for the services, service version and etc.

- ###### Discovering a Vulnerability:

	- As per the output of the nmap and the navigation to the webserver.
	- find if the CVE exists in `exploit db`
	- find on the internet if any exploit exists.

- ###### Search for an Exploit Module:
	
	- `search <keyword>` 
	- https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits

- ###### Locate 
	- To locate the exploit use 
		- `locate exploits`
		- to keep msf up to date use the command 
			- `apt update;`
			- `apt install metasploit-framework`

- ### Spawning a TTY Shell with Python:
	
	- If there's no prompt seen.
	- These shells have limited functionality and can often prevent use of essential commands like:
		- `su(switch user)`
		- `sudo(super user do)`
	- So spawn a TTY shell using the language that is present in the target system.
	- if python exists then use:
		- `python -c 'import pty; pty.spawn("/bin/sh")'` 
