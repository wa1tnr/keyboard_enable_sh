```
 $  echo; date ; echo ; xinput list ; echo

Wed 14 Sep 13:59:07 UTC 2022

⎡ Virtual core pointer                          id=2    [master pointer  (3)]
⎜   ↳ Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
⎜   ↳ *********************                     id=9    [slave  pointer  (2)]
⎜   ↳ Lenovo ThinkPad Compact USB Keyboard with TrackPoint      id=11   [slave  pointer  (2)]
⎣ Virtual core keyboard                         id=3    [master keyboard (2)]
    ↳ Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    ↳ *********************                     id=6    [slave  keyboard (3)]
    ↳ *********************                     id=7    [slave  keyboard (3)]
    ↳ *********************                     id=8    [slave  keyboard (3)]
    ↳ *********************                     id=10   [slave  keyboard (3)]
    ↳ Lenovo ThinkPad Compact USB Keyboard with TrackPoint      id=12   [slave  keyboard (3)]
    ↳ Lenovo ThinkPad Compact USB Keyboard with TrackPoint      id=13   [slave  keyboard (3)]

 $ 
```
Purpose: to remove the TrackPoint (including its buttons, though
that remains untested) dynamically.  Old method described below
(was not flexible enough to work with, daily).

Asterisks appear for line items not related to this keyboard. ;)

The 'id=nn' fields change dynamically depending on current
state of the system - cannot be hard-coded and did not want
to require learning what they are set to, currently, for
these scripts to succeed.

xinput, post-processed with egrep, sed and cut, seemed to be reliable
enough to work with, so that's the current development level
used (locally, as a one-off solution) for this technique.

Unexplored: why the keyboard section gets two entries in
the xinput list table.


# SESSION log:

```
 $ ls
islenovo  lenovo_disable  lenovo_enable

 $ lenovo_enable ; islenovo
        Device Enabled (173):   1

 $ lenovo_disable ; islenovo
        Device Enabled (173):   0

 $ islenovo
        Device Enabled (173):   0

 $ lenovo_enable

 $ islenovo
        Device Enabled (173):   1

 $ lenovo_disable

 $ islenovo
        Device Enabled (173):   0
```
END.
