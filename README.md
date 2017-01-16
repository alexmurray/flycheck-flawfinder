# Flycheck Flawfinder Checker

[![License GPL 3](https://img.shields.io/badge/license-GPL_3-green.svg)](http://www.gnu.org/licenses/gpl-3.0.txt)
[![MELPA](http://melpa.org/packages/flycheck-flawfinder-badge.svg)](http://melpa.org/#/flycheck-flawfinder)
[![Build Status](https://travis-ci.org/alexmurray/flycheck-flawfinder.svg?branch=master)](https://travis-ci.org/alexmurray/flycheck-flawfinder)

Integrate [flawfinder](http://www.dwheeler.com/flawfinder/)
with [flycheck](http://www.flycheck.org) to automatically check for possible
security weaknesses within your C/C++ code on the fly.

## Installation

### MELPA

The preferred way to install `flycheck-flawfinder` is via
[MELPA](http://melpa.org) - then you can just <kbd>M-x package-install RET
flycheck-flawfinder RET</kbd>

To enable then simply add the following to your init file:

```emacs-lisp
(with-eval-after-load 'flycheck
  (require 'flycheck-flawfinder)
  (flycheck-flawfinder-setup)
  ;; chain after cppcheck since this is the last checker in the upstream
  ;; configuration
  (flycheck-add-next-checker 'c/c++-cppcheck '(warning . flawfinder)))
```

If you do not use `cppcheck` then chain after whichever checker you do use
(ie. clang / gcc / irony etc)

```emacs-lisp
(flycheck-add-next-checker 'c/c++-clang '(warning . flawfinder))
```

### Manual

If you would like to install the package manually, download or clone it and
place within Emacs' `load-path`, then you can require it in your init file like
this:

```emacs-lisp
(require 'flycheck-flawfinder)
(flycheck-flawfinder-setup)
```

NOTE: This will also require the manual installation of `flycheck` if you have
not done so already.

## License

Copyright © 2016 Alex Murray

Distributed under GNU GPL, version 3.
