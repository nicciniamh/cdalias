# cdalias - Directory aliases for bash
## Description
cdalias is a script which creates directory aliases for the  bash cd builtin.Aliases are stored in the file pointed to by **CDDICTFILE** or **$HOME/.cdaliases** if not set. The format of this file is simple:

	 alias definition # Comment
 
 Comments may also be placed at the beginning of the line and those lines, as well as blank lines, are ignored entirely.

 Additional options have been added to the cd command:

		-a alias definition - store new alias definition and exit  
		-list  list the directory aliases and exit
		-o     cd will act like popd, although directory 
		       aliases are then irrelevant
		-p     cd will act like pushd
		-r alias removes the alias.
		-h 	   Will display the internal help for cd, 
		       then help on these options and exit

## Installation
Copy cdalias to a directory on your path. If you do not create an aliases dictionary, the two basic aliases will be used. Adding a new alias will write the dictionary. 

To make this work within Bash create a global shell function in .bashrc or some other Bash startup, as:

	function cd() { eval $(~/bin/cdalias $@); } 
	export -f cd

 Once this is put in place, you may use cd as you always do with the additional benefit of being able to type **cd *alias* ** and get to the path pointed by *alias*

 The built-in aliases, when there is no dictionary file, are:
 
 	...	gets to the parent of the parent, or ../..
 	.... gets to the parent of the parent of the parent, or ../../..

