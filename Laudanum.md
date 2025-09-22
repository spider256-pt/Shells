- Laudanum is a repository of ready-made files that can be used to inject onto a victim and receive back access via a reverse shell.
-  https://github.com/jbarcia/Web-Shells/tree/master/laudanum
- These repo includes injectable files for many different `web application` languages to include:
	- `asp`
	- `aspx`
	- `jsp`
	- `php` 


- ### Working with Laudanum:

	- The laudanum files can be found in the `/usr/share/laudanum` directory.
	- Need to edit the file first to insert it in the targets system.
	- Ensure to read the contents and comments.

- ### Laudanum Demonstration:

	- For Demonstration purpose let assume `10.10.14.12` as the target.
	- After scanning ports we find out that a web application exist.
	- lets see if we can get a web shell using `laudanum`.
	- First we need to add an entry into `/etc/hosts` file.
		- `<target_ip> <domain_name.com>`
		- `10.10.14.12`  ` www.testdomain.com`
	- ###### Move a copy for Modification:
		- `cp /usr/share/laudanum/aspx/shell.aspx /home/tester/demo.aspx`
		- use a text-editor to modify the file.
		- Once done with the modification part, if we get a upload vector then we can upload our `demo.aspx` file to the web application or the web server in order to get a web shell.
		- Once we got the shell use the command as per the web shell based on the Os.
		