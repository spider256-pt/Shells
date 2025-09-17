# Metasploit

It is an automated attack framework developed by `Rapid7` that streamlines the process of exploiting vulnerabilities through the use of pre-built modules that contains easy-to-use option exploit vulnerabilities and deliver payloads  to gain a shell on a vulnerable system.

## Practicing with Metasploit

- ##### Commands to start a metasploit attack:
	- `sudo msfconsole`

- If found any vulnerability like any version or any services:

	- `search <name_of_the_service>`
		- This will return the long list of the matching Modules.
		- Each module has a number listed on the format:
			- Name, Disclosure `Date`, `Rank`, `Check` and `Description`.
			- Example:
				- `56 /exploit/windows/smb/psexec`
				
- ##### Option Selection:
		- For selecting an option apply `use` keyword.
			- `use <module>/<the_list_number>`
		
- ##### Examining an Exploit's Option's 
- For examining an Exploits options use show options commands for seeing the exploit option
	- like for verifying if the both `lhost` and `rhost` parameter are set properly or not 

- ##### Setting Options:
	- To set any value to a parameter in a exploit use `set` keyword.
		- `set Lhost <Ip>`
		- `set Rhost <IP>`
		- `set <option_name> <value>`

- ##### Exploit
	- Use `exploit` or run keyword to initiate the attack.