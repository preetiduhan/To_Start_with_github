# daily notes
For installing pip on linux machine:
```
$ curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"

$ python get-pip.py     
$ python3 get-pip.py 
pip install tox
```

```
Let's see how to copy files and create backups with rsync :
1.	 To copy a source directory to a destination use:
$ rsync -av source_path destination_path
For example,
$ rsync -av /home/slynux/data slynux@192.168.0.6:/home/backups/
data
In this command:
  -a stands for archiving
  -v (verbose) prints the details or progress on stdout
The above command will recursively copy all the files from the source path to the
destination path. We can specify paths as remote or local paths.
234Chapter 6
2.	 In order to backup data to a remote server or host, use:
$ rsync -av source_dir username@host:PATH
To keep a mirror at the destination, run the same rsync command scheduled at
regular intervals. It will copy only changed files to the destination.
3.	 Restore the data from the remote host to localhost as follows:
$ rsync -av username@host:PATH destination```


