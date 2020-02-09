# cdalias - Directory aliases for bash
## Description
cdalias is a script which creates directory aliases for the  bash cd builtin.

## Alias Dictionary
The alias dictionary is stored in a file pointed to by **$CDDICTFILE** or **$HOME/.cdaliases** if not set. The format of this file is simple:

	# Comment
	alias definition # Comment
 
 Comments may also be placed at the beginning of the line and those lines, as well as blank lines, are ignored entirely.
 
This file is read each time the command is invoked, thus, it is a good idea to keep the alias list small. Much effort was made to make the reading of the dictionary as fast as possible.
 
### Warning!
The aliases dictionary file is overwritten when adding or removing aliases. Comments are *not* maintained. To prevent this behavior, do not use the **-a** or **-r** options and edit the file directly. 
 

Additional options have been added to the cd command:

		-a alias definition - store new alias definition and exit or
		-a alias:definition (see below) 
		-list  list the directory aliases and exit
		-o     cd will act like popd, although directory 
		       aliases are then irrelevant
		-p     cd will act like pushd
		-r alias removes the alias.
		-h 	   Will display the internal help for cd, 
		       then help on these options and exit

## Installation
### Requirements
1. A *NIX operating system or other system that uses BASH.
2. Bash version 4 or greater. 

### Copy File
Copy cdalias to a directory on your path. If you do not create an aliases dictionary, the two basic aliases will be used. Adding a new alias will write the dictionary. 

To make this work within Bash create a global shell function in .bashrc or some other Bash startup, as:

	function cd() { eval $(~/bin/cdalias "$@"); } 
	export -f cd

 Once this is put in place, you may use cd as you always do with the additional benefit of being able to type **cd *alias* ** and get to the path pointed by *alias*

 The built-in aliases, when there is no dictionary file, are:
 
 	...	gets to the parent of the parent, or ../..
 	.... gets to the parent of the parent of the parent, or ../../..

 ## Aliases and Definitions
 New aliases are parsed using two methods. The first is a simple "alias definition" syntax where there are is not whitespace in the alias. The second is an alias name with spaces and the definition, separated by a colon. E.g.: 		
 	"some dir:/var/adm/some/long/dir/path/nobody/wants/to/type/out"

