+++
title = "Information about SVN (Subversion)"
date = "2024-01-07"
+++

## Subversion (SVN) information

Even if nowadays Git is the prefered version control system in software development, still some companies are using the older systems like subversion (SVN). As I had the opportunity to migrate a subversion based repository from on server instance to a new server location, I want to share my experience in this blog post.

All the following commands assume, that you have access to the repository and have privilages to directly connect to the servers over SSH. To simplify the following section the first server holding the original repository will be assigned the name _server A_, the new target server is called _server B_.

As a first step login to _server A_ over SSH and generate a dump file of the whole SVN repository with the follwing command.

```bash
svnadmin dump /path/to/repo > filename.dump
```

In this case the dump file contains all relevant information (tags, commits, branches, ...). After that the file can be transfered to _server B_ with e.g. the scp command. From there the new location of the repository can be defined and the whole information can be integrated.

```bash
svnadmin create /path/to/new/folder/location
svnadmin load /path/to/new/folder/location < filename.dump
```

To improve the procedure and save file size of the dump file, the output of the first command can be compressed. With this slight improvement up to 50% of file size can be saved.

```bash
# compress the file on server A
svnadmin dump /path/to/repo | gzip -9 > filename.dump.gz

# on server B side, the file has to be uncompressed
gunzip -c filname.dump.gz | svnadmin load /path/to/new/folder/location
```
