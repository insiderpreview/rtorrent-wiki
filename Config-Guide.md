# rTorrent Configuration Guide
**Contents**

 * [Basic Configuration](#basic-configuration)
 * [Advanced Use-Cases](#advanced-use-cases)
 * [Advanced Topics](#advanced-topics)
 * [Complete solutions](#complete-solutions)


## Basic Configuration 

See [[rTorrent Configuration Template|CONFIG-Template]] for a modern rTorrent configuration that provides a good starting point. The following sub-sections describe some of the essential settings you must have in a common configuration like that, plus some advanced settings you can add, depending on what your needs are.

Additionally, the [[Common Tasks in rTorrent]] page lists many useful things to have in a configuration, and also some tips regarding maintenance tasks.

### Using a Session Directory

Adding the `session.path.set` command will enable session management, which means the torrent files and status information for all open downloads will be stored in this directory. When restarting rTorrent all torrents previously loaded will be restored. Only one instance of rTorrent should be used with each session directory, though at the moment no locking is done. An empty string will disable the session handling.

:white_check_mark: This is already contained in [[CONFIG-Template]].


### Watching a Directory for Torrents

The client may be configured to check a directory for new torrents and load them. Torrents loaded in this manner will be *tied* to the file's path. This means when the torrent file is deleted the torrent may be stopped (requires additional configuration), and when the item is removed the torrent file is, too. Note that you can untie an item by using the `U` key (which will delete the tied file), and using `^K` also implictly unties an item.

See also the [Watch Directories](https://github.com/rakshasa/rtorrent/wiki/TORRENT-Watch-directories) page.

:white_check_mark: This is already contained in [[CONFIG-Template]].


## Advanced Use-Cases

These pages and the following sections cover information that you don't need when you start out (i.e. read at your leisure), or only apply to a small number of users.

 * [Ratio Handling](https://github.com/rakshasa/rtorrent/wiki/RTorrentRatioHandling)
 * [Tor Proxying](https://github.com/rakshasa/rtorrent/wiki/Tor-based-Proxying-Guide)
 * [Using DHT](https://github.com/rakshasa/rtorrent/wiki/Using-DHT)
 * [Using XMLRPC with rTorrent](https://github.com/rakshasa/rtorrent/wiki/RPC-Setup-XMLRPC)
 * [Performance Tuning](https://github.com/rakshasa/rtorrent/wiki/Performance-Tuning)
 * [Favoring one group of torrents over the rest of them](https://github.com/rakshasa/rtorrent/wiki/Favoring-group-of-torrents)
 * [[Auto-Scraping]]

## Advanced Topics

 * [Logging](https://github.com/rakshasa/rtorrent/wiki/LOG-Logging)
 * [Migration to the 0.9.x command syntax](https://github.com/rakshasa/rtorrent/wiki/RPC-Migration-0.9)
 * [Choke Groups](https://github.com/rakshasa/rtorrent/wiki/Choke-Groups)
 * [IP filtering](https://github.com/rakshasa/rtorrent/wiki/IP-filtering)


## Complete solutions

* [pimp-my-box](https://github.com/pyroscope/pimp-my-box)
* [Ultimate Torrent Setup](https://github.com/xombiemp/ultimate-torrent-setup/wiki)
* [Automated rTorrent-PS configuration](https://github.com/chros73/rtorrent-ps_setup)
