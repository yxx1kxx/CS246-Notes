# CS 246 Notes

#### Unix file system

Home dir: 

```bash
~/$home
```

Home dir of user "Vicky":

```bash
~Vicky
```



#### The UNIX shell:

```bash
% echo $0 ## repeat the current shell that is being used
-tcsh
% bash ## change to bash
$ echo $0 ## repeat the current shell that is being used
bash
#shell prompt: $ means bash, % means tcsh
```



#### Commands in the UNIX shell

```bash
pwd ## Tells the current directory
cd ## Go back home
cd - ## to the previous dir
cd .. ## to the parent of the current dir
cd . ## leaves you where you are 
ls # list dir/files under current dir
./somefile # execute "somefile"
ls -a # list all files/dir including hidden files
cat someFile #read "somefile"
alias rm="rm -iv" #substitue rm -iv with rm, when type rm, exxcute rm -iv
echo #repeat

```



There is a predefined shell variable PATH for the shell to search for external programs. The value of PATH is typicially set in the .bashrc file, which is executed as the shell starts. 



```bash
which/type somecmd ## tells you what the command somecmd is

$ which ls
/bin/ls

$ ls -F # list all files/dir with special symbols at the end 
Afile@ Bfile* Cfile.cc Dfile/
## *-executeable /-dir @-symbolic way
$ ls -F -G # list all files/dir with special symbols at the end with colors
$ echo $PATH # location of path


$ echo no place like HOME
no place like HOME
$ echo " no place like HOME"
 no place like HOME
$ echo "no place like $HOME"
no place like /Users/vicky
$ echo no place like $HOME
no place like /Users/vicky
$ echo 'no place like $HOME'
no place like $HOME
## single quotes prevent from variables

```



#### Globbing: Command-line pattern

If you run a shell, it means you are running command-line programs:

```bash
$ command -opt1 arg1 -op2 arg2 arg3
```

We can access the command line arguments programmatically using agree and argc parameters to the main function in a C/C++ program.

Globbing patterns only apply to args(oftern, file names), not commands or options

**Globbing:**

```bash
* matches 0 or more characters
? matches 1 characters
{...} matches any alternative in the set
[...] matches 1 character in the set
[!...] matches 1 character not in the set
# can create ranges uding hyphen
[0-3] matches 0 1 2 3
[a-zA-Z] matches lower or upper case letter
[!a-zA-Z] matches non-letter
# hyphen is escaped by putting it at the start or end of set
[-?*]* matches file names starting with -,?,or *
# Note: * doesn't match dotfiles(start with dot, ex .bashrc)
ls *fnord* will find xxxfnordster but not .fnordster, if they exist in the current dir

```



```bash
# assume there are q1a.c q2b.h q3c.cc q4test.cc q5.cpp in the current dir
$ echo q*
q1a.c q2b.h q3c.cc q4test.cc q5.cpp
## matches the filenames start with q
$ echo q*.??
q3c.cc q4test.cc
$ echo *.{C,cc,cpp}
q1a.c q3c.cc q4test.cc q5.cpp
$ echo q[12]*
q1a.c q2b.h
$ echo q[!1]*
q2b.h q3c.cc q4test.cc q5.cpp
```



```bash
$ ls *.pdf *.txt
# will list all PDF and plain text files in the current dir
$ rm *.docx *.doc 
# remove the corresponding files in the cur dir

```



Globbing and quoting:

Globbing is turned off inside single and double quotes

- Single quotes: Everything up to the next single quote is protected (incl. NL, double quotes)
- Double quotes: Protect everything except double quote, backquote, and $VARs







