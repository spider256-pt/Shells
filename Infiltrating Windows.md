# Prominent Windows Exploit

- Several Vulnerabilities in the Windows Operating system and their corresponding attacks are some of the most exploited vulnerabilities.
- Some of them are:
	- `MS08-067`
	- `Eternal Blue`
	- `PrintNightmare`
	- `BlueKeep`
	- `Sigred`
	- `SeriouSam`
	- `Zerologon`

### Enumerating Windows & Fingerprinting Methods:

- ##### How to know if the host is using a Windows machine:
	- The Time to Live(TTL) counter when utilizing ICMP to determine the host is up.
		- The typical response from a Windows Host will either `32` or `128`.
		- The response can or around `128`

- ##### Using Nmap:
	- `nmap -O -v --max-retries <limit> --stats-every <time_in_seconds> <ip_address>`
		- `-O`: This option is used to initialize an OS detection.
		- `-v`: This option is used for verbose output.
		- `-A`: This option is used for aggressive scan which includes Os detection.
		
- ##### Banner Grab to Enumerate Ports
	- `nmap -v <ip_address> --script banner.nse`
		- For each port Nmap sees up, it will attempt to connect to the port and glean any information it can from it.

## Bats, DLLs, & MSI files:
- For creating payloads for windows Host, then their are many options for it.
	- Dlls, batch files, MSI packages and even PowerShell scripts are some common methods to use.
	
	- ### Payloads types to Consider:
		- `DLLs`:
			- A Dynamic Linking Library used in Microsoft Operating System to provide shared code and data that can be used by many different programs at once.
			- These files allows the user to have application that are dynamic and easier to update.
			- injecting a malicious DLL or hijacking a vulnerable library on the host can elevate the privileges and/or bypass the UAC.
	
		- `Batch`:
			- Batch files are text-based DOS scripts utilized by systems admins to complete multiple tasks through the command-line interpreter.
			- These files end with an extension of `.bat` .
			- Can be run on the host in an automated fashion.
			- Can be used to perform basic enumeration steps and feed back over the open port.
		
		- `VBS`:
			- VBScript is a lightweight scripting language based on Microsoft's Visual Basic .
			- It is used as a client-side scripting language in webservers to enable dynamic web page.
			- It can be used for phishing and other attacks.
		
		- `MSI`:
			- `.MSI` files serve as an installation database for the windows Installer.
			- While installation a new application, the installer will look for the `.msi` file to understand all of the components required and how to find them.
			- can run a payload using `.msi` file.
		
		- `PowerShell`:
			- It is both shell environment and scripting language.
			- It is a dynamic language based on the `.NET`.
### Tools, Tactics, and Procedures for Payload Generation, Transfer, and Execution:

- ## Payload Generation:

	- `MSFvenom & Metasploit-Framework`
	
	- `Payloads All The Things` | https://github.com/swisskyrepo/PayloadsAllTheThings | find many different resources and cheat sheets for payload generation and general methodology.
	
	- `Mythic C2 Framework` | https://github.com/its-a-feature/Mythic | The C2 framework is an alternative option to Metasploit as a Command and Control.
	
	- `Nishang` | https://github.com/samratashok/nishang | it is a framework collection of Offensive Powershell implants and scripts.
	
	- `Darkarmour` | https://github.com/bats3c/darkarmour | it is a tool to generate and utilize obfuscated binaries for use against Windows hosts.

## CMD-Prompt and Power[Shell]s:

- There are 2 shells in Windows to utilize by default:
	- `CMD{Command Prompt}`
	- PS{PowerShell}


