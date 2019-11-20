NeoAtlantis Safe Sync Backup Tool
=================================

This is a simple tool for backing up NeoAtlantis data. It is basically a caller
to `rsync`, but includes complex checkings to ensure reliability.

Features and limits:

* When syncing between file systems, check that source and destination path
  exists before calling `rsync`. This ensures situations, when cron task
  scheduling and/or removable media is used, that sync is called only when
  both are accessible.
    * Source and destination are determined with special files,
      `.srsync-src` or `.srsync-dest`. Only when that file exists can sync
      begin.
* Proper dealing with path specification avoiding confusion. There is no such
  feature as mapping one folder `/source` onto `/backup/source`. Both source
  and destination must be folders, and are equivalent. If specified `/source`
  <=> `/backup`, then both folders must exist, thus `/source/file1` =>
  `/backup/file2`.
