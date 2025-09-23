### How does aspx work ?

- ASPX stands for `Active Server Page Extended` is a file type/extension written for Microsoft's ASP.NET Framework.
- If A web server running the ASP.NET framework, web form pages can be generated for users to input data. On the server side the information will be converted into HTML
- Then ASPX-based web-shell can take the advantage to control the underlying Windows operating System. 

### Antak Webshell

- Antak is also a web shell that is built in ASP.NET.
- Antak is included in `Nishang project`(https://github.com/samratashok/nishang).{`Nishang is an Offensive PowerShell toolset`}
- Antak utilizes PowerShell to interact with the Host.

#### Working with Antak:
- The Antak file can be found or can be moved at `/usr/share/nishang/Antak-WebShell` directory.
- The Antak Webshell works like PowerShell console.
- It executes each commands as a new process.
- It also executes scripts in memory and encode commands.

So Antak Can be the powerful webshell tool in action.