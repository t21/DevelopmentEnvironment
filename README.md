# DevelopmentEnvironment

## Mac

### Install git
Install git by installing XCode.

### Configure git completion and git prompt
Add the following to ~/.bash_profile (create file if it does not exist):

```
#!/bin/bash

# Define colors
green="\[\033[0;32m\]"
blue="\[\033[0;34m\]"
purple="\[\033[0;35m\]"
lightblue="\[\033[0;36m\]"
default="\[\033[0m\]"

# Enable git completion
GIT_COMPLETION_FILE=/Applications/Xcode.app/Contents/Developer/usr/share/git-core/git-completion.bash
if [ -f $GIT_COMPLETION_FILE ]; then
  source $GIT_COMPLETION_FILE
fi

# Setup git command prompt
GIT_PROMPT_FILE=/Applications/Xcode.app/Contents/Developer/usr/share/git-core/git-prompt.sh
if [ -f $GIT_PROMPT_FILE ]; then
  source $GIT_PROMPT_FILE
fi
export GIT_PS1_SHOWUPSTREAM="auto verbose"
export GIT_PS1_SHOWCOLORHINTS="yes"
export GIT_PS1_SHOWDIRTYSTATE=1
export GIT_PS1_SHOWSTASHSTATE=true
export GIT_PS1_SHOWUNTRACKEDFILES=true
#export PS1="$green\u$purple\h$blue\w$(__git_ps1)$default $ "
export PROMPT_COMMAND='__git_ps1 "$green\u$default@$purple\h$default:$lightblue\w$default" " \\\$ "'

```

### Configure global gitignore file
Create global gitignore file
```
echo ".DS_Store" > ~/.gitignore_global
```
Make git aware of the global gitignore file
```
git config --global core.excludesfile ~/.gitignore_global
```

### Configure user and email 
```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Setup an SSH key
```
ssh-keygen
```
Hit return a couple of times -- leave password blank if you want.
```
cat ~/.ssh/id_rsa.pub | pbcopy
```
Paste that code into your settings page on your repository host(s).
