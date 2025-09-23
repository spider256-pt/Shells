- Hypertext Preprocessors or PHP is an open-source general-purpose scripting language.
- Typically used as part of a web stack that powers a website
- PHP is the popular server-side programming language.
- PHP is used 78.6% of all website.
### PHP-Based Web Shell:
- PHP processes code & commands on the server-side.
- Can use pre-written payloads to gain a shell through the browser or initiate a reverse shell session.
- Can take advantage of the vulnerability. 

### Bypassing The File Type Restriction:

- ###### Prerequisite:
	- https://github.com/WhiteWinterWolf/wwwolf-php-webshell
		- can download this or copy and paste the source code into a `.php` file
	- Should have basic knowledge of Burp suite.
	- Should know how to configure a web-browser for `BurpSuite`. 

- ###### Steps:
	- with burp open and the web browser proxy settings properly configured.
	- choose the .php file that is going to upload on the web-browser.
	- After this it will seem like web page is hanging, but that's because Burp is forwarding the HTTP requests.
	- Forward request until the POST request containing the `.php` file upload.
	- Change the `Content-type` from `<anything>`  to `<allowed_file_extension>`
		
		- ###### from 
			- `Content-Type: application/x-php`
		- ###### to 
			- `Content-Type: image/gif`
	- This is the essential trick the server and allow the user to upload a `.php` file by bypassing the file type restriction.
	- Then select `forward` twice, the file will be submitted.
	- Turn off the burp.

- ## Considerations when Dealing with Web Shell:
	
	- Web applications sometimes automatically delete files after a pre-defined period.
	- Limited interactivity with the operating system in terms of navigating the file system, downloading and uploading files, chaining commands together may not work, slowing progress, especially when performing enumeration -Potential instability through a non-interactive web shell.
	-  Greater chance of leaving behind proof that we were successful in our attack

[[Shells]]