# Command line tools, vim and various

## Split it in to categories!

- [Mouseless.dev](https://themouseless.dev)
- [Nix Flakes](https://www.tweag.io/blog/2020-05-25-flakes/)
- [Carbon.sh](https://carbon.now.sh/)
- [Fish Shell](https://fishshell.com/docs/current/index.html#)
- [SKHD configuration](https://gist.github.com/zmre/b5e23a6ac1be92ce4f90390940d7f03a)
- [NeoVim is Overpowering](https://crispgm.com/page/neovim-is-overpowering.html)
- [Explain Shell](https://explainshell.com/)
- [Terminals Are Sexy](https://terminalsare.sexy/)
- [Terminal.Sexy](https://terminal.sexy/)
- [Beautiful Linux Environment](https://dev.to/deepu105/my-beautiful-linux-development-environment-2afc)
- [Box Drawing Characters](https://en.wikipedia.org/wiki/Box-drawing_character)
- [Learn Vim](https://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/)
- [VSCode Theme Creator](https://themes.vscode.one/your-themes/)
- [ZSH Autocomplete](https://mrigank11.github.io/2018/03/zsh-auto-completion/)
- [ZSH Autocomplete 2](https://github.com/zsh-users/zsh-completions/blob/master/zsh-completions-howto.org)
- [How does NixOs work](https://christine.website/blog/nixos-desktop-flow-2020-04-25)
- [Programming Fonts Tester](http://app.programmingfonts.org/)
- [CharMap](http://mathew-kurian.github.io/CharacterMap/)
- [How to learn Emacs](http://david.rothlis.net/emacs/howtolearn.html)
- [Vim After 15 Years](https://statico.github.io/vim3.html)
- [Modulinos in Bash](https://blog.dnmfarrell.com/post/modulinos-in-bash/)
- [Bash Pitfalls](https://mywiki.wooledge.org/BashPitfalls)
- [Hurl](https://hurl.dev/)
- [LookAtMe](https://github.com/d0c-s4vage/lookatme/issues)
- [Ruby for ebook](https://nts.strzibny.name/ruby-for-ebook-publishing/)
- [Zsh Profiling](https://htr3n.github.io/2018/07/faster-zsh/)
- [Bash](https://mywiki.wooledge.org/BashFAQ/066)
- [Ascii Doctor](https://asciidoctor.org/)
- [Rclone](https://rclone.org/docs/)
- [GraphViz](https://graphviz.org/)
- [getopts](https://www.golinuxcloud.com/bash-getopts)

## Keybindings for terminal
Open the iTerm preferences `⌘+`, and navigate to the Profiles tab (the Keys tab can be used, but adding keybinding to your profile allows you to save your profile and sync it to multiple computers) and keys sub-tab and enter the following:

### Delete all characters left of the cursor
`⌘+←Delete` Send Hex Codes:
  * `0x18 0x7f` – Less compatible, doesn't work in node and won't work in zsh by default, see below to fix zsh (bash/irb/pry should be fine), performs desired functionality when it does work.
  * `0x15` – More compatible, but typical functionality is to delete the entire line rather than just the characters to the left of the cursor.

### Delete all characters right of the cursor
`⌘+fn+←Delete` or `⌘+Delete→` Send Hex Codes:
  * `0x0b`

### Delete one word to left of cursor
`⌥+←Delete` Send Hex Codes:
  * `0x01b 0x08`

### Delete one word to right of cursor
`⌥+fn←Delete` or `⌥+Delete→` Send Hex Codes: 
  * `0x01b 0x64`

### Move cursor to the front of line
`⌘+←` Send Hex Codes:
  * `0x01`

### Move cursor to the end of line
`⌘+→` Send Hex Codes:
  * `0x05`

### Move cursor one word left
`⌥+←` Send Hex Codes:
  * `0x1b 0x62`

### Move cursor one word right
`⌥+→` Send Hex Codes:
  * `0x1b 0x66`

### Undo
`⌘+z` Send Hex Codes:
  * `0x1f`

### Redo
Typically not bound in bash, zsh or readline, so we can set it to a unused hexcode which we can then fix in zsh.

`⇧+⌘+Z` or `⌘+y` Send Hex Codes:
  * `0x18 0x1f`

_Stolen from: http://stackoverflow.com/questions/6205157/iterm2-how-to-get-jump-to-beginning-end-of-line-in-bash-shell#answer-29403520_
