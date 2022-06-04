# Keym
This is a fork of cwkx's keym adding:
* vi movement keys
* better scrolling
* better keymappings
* vi key map to arrow key toggle

This is a tool for controlling the mouse smoothly with the keyboard. It supports
five speed settings with fast scrolling and responsive updates. A selection of
keys get unmapped while the application is running. This lets you still use other
keys not used by the tool, rather than naively grabbing the entire keyboard.
However, if you still want the application to fully grab all the keyboard you can
press ``Right Control`` to do this.

## Installation
Install either from the makefile or compile with gcc:

```gcc keym.c -lX11 -lXtst -o keym```

## Left-handed usage
Simply execute ``keym`` (e.g. use xbindkeys if you want to launch it via a hotkey,
or you can launch it from your window manager). It will grab the keyboard focus
and you can use ``HJKL`` to then move the cursor, ``M`` to left click, ``N`` to
right click, ``B`` to middle click, ``U/D`` to scroll. I found discrete speed settings
more efficient/predictable than acceleration. I didn't want to add a config.h, as its
easier to modify all the conditionals in the code, e.g. if you wanted to make a better
right-handed version. Exit with ``X``.

Hold ``F`` to move very slowly, ``G`` to move reasonably slowly, ``A`` to move quickly,
and hold ``S`` to move extremely quickly. ``E`` for the browser back button and ``O``
for the browser forward button. Exit with ``M`` or ``X``. Please let me know if you
find any bugs or have any usability suggestions.

## Help wanted / known issue
Some applications, like ``code``, do their own input handling - so typing still happens
even though the keys have been unmapped. While you can press ``Right Control``, calling
``XGrabKeyboard`` to take the focus away, this cause issues in other applications, e.g.
gtk2 menus in ``pcmanfm`` wont register, as the focus will be lost. Solving this in a
stable way, while working for all applications and allowing you to use other keys while
``keym`` is used, is non-trivial. Any suggestions/improvement relating to this challenge,
please let me know.
