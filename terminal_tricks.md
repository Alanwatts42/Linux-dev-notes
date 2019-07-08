# Terminal Tricks

<br>

# search commands
---

<br>


## `find`

### behavior: 
    `find ` with no search term will default to displaying a recursive list of files in the current directory, and any files in child directories, sort of like a `ls` on steroids.


### location: 
    it is a good idea to specify where your search will start, which you do by putting an indicator of the directory, like `.` for the cwd or `~` for home, etc. `find` recursively searches through everything using this as a starting point.


### file name search: 
    `find -name 'search'`

### name search ignoring case: 
    `find -iname 'search'`


### patterns: 
    `find 'p*tterns.*y'`


### directory search:
    `find -path '*folder'` will find a directory called 'folder' even if it's within other directories, with the * wildcard replacing the first part of the path to get to 'folder' such as ``'/dir/home/folder'``


### finding properties of search objects: 
    `find . -executable` find all executable objects starting with current directory. 
    `find ~ -empty` find all zero byte objects starting with home directory.


### types:
    `find . 'object' -executable -type f` find 'object' starting in cwd that is both executable and a file type object (hence `-type f`). 
    `find ~ 'oj' -type d` find 'oj' starting in home directory, showing only directory type objects (hence `-type d`)


### using other commands with find:
    `find . -name "fix_aptget.sh" -exec chmod -x '{}' \;` 
    
    which means:
            - search current dir for named object called "fix-aptget.sh".
            - if it is found execute `chmod -x` command.
            - The parameters that are passed to chmod are -x to remove the executable permissions and '{}' which represents the filename of the found file.
            - the final semicolon marks the end of the parameters that are going to be passed to `chmod`. this must be `escaped` by preceding it with a `\` backslash. hence: `\;` is used to end the `chmod` command and it's subsequent parameters and it's subsequent parameters.

---

<br>

## `locate`

you can use `locate` to quickly find what you're looking for via the database built in to the linux os, which must be updated if necessary using `sudo updatedb##`

### default behavior: 
    `locate doodlefuck` quickly searches all files for the string 'doodlefuck' and will just as quickly pull up a list of matching files such as perhaps: `/home/dave/doodlefuck/doodlefuck.html` and will simply list them one per line on the terminal output. 

### limiting results: 
    `locate -n 10 doodlefuck` limits the results of this search to the first 10 matching file names in the database listed as described above (one per line, full filename with location).

---

<br>

## `which`

---

<br>

## `whereis`

---

<br>

## `whatis`

---

<br>

## `apropos`

---


