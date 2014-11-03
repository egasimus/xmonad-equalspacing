Equal spacing for xmonad
==

Layout modifier for xmonad which aims to be at least
a little bit nicer than what's commonly available.

Rationale and features
--

The humble author was endlessly annoyed by having the space
between two windows be twice as wide as the space between a
window and the screen edge. Therefore, the simple technique
of shrinking the windows from one corner and the screen from
the opposite one was implemented.

The humble author was also endlessly annoyed
by not being able to change spacing on the fly.
therefore, a message was added to control that.

Having eventually constructed this module, the humble author
was then endlessly annoyed by how big his preferred borders
ended up being. Therefore, borders were made to automatically
shrink with each subsequent window.

Installation
--

Put `EqualSpacing.hs` somewhere under `~/.xmonad/lib/`
and import it accordingly in your `xmonad.hs`.

For example, `~/.xmonad/lib/XMonad/Layout/EqualSpacing.hs`
can be imported with `import XMonad.Layout.EqualSpacing`.

Usage
--

A minimal configuration should be along these lines:

```
import XMonad
import XMonad.Layout.EqualSpacing

main = xmonad $ defaultConfig
    { layoutHook = equalSpacing 36 6 0 1 $ layoutHook defaultConfig }
```


Recommendation
--

Use with https://github.com/benweitzman/BinarySpacePartition/


I am not smart
--

Please note that this spacing is not 'smart', meaning that it does not exhibit
`XMonad.Layout.Spacing.smartSpacing`'s behavior of not adding any spacing when
there's only one window open on the current workspace.
