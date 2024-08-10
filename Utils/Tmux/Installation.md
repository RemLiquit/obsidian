
# Installation
Install Tmux

```
sudo apt-get install tmux
```
# Plugins
```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Create ~/.tmux.conf and paste 
# Principal List of plugins
```
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'arcticicestudio/nord-tmux'
set -g @plugin 'tmux-plugins/tmux-prefix-highlight'

run '~/.tmux/plugins/tpm/tpm'
```
# Other examples:
set -g @plugin 'github_username/plugin_name'
set -g @plugin 'git@github.com:user/plugin'
set -g @plugin 'git@bitbucket.com:user/plugin'
set -g @continuum-restore 'on'
# Initialize TMUX plugin manager
Open Tmux and in other terminal Reload Tmux

```
tmux source ~/.tmux.conf
```

In Tmux terminal use ctrl+b and shift+i