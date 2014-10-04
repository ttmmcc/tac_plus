# TACACS+ Daemon (tac_plus)

`[tac_plus][1]` is a daemon from [Shrubbery Networks][2] that provides
[AAA][3] services.

The source is hosted here in the event that it is ever unavailable from
the developer.  It is also made available here for the purpose of
cloning to local [git][4] infrastructure, which is then used as the
source to build and update local TACACS+ infrastructure.

## Requirements

* Linux
* Build Environment
* Packages:
  * tcp-wrappers(-dev)
  * bison
  * flex
  * pam(-dev)

## Features

* IPv4
* IPv6
* PAM
  * LDAP
  * Google Authenticator
  * Anything Else PAM Supports
* Logging to Syslog
* Receiving Accounting Information
* Authorization Control

## Installing

```bash
sudo adduser --home=/opt/tac_plus tac-plus
git clone https://github.com/supertylerc/tac_plus
cd tac_plus/src
./configure --prefix=/opt/tac_plus --with-userid=tac-plus --with-groupid=tac-plus
make && sudo make install
sudo mkdir /opt/tac_plus/etc
sudo cp ../samples/tac_plus.conf /opt/tac_plus/etc/tac_plus.conf
sudo chown -R tac-plus:tac-plus /opt/tac_plus
sudo cp ../samples/tac_plus.upstart /opt/init/tac_plus.conf
```

## Configuring

To configure `tac_plus`, you need to edit
`/opt/tac_plus/etc/tac_plus.conf` (or whatever configuration file in
whatever path you chose).  You should follow the guides on the [official
tac_plus website][1] as they will be more complete than what is offered
here.  Additionally, you can see the series on TACAC+ that I wrote
[here][5].

## Running

```bash
sudo service tac_plus start
```

## Credits

* [Shrubbery Networks][2], TACACS+ Daemon
* [Tyler Christiansen][6], Git Repo, Instructions, Upstart Job, Sample
  Configuration

[1]: http://shrubbery.net/tac_plus/ "TACACS+ Daemon"
[2]: http://shrubbery.net/ "Shrubbery Networks, Inc"
[3]: http://en.wikipedia.org/wiki/AAA_protocol "Authentication,
Authorization, and Account"
[4]: http://git-scm.org/ "Git Distributed Version Control System"
[5]: http://oss-stack.io/blog/categories/tacacs/ "OSS Stack - TACACS+
Category"
