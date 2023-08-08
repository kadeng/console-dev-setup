
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

#### Start / Reenter named pide session

```
pide my_session_name
```

#### Common pide keyboard shortcuts

Always start with **ctrl+a** followed by a command

 * **Detach Session**: **ctrl+a d**
 * **Split window**: **ctrl+a -** and **ctrl+a +**
 * **Paste**: **ctrl+p v**
See **local/tmux.conf** for more

##  How To

### Quit

 ** Without writing: **:q!**
 ** Write file, then quit: **:wq**

### Copy and Paste in VIM

 * Enter visual mode with **v** to mark text
 * **Copy** with **y** (yank)
 * **Delete or Cut** with **d** (delete)
 * **Paste** with **p** (put/paste)

See https://vim.fandom.com/wiki/Cut/copy_and_paste_using_visual_selection

### YouComplete Me Keyboard Shortcuts

Available Commands https://github.com/ycm-core/YouCompleteMe#goto-commands

 * Mapped **:YcmCompleter Goto** to **<CTRL+g>**
 * Go Back: **Ctrl+o** 
 * Go Forward **Ctrl+i**

### Python Debugging with PUDB

[PUDB](https://github.com/inducer/pudb) is a full-featured Python Commandline debugger
that is much more user friendly than pdb

### Attaching to a process

PUDB can be used to debug an already launched python process, using
https://github.com/kadeng/pybugg

#### Running a Pytest under PUDB

Example Commandline: Run a pytest, break into pudb commandline debugger on test enter

```bash
pytest --trace --pdbcls pudb.debugger:Debugger test/inductor/test_fused_attention.py -k test_sdpa_rewriter_9
```


## TO DO

 * **More Plugins**: https://hackingcpp.com/dev/vim_plugins.html
 * **Debugging**: See [Vimspector](https://github.com/puremourning/vimspector)

