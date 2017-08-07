# Jump tree #

jump-tree is an undo-tree like jumping implementation, so that we can jump back and forth in a tree way like undo-tree. It's inspired by and a combination of undo-tree and jumplist.

![demo](https://github.com/yangwen0228/jump-tree/blob/master/jump-tree.gif)

## Installation
You can install  manually from github;
`git clone https://github.com/yangwen0228/jump-tree.git`

Then add this to your init:
`(require 'jump-tree)`

## Usage
Just call `M-x global-jump-tree-mode` and then use `M-,` to jump previous, `M-.` to jump next and `C-x j` to view the jump tree visualizer.
The record of the jump node is decided by the `jump-tree-pos-list-hook-commands` variable. The default value is as follows:
```
'(beginning-of-buffer
  end-of-buffer backward-up-list
  beginning-of-defun end-of-defun
  unimacs-move-beginning-of-line unimacs-move-end-of-line
  unimacs-move-beginning-of-window unimacs-move-end-of-window
  helm-swoop helm-imenu helm-find-files helm-multi-files
  helm-projectile-switch-project helm-projectile-find-file
  helm-gtags-find-pattern helm-gtags-find-tag-adapter
  helm-gtags-find-rtag-adapter helm-ag-select-directory
  find-function find-variable
  mark-defun mark-whole-buffer
  avy-goto-char avy-goto-char-2
  ensime-edit-definition
  ensime-edit-definition-with-fallback
  isearch-forward)
```

You can change it to other hook commands.

## Thanks to
Toby Cubitt's [undo-tree](http://www.dr-qubit.org/undo-tree/undo-tree.el)
ganmacs's [jumplist](https://github.com/ganmacs/jumplist)

## Todo
- [ ] When the records' buffers get closed, the position markers become invalid. Clear the records? Or use a file to save the last point states, and restore the states?
- [ ] Last position is sometimes not reachable.

