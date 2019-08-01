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

<br>

# Possible better options for a Terminal emulator (Lubuntu)

## Current Terminal: Terminator 
### Reasons for switching:
 - While it works great in some ways, I tend to get too bogged down trying to get it to look and do what I want it to do.
 - The main selling point of Terminator, which is the ability to split 
a terminal into multiple panels, is available in multiple other similar
terminal emulators, some of which are superior in other ways as well.
 - Terminator has a bespoke configuration scheme, and is especially difficult when dealing with changing color schemes, or even saving the one you liked.

<br>

## Requirements for new Terminal solution:
 - "Dotfile" config scheme, similar to how vim is configured.
 - Retains existing color syntax highlighting imposed by vim. Doesn't 
necessarily need to drive any changes in the color of certain syntax 
beyond the traditional colorscheme options, just needs to not interfere 
with what's already being done.
 - Must be somehow better than the ones I already have availble to me. 
This requirement is somewhat obvious, since if what I have is already 
better than what's out ther, then I might as well use what I already have, 
such as Lxterminal or xvt.

## Possible new Terminal solutions:
Ordered top to bottom by when they are mentioned on this reddit thread:
<a href='https://www.reddit.com/r/linux/comments/aeqitl/preferred_terminal_emulator/'>
r/linux thread: preffered terminal emulator
</a>
The reddit dudes are probably arrogant pricks, but they're typically 
arrogant pricks who know a thing or two about a thing or two.


1. Tilix | https://gnunn1.github.io/tilix-web/
    - very similar to Terminator, but seemingly without any of the slight issues I ran into with Terminator.
    - Enables saving of colorschemes on .json files, which directly solves the problem I was having the most frustration with.
    - Shortcut keys are familiar, and I figured out how to customize them whereas I couldn't with Terminator, possibly not anyone else's fault since I don't have a mouse, but I was impressed that I could do it on tilix.
    - It's not 100% perfect, since I can't completely configure or store eerything to github in ddotfiles like a super badass hacker dude, but that's overkill anyway, and for mst if not all everyday use, this one will do fine.
    Verdict: 9/10

2. Termite | https://github.com/thestinger/termite/
    - A lot less gui-driven. Requires some potentially difficult or confusing setup process. There's not much in the way of install docs, at least ver little that I can easily find and none included right up front. 
    - Much more friendly to the approach a power-user might prefer, and which many will be familiar with if they've dabbled at all with vim's .vmrc configuration. That said, it's probably better if nothing attached to ny

3. Xfce-Term

