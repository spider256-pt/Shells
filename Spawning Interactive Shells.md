- ##### /bin/sh -i

	- This command will execute the shell interpreter specified in the path in interactive mode (-i)

- ##### Perl

	- If the programming language Perl is present on the system, then
	- `perl -e 'exec "/bin/sh";'`
	- `perl: exec "/bin/sh";`

- ##### Ruby

	- If the programming language Ruby is present on the system, then
	- `ruby: exec "/bin/sh"`

- ##### Lua 

	- If the programming language Lua is present on the system,   then it can be used for `os.execute` method to execute shell interpreter
	- `lua: os.execute('/bin/sh')`

- ##### AWK

	- AWK is a C-like pattern scanning and processing language present on most UNIX/Linux-based systems.
	- Widely used by developers and sysadmins to generate the reports.
	- It can also be used  to spawn an interactive shell.
	- `awk 'BEGIN {system("/bin/sh")}'`

- ##### Find

	- Find is a command present on most Unix/Linux systems widely used to search for & through files and directories using various criteria.
	- `find / -name nameoffile -exec /bin/awk 'BEGIN {system("/bin/sh")}' \;
	- `find . -exec /bin/sh \; -quit` 

- ##### VIM

	- The shell interpreter language from within the popular command-line-based text-editor VIM.
	- `vim -c ':!/bin/sh'`
	- ###### Vim escape:
		- `vim`
		- `:set shell=/bin/sh`
		- `:shell`

- ##### Execution Permission Consideration:

	- Run this command to list the file properties and permissions:
	
		- `ls -la <path/to/fileorbinary>`
	
	- To check the sudo permissions:
	
		- `sudo -l`



