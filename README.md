# Case-Insensitive Case-Preserving Overlay FUSE File System
#### cicpoffs

This is a case-insensitive overlay FUSE file system, like [CIOPFS](https://www.brain-dump.org/projects/ciopfs/).

The difference is that:
- This one preserves the original case.
- This one doesn’t have the limitation that “All filenames in the data directory which aren’t all lower case are ignored.”
- This one has been very poorly ported to work with modern (3.0+) versions of FUSE.

## Motivation

Run TESV:Skyrim (linux) with some mods (that are cross-platform in theory, but may have issues deriving from Windows' case-insensitive file system and there's no enforceable convention in modding).

## Preserve inode number

Add `-o use_ino` argument to the commandline otherwise each case combination that points to the same file will get different inodes.

## License

This project uses some modified GPLv2 code in a few files (namely `fuse_launcher_gpl2.cpp`, `ulockmgr.c` and `ulockmgr.h`).

All other files are avaliable as either MIT or GPLv2-or-later, at your discretion.

Due to this reason, the resulting compiled binary will be GPLv2-licensed unless the first file is rewritten or the `ulockmgr` files removed prior to building (hint: they may be provided by your FUSE distribution.)
