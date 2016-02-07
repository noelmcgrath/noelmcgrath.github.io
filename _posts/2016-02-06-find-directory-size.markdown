---
layout: post
title:  "Find directory size on Ubuntu"
date:   2016-02-06 12:15:10

---
This post will cover how to find out the size of a directory and also disk space usage.

For this I will be using two unix programs:

* [du] : disk usage
* [df] : disk free

## Finding the size of a directory

The syntax is as follows:

```bash
$du
$du diretorypath
$du [options] diretorypath

```

### Examples
__du__ on its own shows the size of the directory and all sub directories

```bash
root@noel:/vagrant/grafana_with_graphite# du
1       ./grafana
7       ./graphite/graphite
2       ./graphite/nginx
1       ./graphite/statsd
19      ./graphite
102     .

```

Pass  a directory:

```bash
root@noel:/vagrant/grafana_with_graphite# du /vagrant/grafana_with_graphite
1       /vagrant/grafana_with_graphite/grafana
7       /vagrant/grafana_with_graphite/graphite/graphite
2       /vagrant/grafana_with_graphite/graphite/nginx
1       /vagrant/grafana_with_graphite/graphite/statsd
19      /vagrant/grafana_with_graphite/graphite
102     /vagrant/grafana_with_graphite

```

### Some Options

* -h 			: human readable, show output in KB,MB, G
* -s 			: summarize, display total
* -v 			: separate-dirs, report size of each directory seperately, not including subdirectories
* --exclude=PAT 	: skip subdirectories or files matching PAT

```bash
root@noel:/vagrant/grafana_with_graphite# du -h --exclude=statsd
512     ./grafana
7.0K    ./graphite/graphite
1.5K    ./graphite/nginx
18K     ./graphite
102K    .

```

## Display free and used disk space

The syntax is as follows:

```bash
$df
$df diretorypath
$df [options] diretorypath

```

### Examples
__df__ with no options reports the space used and free on all mounted filesystems

```bash
$df
$df -h
$df -h /path

```

[du]:     http://ss64.com/bash/du.html
[df]:     http://ss64.com/bash/df.html