Русская раскладки, совместимая с Programmer Dvorak
===========================================================================

Для английского языка все это точная копия [Programmer
Dvorak](http://www.kaufmann.no/roland/dvorak/).  Для русского языка
доступны все символы обычной windows-раскладки, но в максимально
совместимом с Programmer Dvorak виде.

![Keyboard Layout](dvp.png)

Установка
=========

Emacs
-----

    (load-file "~/path/to/russian-computer-d.el")
    (setq default-input-method "russian-computer-d")

xorg
----

Пример для debian-based дистрибутивов, гарантирующий что обновлением
раскладка не перезапишется.

    # dpkg-divert --divert /usr/share/X11/xkb/symbols/ru.orig \
                  --rename /usr/share/X11/xkb/symbols/ru
    # cp /usr/share/X11/xkb/symbols/ru.orig /usr/share/X11/xkb/symbols/ru
    # cat /path/to/ru-xkb.add >> /usr/share/X11/xkb/symbols/ru.orig

Потом выполнить что-то вроде 

    $ setxkbmap us,ru dvp,dvp grp:menu_toggle,grp:sclk_toggle,ctrl:nocaps,altwin:super_win
    
или в xorg.conf дописать:

    Section "InputClass"
            Identifier "Keyboard"
            MatchIsKeyboard "True"
            Option          "XkbRules"      "xorg"
            Option          "XkbModel"      "pc105"
            Option          "XkbLayout"     "us,ru"
            Option          "XkbVariant"    "dvp,dvp"
            Option          "XkbOptions"    "grp:menu_toggle,ctrl:nocaps,altwin:super_win,grp:sclk_toggle"
    EndSection


