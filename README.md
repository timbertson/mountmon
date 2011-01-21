mountmon
--------

`mountmon` is a simple linux program to watch for your storage device to be plugged in
(via USB). It runs in the background, monitoring USB events.

Once an interesting device is inserted and mounted, it'll run the command specified,
giving the location of your device as the last argument.

Config is all loaded from the file `~/.config/mountmon/mountmon_config.py`. This file
must declare `mapping`, a dictionary of matching functions to action functions.

A matching function receives a device, and returns `True` or `False`.
An action function receives a path and returns a list of command-line arguments to run.

### For example:

	$ cat ~/.config/mountmon/mountmon_config.py
	import os
	HOME = os.environ['HOME']

	def is_kindle(device):
		return 'kindle' == str(device['info.product']).lower()

	mapping = {
		is_kindle:  lambda path: [HOME + "/bin/pagefeed-kindle-sync", "--ask", path]),
	}

will run the command `~/bin/pagefeed-kindle-sync --ask /path/to/kindle` each time your
kindle is inserted.

----

[indicate-task](http://gfxmonk.net/dist/0install/indicate-task.xml) is super useful for
easily showing a GUI background tasks, I use it for all my mountmon actions.

----

Requires HAL, Dbus and gobject python bindings. These all come standard with ubuntu,
so I'm afraid I don't know what to install if you don't already have them.

