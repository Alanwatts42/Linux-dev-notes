# Bash Notes

<br>
<br>
<br>

# Useful Commands

<br>

### `readlink -f /foo/bar/symlink`
---
| Shows actual file path for a symlink. In other words, you can use this on a 
symlink to find out where it leads. The `-f` arg is only necessary if you want 
to trace it further than one level, otherwise `readlink /foo/symlink` is 
sufficient to follow a symlink one level down, which is usually all you need 
since most symlinks are not nested deeply enough to need `-f`.

``` # for this example the symlink (--> = one level) is:  ~/.foo --> ~/dir/folder/.foo -- 
# --> /usr/local/bar/dir/.foo

readlink ~/.foo
# output:  ~/dir/folder/.foo

readlink -f ~/.foo
# output: /usr/local/bar/dir/.foo
```

<br>
<br>

### `ls 'long-ass list of things' | grep 'specific thing'` 
---
| Parses text within the terminal, typically used in conjunction with `|` to 
chain it together with a prefix command that outputs a large amount of text. 
The typical use-case for this command assumes two things: The first assumption 
is that you have a single or a small number of target search terms for what 
you want to find, or you're looking for one specific thing. The second assumption 
is that what you're looking for is hidden within, or is one of, a large number 
of other files, directories, or other words in a text file. `grep` can be used 
to find or parse out whatever text you want to find, and can find from within 
any text that you can find a way to output to the terminal and chain it together 
with your search term using `| grep`, or otherwise find a way to use `grep` 
on, however that may be.

```
# example directory is $HOME/.zsh/ and contains about two dozen other files

ls -a
# output: ls -a lists all files in the directory, including 'init.zsh'

ls -a | grep init.zsh
# output: init.zsh

# 'ls -a' still runs, and lists all files in the directory '| grep' then parses
# this list of files and outputs a new list containing any files within the first list 
# that match the search term 'init.zsh' and filters out any that don't. 
# in this example, since only one file fits this search, only one file is listed.
```

---


<br>
<br>
<br>


# .Bashrc and configuration

<br>

# Functions - 
| Similar to aliases, but can have things like parameters/variables

### Function for "apt-grab <program> = "sudo apt-get -f install <program> --install-suggests"

```
apt-grab(){
    "sudo apt-get install ${1} --install-suggests"
```

## Aliases - examples found in /usr/share/doc/bash-doc/examples

Essentially these are just shortcuts for bash commands that you can create yourself by adding
them to the .bashrc or, using a line of code in .bashrc that specifies another file that the
computer should look at for additional (or even all of the user-added) shortcuts. 

My shortcuts are in a file called .bash_aliases that I saved to the same directory as the 
.bashrc file. Details on ways to set up your .bashrc and aliases can be found in 
`/usr/share/doc/bash-doc/examples/` as long as you the bash-doc package installed. If 
not, just type `sudo apt install bash-doc` into your terminal, and the examples folder should 
appear where it should be. 

Once you know where to add your aliases, their format is very straightforward. Each one starts with `alias` followed by the name of your alias, then an equals sign, open quotes (single or double should both work fine), then type the entire bash command you want the alias to be assigned to, and of course close the quotes at the end, and that's it. Here's what it looks like:

`alias <alias name>="<bash command>"`

or, let's say I'm creating an alias called 'apt-up' that will be used to run "sudo apt-get 
update && sudo apt-get dist-upgrade" here's what I would put in my .bash_aliases (or .bashrc)
to do that:

```
alias apt-up="sudo apt-get update && sudo apt-get dist-upgrade"
```

# setopt AUTO_CD

If you are looking for a way to shorten directory names, I suggest looking into Named Directories and the `AUTO_CD` option instead of aliases:
`
hash -d w=~/Documents/UoMWorkspace/Semester2
hash -d j=~/Documents/UoMWorkspace/Semester2/COMP17412
`
This allows you to use `~w` instead of `~/Documents/UoMWorkspace/Semester2` and `~j` instead of `~/Documents/UoMWorkspace/Semester2/COMP17412 (or ~w/COMP17412)`. So `cd ~j` is identical to `cd ~/Documents/UoMWorkspace/Semester2`. It also works as part of a path, e.g. `cat ~j/somedir/somefile`.

With
`
setopt AUTO_CD
`
zsh will automatically cd to a directory if it is given as command on the command line and it is not the name of an actual command. e.g.

`
% /usr
% pwd
/usr
% ~w
/home/YOURUSERNAME/Documents/UoMWorkspace/Semester2
`
