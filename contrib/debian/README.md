
Debian
====================
This directory contains files used to package sombed/sombe-qt
for Debian-based Linux systems. If you compile sombed/sombe-qt yourself, there are some useful files here.

## sombe: URI support ##


sombe-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install sombe-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your sombeqt binary to `/usr/bin`
and the `../../share/pixmaps/sombe128.png` to `/usr/share/pixmaps`

sombe-qt.protocol (KDE)

