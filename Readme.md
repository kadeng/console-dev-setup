
### My Pytorch Development Console / VIM / TMUX Config

Useful for Pytorch Development

### VIM

#### Setup

1. Check out this repo and put things into place


```
mkdir ~/install
cd install
git clone https://github.com/kadeng/console-dev-setup
cp console-dev-setup/.vimrc ~/.vimrc
mkdir -p ~/.local
cp -rav console-dev-setup/local ~/local
chmod +x ~/.local/bin/*
```

Make sure that $HOME/.local/bin is on your PATH

2. Install Vundle and install plugins

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
vim +PluginInstall +qall
```

This should have installed [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe) 

We still need to compile that, and we want **clangd completer** support
```
cd ~/.vim/bundle/YouCompleteMe
python3 install.py --clangd-completer
```

### pide command

pide is a simple script which uses tmux to create a named IDE-like session with mouse navigation
tmux key is mapped to ctrl+a to make it behave similar to screen (my personal preference)

#### start pide session

```
pide my_session_name
```

See **local/tmux.conf** for more

##  How To

### Copy and Paste in VIM

See https://vim.fandom.com/wiki/Cut/copy_and_paste_using_visual_selection

### YouComplete Me Keyboard Shortcuts

Available Commands https://github.com/ycm-core/YouCompleteMe#goto-commands

 * Mapped **:YcmCompleter Goto** to **<CTRL+g>**
