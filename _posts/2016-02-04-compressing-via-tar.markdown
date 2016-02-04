---
layout: post
title:  "Compressing via tar"
date:   2016-02-04 15:31:10

---
The following outlines how to compress(archive) a whole directory in linux, and also how to decompress the tar file.
I will be using the [tar command]

The following command tars a directory

```bash
tar -zcvf tarfile-name.tar.gz directory-name

```

Where

* -z : Compress archive using gzip program
* -c : Create the archive
* -v : Verbose, display progress
* -f : Archive file name

For example if you have a directory named mydirectory in home the following will create a tar named mydirectory.tar.gz:

```bash
tar -zcvf mydirectory.tar.gz /home/mydirectory

```

To uncompress(extract) the directory the following command will be used

```bash
tar -zxvf mydirectory.tar.gz  -C /home/newdirectory

```



## My use case
I need to compress a graphite metrics directory to make available elsewhere

```bash
$ cd /var/graphite && tar -zcvf graphitestorage.tar.gz storage

# => Move file the new machine via scp

```

Now on new host uncompress directory

```bash
$ tar -zxvf graphitestorage.tar.gz -C /var/graphite

```




[tar command]:      http://linuxcommand.org/man_pages/tar1.html