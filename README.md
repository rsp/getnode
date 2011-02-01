GETNODE
=======
Copyright (c) 2010, 2011 Rafal Pocztarski.
This program comes with ABSOLUTELY NO WARRANTY.
You may redistribute it under certain conditions.
See LICENSE or run `getnode license` for details.

Getnode downloads, configures, builds and tests the Node.js source code.
Project home page: [https://github.com/rsp/getnode]

Usage: 
       getnode VERSION
       getnode VERSION PREFIX

Downloads: http://nodejs.org/dist/node-vVERSION.tar.gz
and builds for installation in PREFIX or /opt/node by default.
If PREFIX is `v` or `V` it is equivalent to /opt/node-VERSION
(Note: the default prefix will change in later versions)

Examples:
          getnode 0.2.6
          getnode 0.2.6 v
          getnode 0.2.6 /usr/local

ABOUT NODE
----------
[Node.js](http://nodejs.org/) is an event-driven I/O framework for the V8
JavaScript engine developed by [Ryan Dahl](https://github.com/ry).

ABOUT GETNODE
-------------
[Getnode](https://github.com/rsp/getnode) is a shell script written by
[Rafał Pocztarski](https://github.com/rsp) to speed up Node deployments.

It downloads the source code of a given version of Node, calculates SHA-1
checksum and asks for approval.  Then it tries to configure, build and test
Node.  Currently it doesn't install but does everything except `make install`.

Note that it only installs a single version in a single place at a time.
For more advanced tools to manage Node installations see:
[nvm](https://github.com/creationix/nvm) by 
[Tim Caswell](https://github.com/creationix) and
[nave](https://github.com/isaacs/nave) by
[Isaac Z. Schlueter](https://github.com/isaacs).

PREREQUISITES
-------------
Getnode uses Wget to download the source code of Node, Tar to extract it and
Make to build it.  Building Node requires essential development tools like
Make and a C++ compiler, Python version 2.4 or higher and a development
version of the SSL library.  Testing Node requires cURL.

Most of those tools are probably installed by default on any modern system.
For example on a fresh install of Ubuntu Server 10.10 you need to run:

    sudo apt-get install build-essential libssl-dev curl

to have everything needed to build and test Node.

See more info on
[Node's dependencies](https://github.com/ry/node/wiki/Installation).

TODO
----
There is still a lot to do to make this script more useful.

* The default installation prefix will change and more shortcuts will be added.
* There should be an option to build without SSL and maybe without testing.
* There will be an option to automatically `make install`.
* There will be option to automatically answer Yes to any question.
* There will be a way to supply the correct SHA-1 checksum to verify against.

This is an early version, use it at your own risk.
