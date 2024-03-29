# my-sys-config

## zsh setup

**On macbook pro M1, antigen always has issue of oh-my-zsh related error. No color and suggestions after openning >3 terminals! So I found this is the most reliable way to intall them.**
1. zsh-autosuggest:  
   use the manual install method: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#manual-git-clone
2. syntax:  
   fast-syntax seems not work, I used the zsh-syntax-highlighting w/ brew install:  Mac OS X / Homebrew: brew install zsh-syntax-highlighting
3. tree:
   brew install tree
4. tmux
   brew install tmux

final:

```zsh
##################################


######### use autosuggestion & syntax highlight
autoload colors && colors
# autoload compinit && compinit

###########################################

## enable prefix history search!! ###
# https://unix.stackexchange.com/questions/97843/how-can-i-search-history-with-text-already-entered-at-the-prompt-in-zsh
bindkey "^[[A" history-beginning-search-backward
bindkey "^[[B" history-beginning-search-forward
#####

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
# set shortened prompt:  %3~ - based on '~', only show latest 3 layers of directory. example:  a/b/c, ~/d/e, etc... 
setopt PROMPT_SUBST
PROMPT='@%m %{$fg[green]%}%3~ %{$fg[cyan]%}{${vcs_info_msg_0_}}%{$fg[red]%}>'
###################################

### ls color ###
export CLICOLOR=1
###############

############# enable autosuggest && syntax highlighter ####
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh


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

### terminal setup ####
Save this to `my-cfg.terminal`, and use `Terminal` to import it. 

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>BackgroundBlur</key>
	<real>0.15255442713753561</real>
	<key>BackgroundColor</key>
	<data>
	YnBsaXN0MDDUAQIDBAUGBwpYJHZlcnNpb25ZJGFyY2hpdmVyVCR0b3BYJG9iamVjdHMS
	AAGGoF8QD05TS2V5ZWRBcmNoaXZlctEICVRyb290gAGmCwwXHR4lVSRudWxs1Q0ODxAR
	EhMUFRZcTlNDb21wb25lbnRzVU5TUkdCXE5TQ29sb3JTcGFjZV8QEk5TQ3VzdG9tQ29s
	b3JTcGFjZVYkY2xhc3NPEBIwIDAgMCAwLjkwMjEyNDI5NzhPEBMwIDAgMCAwLjkwMjEy
	NDI5NzgAEAGAAoAF0xgRGRobHFVOU0lDQ1lOU1NwYWNlSUSAA4AEEAxPEQIYAAACGGFw
	cGwEAAAAbW50clJHQiBYWVogB+YAAQABAAAAAAAAYWNzcEFQUEwAAAAAQVBQTAAAAAAA
	AAAAAAAAAAAAAAAAAPbWAAEAAAAA0y1hcHBs7P2jjjiFR8NttL1PetoYLwAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAKZGVzYwAAAPwAAAAwY3BydAAAASwAAABQd3Rw
	dAAAAXwAAAAUclhZWgAAAZAAAAAUZ1hZWgAAAaQAAAAUYlhZWgAAAbgAAAAUclRSQwAA
	AcwAAAAgY2hhZAAAAewAAAAsYlRSQwAAAcwAAAAgZ1RSQwAAAcwAAAAgbWx1YwAAAAAA
	AAABAAAADGVuVVMAAAAUAAAAHABEAGkAcwBwAGwAYQB5ACAAUAAzbWx1YwAAAAAAAAAB
	AAAADGVuVVMAAAA0AAAAHABDAG8AcAB5AHIAaQBnAGgAdAAgAEEAcABwAGwAZQAgAEkA
	bgBjAC4ALAAgADIAMAAyADJYWVogAAAAAAAA9tUAAQAAAADTLFhZWiAAAAAAAACD3wAA
	Pb////+7WFlaIAAAAAAAAEq/AACxNwAACrlYWVogAAAAAAAAKDgAABELAADIuXBhcmEA
	AAAAAAMAAAACZmYAAPKnAAANWQAAE9AAAApbc2YzMgAAAAAAAQxCAAAF3v//8yYAAAeT
	AAD9kP//+6L///2jAAAD3AAAwG7SHyAhIlokY2xhc3NuYW1lWCRjbGFzc2VzXE5TQ29s
	b3JTcGFjZaIjJFxOU0NvbG9yU3BhY2VYTlNPYmplY3TSHyAmJ1dOU0NvbG9yoiYkAAgA
	EQAaACQAKQAyADcASQBMAFEAUwBaAGAAawB4AH4AiwCgAKcAvADSANQA1gDYAN8A5QDv
	APEA8wD1AxEDFgMhAyoDNwM6A0cDUANVA10AAAAAAAACAQAAAAAAAAAoAAAAAAAAAAAA
	AAAAAAADYA==
	</data>
	<key>CursorColor</key>
	<data>
	YnBsaXN0MDDUAQIDBAUGBwpYJHZlcnNpb25ZJGFyY2hpdmVyVCR0b3BYJG9iamVjdHMS
	AAGGoF8QD05TS2V5ZWRBcmNoaXZlctEICVRyb290gAGmCwwXHR4lVSRudWxs1Q0ODxAR
	EhMUFRZcTlNDb21wb25lbnRzVU5TUkdCXE5TQ29sb3JTcGFjZV8QEk5TQ3VzdG9tQ29s
	b3JTcGFjZVYkY2xhc3NPECgwLjY4NTI5Njg3NTUgMC43MDU5MTc5MjI5IDAuMjM5ODI2
	MTg3OCAxTxAnMC42MTk3NzUxNzYgMC42NjAzNzY2MDg0IDAuMDcxMzU0Mjk5NzgAEAGA
	AoAF0xgRGRobHFVOU0lDQ1lOU1NwYWNlSUSAA4AEEAxPEQIYAAACGGFwcGwEAAAAbW50
	clJHQiBYWVogB+YAAQABAAAAAAAAYWNzcEFQUEwAAAAAQVBQTAAAAAAAAAAAAAAAAAAA
	AAAAAPbWAAEAAAAA0y1hcHBs7P2jjjiFR8NttL1PetoYLwAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAKZGVzYwAAAPwAAAAwY3BydAAAASwAAABQd3RwdAAAAXwAAAAU
	clhZWgAAAZAAAAAUZ1hZWgAAAaQAAAAUYlhZWgAAAbgAAAAUclRSQwAAAcwAAAAgY2hh
	ZAAAAewAAAAsYlRSQwAAAcwAAAAgZ1RSQwAAAcwAAAAgbWx1YwAAAAAAAAABAAAADGVu
	VVMAAAAUAAAAHABEAGkAcwBwAGwAYQB5ACAAUAAzbWx1YwAAAAAAAAABAAAADGVuVVMA
	AAA0AAAAHABDAG8AcAB5AHIAaQBnAGgAdAAgAEEAcABwAGwAZQAgAEkAbgBjAC4ALAAg
	ADIAMAAyADJYWVogAAAAAAAA9tUAAQAAAADTLFhZWiAAAAAAAACD3wAAPb////+7WFla
	IAAAAAAAAEq/AACxNwAACrlYWVogAAAAAAAAKDgAABELAADIuXBhcmEAAAAAAAMAAAAC
	ZmYAAPKnAAANWQAAE9AAAApbc2YzMgAAAAAAAQxCAAAF3v//8yYAAAeTAAD9kP//+6L/
	//2jAAAD3AAAwG7SHyAhIlokY2xhc3NuYW1lWCRjbGFzc2VzXE5TQ29sb3JTcGFjZaIj
	JFxOU0NvbG9yU3BhY2VYTlNPYmplY3TSHyAmJ1dOU0NvbG9yoiYkAAgAEQAaACQAKQAy
	ADcASQBMAFEAUwBaAGAAawB4AH4AiwCgAKcA0gD8AP4BAAECAQkBDwEZARsBHQEfAzsD
	QANLA1QDYQNkA3EDegN/A4cAAAAAAAACAQAAAAAAAAAoAAAAAAAAAAAAAAAAAAADig==
	</data>
	<key>ProfileCurrentVersion</key>
	<real>2.0699999999999998</real>
	<key>RestoreLines</key>
	<integer>30000</integer>
	<key>TextBoldColor</key>
	<data>
	YnBsaXN0MDDUAQIDBAUGBwpYJHZlcnNpb25ZJGFyY2hpdmVyVCR0b3BYJG9iamVjdHMS
	AAGGoF8QD05TS2V5ZWRBcmNoaXZlctEICVRyb290gAGmCwwXHR4lVSRudWxs1Q0ODxAR
	EhMUFRZcTlNDb21wb25lbnRzVU5TUkdCXE5TQ29sb3JTcGFjZV8QEk5TQ3VzdG9tQ29s
	b3JTcGFjZVYkY2xhc3NPEBkwLjUzMzc1IDAuNTMzNzUgMC41MzM3NSAxTxAnMC40NTk0
	NDk2NDg5IDAuNDU5NDQ5NjQ4OSAwLjQ1OTQ0OTY0ODkAEAGAAoAF0xgRGRobHFVOU0lD
	Q1lOU1NwYWNlSUSAA4AEEAxPEQIYAAACGGFwcGwEAAAAbW50clJHQiBYWVogB+YAAQAB
	AAAAAAAAYWNzcEFQUEwAAAAAQVBQTAAAAAAAAAAAAAAAAAAAAAAAAPbWAAEAAAAA0y1h
	cHBs7P2jjjiFR8NttL1PetoYLwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAK
	ZGVzYwAAAPwAAAAwY3BydAAAASwAAABQd3RwdAAAAXwAAAAUclhZWgAAAZAAAAAUZ1hZ
	WgAAAaQAAAAUYlhZWgAAAbgAAAAUclRSQwAAAcwAAAAgY2hhZAAAAewAAAAsYlRSQwAA
	AcwAAAAgZ1RSQwAAAcwAAAAgbWx1YwAAAAAAAAABAAAADGVuVVMAAAAUAAAAHABEAGkA
	cwBwAGwAYQB5ACAAUAAzbWx1YwAAAAAAAAABAAAADGVuVVMAAAA0AAAAHABDAG8AcAB5
	AHIAaQBnAGgAdAAgAEEAcABwAGwAZQAgAEkAbgBjAC4ALAAgADIAMAAyADJYWVogAAAA
	AAAA9tUAAQAAAADTLFhZWiAAAAAAAACD3wAAPb////+7WFlaIAAAAAAAAEq/AACxNwAA
	CrlYWVogAAAAAAAAKDgAABELAADIuXBhcmEAAAAAAAMAAAACZmYAAPKnAAANWQAAE9AA
	AApbc2YzMgAAAAAAAQxCAAAF3v//8yYAAAeTAAD9kP//+6L///2jAAAD3AAAwG7SHyAh
	IlokY2xhc3NuYW1lWCRjbGFzc2VzXE5TQ29sb3JTcGFjZaIjJFxOU0NvbG9yU3BhY2VY
	TlNPYmplY3TSHyAmJ1dOU0NvbG9yoiYkAAgAEQAaACQAKQAyADcASQBMAFEAUwBaAGAA
	awB4AH4AiwCgAKcAwwDtAO8A8QDzAPoBAAEKAQwBDgEQAywDMQM8A0UDUgNVA2IDawNw
	A3gAAAAAAAACAQAAAAAAAAAoAAAAAAAAAAAAAAAAAAADew==
	</data>
	<key>TextColor</key>
	<data>
	YnBsaXN0MDDUAQIDBAUGBwpYJHZlcnNpb25ZJGFyY2hpdmVyVCR0b3BYJG9iamVjdHMS
	AAGGoF8QD05TS2V5ZWRBcmNoaXZlctEICVRyb290gAGmCwwXHR4lVSRudWxs1Q0ODxAR
	EhMUFRZcTlNDb21wb25lbnRzVU5TUkdCXE5TQ29sb3JTcGFjZV8QEk5TQ3VzdG9tQ29s
	b3JTcGFjZVYkY2xhc3NPECgwLjY3NjAwNjk0NDQgMC42NzYwMDY5NDQ0IDAuNjc2MDA2
	OTQ0NCAxTxAnMC42MTMxMzg3MzUzIDAuNjEzMTM4NzM1MyAwLjYxMzEzODczNTMAEAGA
	AoAF0xgRGRobHFVOU0lDQ1lOU1NwYWNlSUSAA4AEEAxPEQIYAAACGGFwcGwEAAAAbW50
	clJHQiBYWVogB+YAAQABAAAAAAAAYWNzcEFQUEwAAAAAQVBQTAAAAAAAAAAAAAAAAAAA
	AAAAAPbWAAEAAAAA0y1hcHBs7P2jjjiFR8NttL1PetoYLwAAAAAAAAAAAAAAAAAAAAAA
	AAAAAAAAAAAAAAAAAAAKZGVzYwAAAPwAAAAwY3BydAAAASwAAABQd3RwdAAAAXwAAAAU
	clhZWgAAAZAAAAAUZ1hZWgAAAaQAAAAUYlhZWgAAAbgAAAAUclRSQwAAAcwAAAAgY2hh
	ZAAAAewAAAAsYlRSQwAAAcwAAAAgZ1RSQwAAAcwAAAAgbWx1YwAAAAAAAAABAAAADGVu
	VVMAAAAUAAAAHABEAGkAcwBwAGwAYQB5ACAAUAAzbWx1YwAAAAAAAAABAAAADGVuVVMA
	AAA0AAAAHABDAG8AcAB5AHIAaQBnAGgAdAAgAEEAcABwAGwAZQAgAEkAbgBjAC4ALAAg
	ADIAMAAyADJYWVogAAAAAAAA9tUAAQAAAADTLFhZWiAAAAAAAACD3wAAPb////+7WFla
	IAAAAAAAAEq/AACxNwAACrlYWVogAAAAAAAAKDgAABELAADIuXBhcmEAAAAAAAMAAAAC
	ZmYAAPKnAAANWQAAE9AAAApbc2YzMgAAAAAAAQxCAAAF3v//8yYAAAeTAAD9kP//+6L/
	//2jAAAD3AAAwG7SHyAhIlokY2xhc3NuYW1lWCRjbGFzc2VzXE5TQ29sb3JTcGFjZaIj
	JFxOU0NvbG9yU3BhY2VYTlNPYmplY3TSHyAmJ1dOU0NvbG9yoiYkAAgAEQAaACQAKQAy
	ADcASQBMAFEAUwBaAGAAawB4AH4AiwCgAKcA0gD8AP4BAAECAQkBDwEZARsBHQEfAzsD
	QANLA1QDYQNkA3EDegN/A4cAAAAAAAACAQAAAAAAAAAoAAAAAAAAAAAAAAAAAAADig==
	</data>
	<key>columnCount</key>
	<integer>120</integer>
	<key>name</key>
	<string>xiang</string>
	<key>rowCount</key>
	<integer>35</integer>
	<key>type</key>
	<string>Window Settings</string>
</dict>
</plist>
```


