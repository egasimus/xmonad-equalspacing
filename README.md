Equal spacing for xmonad
==

Layout modifier for [xmonad](http://xmonad.org/) which aims to
be at least a little bit nicer than what's commonly available.

Rationale and features
--

The humble author was endlessly annoyed by having the space
between two windows be twice as wide as the space between a
window and the screen edge. Therefore, the simple technique
of shrinking the windows from one corner and the screen from
the opposite one was implemented, providing **pleasantly equal
spacing.**

The humble author was also endlessly annoyed by not being able
to **change spacing on the fly.** Therefore, a `Message` was
added to control that via hotkeys.

Having eventually constructed this module, the humble author
was then endlessly annoyed by how big his preferred borders
ended up being. Therefore, he made his **borders automatically
shrink based on number of windows**.

Installation
--

Put `EqualSpacing.hs` somewhere under `~/.xmonad/lib/`
and then import it accordingly in your `xmonad.hs`.

For example, `~/.xmonad/lib/XMonad/Layout/EqualSpacing.hs`
can be imported with `import XMonad.Layout.EqualSpacing`.

Usage
--

A minimal configuration should be along these lines:

```
import XMonad
import XMonad.Util.EZConfig(additionalKeysP)

import XMonad.Layout.EqualSpacing

main = xmonad $ defaultConfig
    { layoutHook = equalSpacing 36 6 0 1 $ layoutHook defaultConfig
    } `additionalKeysP` [ ("M-[", sendMessage $ LessSpacing)
                        , ("M-]", sendMessage $ MoreSpacing) ]
```

Of course the humble author hasn't bothered to test that,
but you are a smart person and should be able to figure it out, right?

Reference
---

**equalSpacing *gap* *add* *mult* *min***
* *gap* -- the spacing from one window to the next, or, indeed, from
  the screen edge to the windows.
* *add* -- number of pixels subtracted from border for each new window
* *mult* -- not implemented yet because I haven't figured out yet how
  exponentiation works in Haskell.
* *min* -- absolute minimum border

**EqualSpacingMsg = MoreSpacing | LessSpacing**
Increments/decrements border size by a pixel. TODO parameterized message.

Recommendation
--

Use this with https://github.com/benweitzman/BinarySpacePartition/ !


I am not smart
--

Please note that this spacing is not 'smart', meaning that it does not exhibit `XMonad.Layout.Spacing.smartSpacing`'s behavior of not adding any spacing when there's only one window open on the current workspace.
