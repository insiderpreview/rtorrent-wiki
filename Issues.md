# Known Issues

## Major issues

1. [rTorrent reading 4x more data than sending](https://github.com/rakshasa/rtorrent/issues/443)
2. [Sorting/filtering 'started' and 'stopped' views causes announces to fire with v0.9.6]( https://github.com/rakshasa/rtorrent/issues/449) (fixed in current master branches)

## Using the 'ntfs' File System

`rtorrent` has issues with **ntfs** partitions.
It's reported that `rtorrent` freezes when downloading on partition formatted with ntfs filesystem.[1]

Also, if the files are bigger than 4GB, data gets corrupted.[2]


***

1. [Constant freezes when downloading torrent to NTFS partition](http://askubuntu.com/questions/399775/constant-freezes-when-downloading-torrent-to-ntfs-partition)
2. [Error writing to NTFS drive](https://github.com/rakshasa/rtorrent/issues/194)
3. [ntfs-3g: Data corruption when using rtorrent](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=743734)
