GETNODE
=======

Getnode downloads, configures, builds and tests the Node.js source code.
It verifies the SHA-1 checksum of the downloaded source code.
Project home page: https://github.com/rsp/getnode

Usage: 

    getnode VERSION
    getnode VERSION PREFIX

It downloads http://nodejs.org/dist/node-vVERSION.tar.gz
and builds for installation in PREFIX or $HOME/local/node by default.
If PREFIX is `v` or `V` it is equivalent to $HOME/local/node-VERSION
(Note: the default prefix may change in later versions)

Examples:

    getnode 0.4.9
    getnode 0.4.9 v
    getnode 0.4.9 ~/node-0.4

ABOUT NODE
----------
[Node.js](http://nodejs.org/) is an event-driven I/O framework for the V8
JavaScript engine developed by [Ryan Dahl](https://github.com/ry).

ABOUT GETNODE
-------------
[Getnode](https://github.com/rsp/getnode) is a shell script that
downloads the source code of a given version of Node, calculates SHA-1
checksum and verifies it against a list of known checksums.  Then it tries to
configure, build and test Node.  Currently it doesn't install but does
everything except `make install`.

Note that it only installs a single version in a single place at a time.
For more advanced tools to manage Node installations see:
[nvm](https://github.com/creationix/nvm) by 
[Tim Caswell](https://github.com/creationix) and
[nave](https://github.com/isaacs/nave) by
[Isaac Z. Schlueter](https://github.com/isaacs).

Both nvm and nave can be used to manage many different Node versions installed
simultaneously on the same system.  Getnode on the other hand can be used to
install one version of Node on many different systems.  So if you need to run
a specific version of Node in a heterogeneous environment of incompatible
systems where binary deployment is not an option then Getnode may be for you.

SECURITY
--------
Getnode uses insecure HTTP connections to download the source code but it then
verifies it against a list of known SHA-1 checksums to make sure that the
downloaded code contains exactly what was expected.

Currently it knows checksums of the following versions of Node:

* 0.1.100 - 0.1.104
* 0.2.0 - 0.2.6
* 0.3.0 - 0.3.8
* 0.4.0 - 0.4.9

If you try to get a version of Node that Getnode doesn't know about then
you have to explicitly accept the computed checksum so you have an option
to verify it manually.

Note that at the time of this writing there is no list of SHA-1 checksums on
the [Node.js website](http://nodejs.org/).  Also, the Node.js website cannot
be accessed using HTTPS.

The checksums in this script were computed manually after downloading the
above versions over HTTP so they are not guaranteed to be "correct".  It is
possible, however unlikely, that I have computed checksums of corrupted or
even malware-infected versions.  What you can tell after a positive
verification is that you have downloaded the same file as I have.  This is
usually enough to avoid local and/or temporary attacks like local DNS
spoofing, cache poisoning or TCP session hijacking, that could potentially
allow the attacker to provide any arbitrary payload as the requested source
code that is downloaded over HTTP.

PREREQUISITES
-------------
Getnode uses cURL or Wget to download the source code of Node; OpenSSL,
sha1sum or shasum to verify it; Tar to extract it and Make to build it.
Building Node requires essential development tools like Make and a C++
compiler, Python version 2.4 or higher and a development version of the SSL
library.  Testing Node requires cURL.

Most of those tools are probably installed by default on any modern system.
For example on a fresh install of Ubuntu Server 10.10 you need to run:

    sudo apt-get install build-essential libssl-dev curl

to have everything needed to build and test Node.

See more info on
[Node's dependencies](https://github.com/ry/node/wiki/Installation).

BUGS
----
If you find any bugs or have any suggestion, please use
[the issue tracking system](https://github.com/rsp/getnode/issues)
or fork [the project on GitHub](https://github.com/rsp/getnode),
commit your changes and send me a pull request.

TODO
----
There is still a lot to do to make this script more useful.

* The default installation prefix will change and more shortcuts will be added.
* There should be an option to build without SSL and maybe without testing.
* There will be an option to automatically `make install`.
* There will be option to automatically give the default answer to any question.
* There might be an option to provide url instead of version for local mirrors.
* There might be an option to update PATH and MANPATH.
* There should be an option to (securely) install NPM
* The name might change

This is an early version, use it at your own risk.

AUTHOR
------
Copyright (c) 2010, 2011 Rafal Pocztarski.

LICENSE
-------
This program is released under the MIT License.  See LICENSE or run
`getnode license` for details.  It comes with ABSOLUTELY NO WARRANTY.
