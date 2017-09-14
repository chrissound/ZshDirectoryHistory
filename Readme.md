# Woooooooo

## What problem does this solve?
This allows you to store the command line history per directory. This is completely independent of the global history.

## What limitations does this have?
It pollutes a .directory_history file in every directory you run a command in. 

## Requirements
FZF and ZSH.

## How do I use this? 
Add this to your ~/.zshrc and then press CTRL+P

## Code:

```
#directory based history
beepboop () {
  echo -n "$1" >> .directory_history
}

openFzfDirectoryHistory() {
  RBUFFER=$(cat .directory_history | fzf)
  zle redisplay
	zle end-of-line;
	zle accept-line;
}

zle     -N   openFzfDirectoryHistory
bindkey '^P' openFzfDirectoryHistory
add-zsh-hook zshaddhistory beepboop
```
