vim: fdl=3:
$onGH/harriott-zenburn-emacs/README.md

# zenburn-theme for Emacs

[![License GPL 3][badge-license]](http://www.gnu.org/licenses/gpl-3.0.txt)

## About
My fork of the excellent [zenburn-emacs](https://github.com/bbatsov/zenburn-emacs), created just so that I can tweak basic coloring `fringe` to be dimmer.

### how
The original theme uses `zenburn-fg`
```
    ...
;;;;; basic coloring
    ...
    (fringe ((t (:foreground ,zenburn-fg :background ,zenburn-bg+1))))
    ...
;;; Color Palette
    ...
    ("zenburn-fg"       . "#DCDCCC")
    ...
    ("zenburn-bg-1"     . "#2B2B2B")
    ...
```
I switch to `zenburn-bg-1`, which gives less obtrusive fringe marks.

![unobtrusive screenshot](screenshots/psilocybin.jpg)

### install
I symlink this repository to `~/.emacs.d/harriott-zenburn-emacs` (in my [$OSAB/bs-symlinks/jo-2-whenWM-0.sh](https://github.com/harriott/OS-ArchBuilds/blob/master/bs-symlinks/jo-2-whenWM-0.sh)) then in my [$misc/CP/Emacs/init.el](https://github.com/harriott/misc/blob/master/Emacs/init.el) I have:
```lisp
; (use-package zenburn-theme)  ; gets the original
(require 'zenburn-theme)  ; gets this version
  (load-theme 'zenburn t)
```
I noticed that whenever I tweak my copy of the theme Emacs warns me that it considers "The local variables list in zenburn-theme.el contains values that may not be safe (*)." My workaround is to briefly switch back to the original theme.

## merging from bbatsov upstream

    git remote add upstream git@github.com:bbatsov/zenburn-emacs

    git remote -v                                # check remote locations
    git fetch upstream                           # grab the changed upstream
    git merge upstream/master -m 'merge message' # merges in the changes
    rg HEAD                                      # ripgrep for any conflicts
    in vim: /^<<<<<<< HEAD$\|^=======$\|^>>>>>>> upstream/master$
    gic '2 commits behind'
    git merge --abort                            # undo the merge

## License
Copyright © 2010-2022 Bozhidar Batsov and
[contributors](https://github.com/bbatsov/zenburn-emacs/contributors).

Distributed under the GNU General Public License, version 3

[badge-license]: https://img.shields.io/badge/license-GPL_3-green.svg
