# my-sys-config

## zsh setup

**On macbook pro M1, antigen always has issue of oh-my-zsh related error. No color and suggestions after openning >3 terminals! So I found this is the most reliable way to intall them.**
1. zsh-autosuggest:  
   use the manual install method: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#manual-git-clone
2. syntax:  
   fast-syntax seems not work, I used the zsh-syntax-highlighting w/ brew install:  Mac OS X / Homebrew: brew install zsh-syntax-highlighting


final:

```zsh
##################################

autoload colors && colors
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

######## setup git branch name #####
# Load version control information
autoload -Uz vcs_info
precmd() { vcs_info }

# Format the vcs_info_msg_0_ variable
zstyle ':vcs_info:git:*' formats '%b'

# Initialize command prompt
# export PS1="%n@%m:%~%# "
# Set up the prompt (with git branch name)
# set color:   %{$fg[blue]%} - blue, %{$fg[green]%} - green, etc...
setopt PROMPT_SUBST
PROMPT='@%m %{$fg[green]%}${PWD/#$HOME/~} %{$fg[blue]%}{${vcs_info_msg_0_}}%{$fg[red]%}>'
###################################

### ls color ###
export CLICOLOR=1
###############


################ my custom zshrc ########
# Enable 256 color to make auto-suggestions look nice
export TERM="xterm-256color"


export HISTSIZE=50000000
alias c="clear"
alias ghist="history | sort -rn | grep"
alias prettyjson="python -m json.tool"
alias playSound='afplay ~/myown/5sec_music.mp3 &'
set -o vi

```
