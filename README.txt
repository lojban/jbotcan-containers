This is the containerized service infrastructure for the static-site
version of jbotcan.  The actual content lives at
https://github.com/La-Lojban/la-lojban.github.io

NB: This is *not* the setup for the PHP/Glaukaba instance of
jbotcan; that was never checked in anywhere, and is currently in a
separate directory in the spjbotcan account on lebna (if that means
nothing to you and you think you need access, bug Robin or gleki).

This is an LBCS instance (see https://github.com/lojban/lbcs/ ),
which is why a bunch of things in here are symlinks off into
apparently empty space; you have to have LBCS installed in
/opt/lbcs/ for them to work.

That's also where the docs on how to like start and stop the service
and so on are.

Deploying A Fresh Instance
==========================

Assuming you have rootless podman working, you should be able to
deploy a copy of jbotcan with something like this:

$ cd /opt
$ git clone git@github.com:lojban/lbcs.git

As the system account you're using for the service:

$ cd ~
$ git clone git@github.com:lojban/jbotcan-containers.git
jbotcan/
$ cd ~/jbotcan/containers/web
$ git clone https://github.com/La-Lojban/la-lojban.github.io data/

$ cd ~/jbotcan
$ ./setup.sh

At that point systemctl commands should work as expected, although
you'll probably want to test with:

$ ./run_container.sh web
