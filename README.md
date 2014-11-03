equal spacing for xmonad
==

layout modifier for xmonad which aims to be at least
a little bit nicer than what's commonly available.

install
--

put `EqualSpacing.hs` somewhere under `~/.xmonad/lib/`
and import it accordingly in your `xmonad.hs`.

for example, `~/.xmonad/lib/XMonad/Layout/EqualSpacing.hs`
can be imported with `import XMonad.Layout.EqualSpacing`.

usage
--

a minimal configuration should be along these lines:

```
import XMonad
import XMonad.Layout.EqualSpacing

main = xmonad $ defaultConfig
    { layoutHook = equalSpacing 36 6 0 1 $ layoutHook defaultConfig }
```

recommendation
--

use with https://github.com/benweitzman/BinarySpacePartition/


i am not smart
--

please note that this spacing is not 'smart', meaning that it does not exhibit
`XMonad.Layout.Spacing.smartSpacing`'s behavior of not adding any spacing when
there's only one window open on the current workspace.
