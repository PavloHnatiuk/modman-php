modman-php
==========

PHP implementation for modman, to use it on every operating system with PHP support (also Windows).

Currently implemented:
 - init (creates .modman directory)
 - link <target> (creates symlinks)
 - deploy <module> (update symlinks)
 - deploy-all (updates all modules)
 - repair (repairs all symlinks)
 - clean (removes all dead symlinks)

 --force is available for link, deploy and deploy-all, if not set script aborts when conflicts are found

Usage examples:

    php modman.php init
    php modman.php link ..\B2BProfessional
    php modman.php deploy B2BProfessional

Currently supported in modman files:
 - symlinks
 - @import
 - @shell

For Windows users there's also a batch file available, so instead of typing php and directory to modman.php you could just use modman.bat everywhere if you add it to your %PATH%-variable:

    modman link c:\B2BProfessional


VCS integration is postponed, because there are great clients out there, so we don't use it in modman anyway.


Started at Magento Hackathon in Zürich 2013-03-09


Influenced by the original modman at https://github.com/colinmollenhour/modman/


init
====

Creates the .modman directory, which is used for all other operations.

    cd $PROJECT
    php modman.php init

link
====

Creates symlink from a modman file

    cd $PROJOECT
    php modman.php link /path/to/myMageModule

Optional parameter --force to automatically remove conflicted files

deploy
======

Updates the symlinks of a linked module

    cd $PROJECT
    php modman.php deploy myMageModule

Optional parameter --force to automatically remove conflicted files

deploy-all
==========

Updates all symlinks of linked modules

    cd $PROJECT
    php modman.php deploy-all

Optional parameter --force to automatically remove conflicted files

repair
======

Repairs all symlinks of all linked modules

    cd $PROJECT
    php modman.php repair

clean
=====

Scans directory for dead symlinks and deletes them. Useful if a module was deleted and not removed in the project

    cd $PROJECT
    php modman.php clean

remove
======

Removes links of a project

    cd $PROJECT
    php modman.php remove myMageModule

Optional parameter --force to automatically remove conflicted files
