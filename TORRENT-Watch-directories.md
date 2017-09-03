Watch Directories
=================

Introduction
------------

To load torrent files dropped into special folders (by direct download, DropBox, ``scp``, ``sshfs``, and so on),
you can extend your configuration with scheduled checks trying to load new files from these folders.

Watch Directory Schedules
-------------------------

These examples load items from different directories, in started state or idle.
The 3rd example shows how to set a non-default download path, using a post-load command.

```ini
schedule2 = watch_directory_foo, 20, 10, "load.start_verbose=~/watch_foo/*.torrent"
schedule2 = watch_directory_bar, 21, 10, "load.verbose=~/watch_bar/*.torrent"
schedule2 = watch_directory_baz, 22, 10, "load.verbose=~/watch_baz/*.torrent,d.directory.set=~/baz/"
```

The used *verbose* load commands log any problems to the console.
Be aware though that half-written files can lead to spurious warnings,
especially if your schedules have an interval like only 1 second.
Use the ``load.start`` or ``load.normal`` commands instead 
if you do *not* want any diagnostics.

Also note that the start times are incremental, to spread the load caused by scanning the watch directories.

Dynamic Start Behaviour
-----------------------

Sometimes you want to easily change whether an item loaded by a watch is started immediately or not. This is especially useful when combined with automatic downloaders like `FlexGet` or `autodl-irssi`.
Usually, newly added items are started immediately – that is the whole point of automation.

In some cases though, you might want to disable that and delay downloading until later.
Testing configuration changes is a typical reason, because an innocent mistake could
swamp you with lots of downloads. If they stay dormant at first, that is easily fixed.

See [Watches With Dynamic Start Behaviour](https://pyrocore.readthedocs.io/en/latest/usage.html#watch-start) for how to set this up.


Tied Files
----------

```ini
# Either use this…
schedule2 = tied_directory, 10, 10, start_tied=
schedule2 = untied_directory, 10, 10, stop_untied=

# OR one of these, the combination does not make sense
schedule2 = untied_directory, 10, 10, close_untied=
schedule2 = untied_directory, 10, 10, remove_untied=
```

When a download is created the torrent file's original path is associated with the download. When the commands '*_untied' are called the respective actions (stop, close, remove) are called for downloads if their original torrent file is not found.

The reverse happens if 'start_tied' is called.

Inotify
-------

On Linux and using v0.9.7+, you may use inotify to watch a directory, and the provided command is called with the the full path of new files as the first argument. Use `method.insert` to define more complex multi-command inotify handlers, or when you want to pass additional parameters to a handler command.

```ini
directory.watch.added = "~/Download/watch/", load.start
```

