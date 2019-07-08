# `.bash_aliases` - examples found in `/usr/share/doc/bash-doc/examples`

<br>

This markdown file is a reformatted version of my `~/.bash_aliases` file, which is a companion file to my `~/.bashrc` that contains... aliases. As shocking as that may be. 


<br>
<br>

# Functions - similar to aliases, but can have things like parameters/variables

<br>

## Function for "apt-grab <program> = "sudo apt-get -f install <program> --install-suggests"
```
apt-grab(){
    "sudo apt-get install ${1} --install-suggests"
}

```
```
wifi-func(){
    "sudo nmcli dev wifi connect ${1} password ${2}"
}
```

<br>

# Aliases - bash command shortcuts

## Apt or apt-get shortcuts for convenience
```
alias apt-up="sudo apt-get update && sudo apt-get dist-upgrade"
```

## Wifi operations via the terminal - very long, very specific, aliases therefore very necessary
```
alias wifi-go="sudo nmcli dev wifi connect"
alias mifi-go="sudo nmcli dev wifi connect MY_EX-WIFI_GOT_THE_HOUSE password amqv294#"
alias wifi-scan="sudo nmcli dev wifi"
```

## Pip, pipenv, and python
```
alias py="Python3 -m"
alias pip-go="pip3 install --user"
alias pipenv-go="pipenv install"
```

