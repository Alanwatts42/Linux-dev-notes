# Lubuntu OS Notes

<br>

## Underlying Framework

The thing about LXDE is that's very bare bones. As such, it doesn't supply a window manager, but it does supply lxsession, which starts everything up when you log in, which would in turn start the window manager, which then starts up everything else. What this means, is that unlike standard ubuntu, where gnome is essentially tied into the underlying OS, lubuntu doesn't have anything analogous to gnome that replaces it. Instead, it has nothing at all. This means that it runs very very fast and very lightweight, with little to no issues even on the shittiest of shitty computers. However, this also means it's a little more difficult to configure everything just the way you want it (not that it's tremendously easy with gnome either though, so there's that). 


to re-bind keyboard commands you can: `cd ~/.config/lxde/lubuntu-rc.xml`
```
      <keybind key="W-a">
      <action name="ShowMenu">
           <menu>lxpanelctl menu</menu>
      </action>
    </keybind>
```


