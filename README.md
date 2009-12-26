kindlemon
--------

`kindlemon` is a simple linux program to watch for your kindle to be plugged in (via USB).
Once your kindle is inserted and mounted, it'll run the command specified, giving the location
of your kindle as the last argument.

### For example:

	kindlemon ~/scripts/sync-kindle --ask

will run the command `~/scripts/sync-kindle --ask /media/Kindle` when your kindle is inserted
(with the appropriate path, if /media/Kindle is not where your kindle gets mounted)

----

Requires HAL, Dbus and gobject python bindings. These all come standard with ubuntu,
so I'm afraid I don't know what to install if you don't already have them.

