# cdalias - Directory aliases for bash
## Description
cdalias is a script which creates directory aliases for the  bash cd builtin.

## Alias Dictionary
The alias dictionary is stored in a file pointed to by `$CDDICTFILE` or `$HOME/.cdaliases` if not set. The format of this file is simple:

	# Comment
	alias:definition # Comment

### Alias Name Restrictions
Alias names must not contain leading dashes or any slashes or, generally special characters. For aliase names with spaces use the second syntax of 
 `alias name:/some/long/path`. Other restrictions such as slashes, dashes and special characters apply. 

Comments may also be placed at the beginning of the line and those lines, as well as blank lines, are ignored entirely.
 
This file is read if there is no in-memory dictionary and reread if the dictionary is modified.
 
### Warning!
The aliases dictionary file is overwritten when adding or removing aliases. Comments are *not* maintained. To prevent this behavior, do not use the `-a` or `-r` options and edit the file directly. 
 

Additional options have been added to the cd command:

		-a alias definition - store new alias definition and exit or
		-a alias:definition (see below) 
		-o     cd will act like popd, although directory 
		       aliases are then irrelevant
		-p     cd will act like pushd
		-r alias removes the alias.
		-list  list the directory aliases and exit
		-reload reload aliases from dictionary
		-h 	   Will display the internal help for cd, 
		       then help on these options and exit

## Installation
### This procedure is different from previous versions and the old methods wont work.

### Requirements
1. A *NIX operating system or other system that uses BASH.
2. Bash version 4 or greater. 

### Copy File
Copy cdalias to a directory on your path. If you do not create an aliases dictionary, the two basic aliases will be used. Adding a new alias will write the dictionary.

Add a line to .bashrc or other .bash startup file with: 
`source /path/to/script/cdalias`

This will initialize the in-memory dictionary and create the alias for cd. To stop using cdalias, remove the entry in the startup file and execute `unalias cd`. 

 Once this is put in place, you may use cd as you always do with the additional benefit of being able to type `cd <alias>`  and get to the path pointed by `alias`

## Aliases and Definitions

### Built-in Aliases
 The built-in aliases, when there is no dictionary file, are:
 
`...	gets to the parent of the parent, or ../..`

`.... gets to the parent of the parent of the parent, or ../../..`

### Defining New Aliases
New aliases may be added using the -a option to cdalias are parsed by cdalias using two methods. The first is a simple `alias definition` syntax where there are not whitespace in the alias. The second is an alias name with spaces and the definition, separated by a colon. E.g.: 
 	`some dir:/var/adm/some/long/dir/path/nobody/wants/to/type/out`

### Adding alises directly to the Alias Dictionary

Aliases may be added, with optional comments, to the alias dictionary. The format is listed above. **Note**: Comments are lost in this file when the -a or -r options are used.
 	