### tmux
```
Tmux will allow you to split your screen into halves vertically or horizontally.

# install tmux
brew install tmux          # on mac
sudo apt-get install tmux  # on debian

# run it
tmux

# split the screen vertically using this shortcut
CTRL+B %

# split the screen horizontally using this shortcut
CTRL+B "

# switch between screens using this shortcut
CTRL+B o
```

### tmux conf
```
# split panes using | and -
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

# switch panes using Alt-arrow without prefix
# M is Meta, which is usually your Alt key. Remember to go to "Preference" of Mac Terminal to enable "use Option as Meta key"!!
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Enable mouse mode (tmux 2.1 and above. Check: $ tmux -V)
set -g mouse on
  ## mouse mode, select and copy to copyboard
# macOS only
set -g mouse on
bind -n WheelUpPane if-shell -F -t = "#{mouse_any_flag}" "send-keys -M" "if -Ft= '#{pane_in_mode}' 'send-keys -M' 'select-pane -t=; copy-mode -e; send-keys -M'"
bind -n WheelDownPane select-pane -t= \; send-keys -M
bind -n C-WheelUpPane select-pane -t= \; copy-mode -e \; send-keys -M
bind -T copy-mode-vi    C-WheelUpPane   send-keys -X halfpage-up
bind -T copy-mode-vi    C-WheelDownPane send-keys -X halfpage-down
bind -T copy-mode-emacs C-WheelUpPane   send-keys -X halfpage-up
bind -T copy-mode-emacs C-WheelDownPane send-keys -X halfpage-down

# To copy, left click and drag to highlight text in yellow, 
# once you release left click yellow text will disappear and will automatically be available in clibboard
# # Use vim keybindings in copy mode
setw -g mode-keys vi
# Update default binding of `Enter` to also use copy-pipe
unbind -T copy-mode-vi Enter
bind-key -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel "pbcopy"
bind-key -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel "pbcopy"
```
