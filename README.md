# haskell-mode, @neongreen's fork

This is a quick-and-dirty fork of haskell-mode. It does two things:

1. Disable showing info for things at point (like types, syntax references, etc). This is done to deal with the incredibly annoying issue https://github.com/haskell/haskell-mode/issues/1498 (when the “restart session” prompt appears whenever you try to edit anything in a broken project).

2. Disable gathering types (the [“Collecting type info for N module(s)”](https://github.com/haskell/haskell-mode/issues/1436) message), because otherwise working with large projects becomes hard (gathering types for 300 modules takes 5–15 seconds).

## Installation

Remove haskell-mode:

  * `M-x package-list-packages`
  
  * Mark `haskell-mode` (and also `intero` and `ghc` if you have them) with `d`.
  
  * Press `x` to do uninstallation.

Clone this repository and build it:

```
$ git clone https://github.com/neongreen/haskell-mode-neongreen
$ cd haskell-mode-neongreen && make
```

Enable it in Emacs by adding the following to `init.el` (replace `~/code` with wherever you cloned the repository):

```
(add-to-list 'load-path "~/code/haskell-mode-neongreen/")
(require 'haskell-mode-autoloads)
(add-to-list 'Info-default-directory-list "~/code/haskell-mode-neongreen/")
```

If you had `(require 'haskell)` in your `init.el`, comment it out.

Restart Emacs.

## Troubleshooting

> I'm getting `error: Required feature 'haskell-mode-autoloads' was not provided`

You probably forgot to do `make`.
