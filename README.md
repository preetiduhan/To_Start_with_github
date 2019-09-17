# daily notes
For installing pip on linux machine:
```
$ curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"

$ python get-pip.py     
$ python3 get-pip.py 
pip install tox
```

How to use rsync for backup :
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

```
Every system administrator has to deal with plain text files on a daily basis. Knowing how to view certain sections, how to replace words, and how to filter content from those files are skills…

Please note that the -i option indicate in-place editing. Then changes will not be returned to the screen, but will be saved to the file.

1. Viewing a range of lines of a document

Tools such as head and tail allow us to view the bottom or the top of a file. What if we need to view a section in the middle? The following sed one-liner will return lines 5 through 10 from myfile.txt:

# sed -n '5,10p' myfile.txt

2. Viewing the entire file except a given range

On the other hand, it’s possible that you want to print the entire file except a certain range. To exclude lines 20 through 35 from myfile.txt, do:

# sed '20,35d' myfile.txt

3. Viewing non-consecutive lines and ranges

It’s possible that you’re interested in set of non-consecutive lines, or in more than one range. Let’s display lines 5-7 and 10-13 from myfile.txt:

# sed -n -e '5,7p' -e '10,13p' myfile.txt

4. Replacing words or characters (basic substitution)

To replace every instance of the word version with story in myfile.txt, do:

# sed 's/version/story/g' myfile.txt

Additionally, you may want to consider using gi instead of g in order to ignore character case:

# sed 's/version/story/gi' myfile.txt

To replace multiple blank spaces with a single space, we will use the output of ip route show and a pipeline:

# ip route show | sed 's/  */ /g'

Compare the output of ip route show with and without the pipeline:
Replace Words or Characters in File

5. Replacing words or characters inside a range

If you’re interested in replacing words only within a line range (30 through 40, for example), you can do:

# sed '30,40 s/version/story/g' myfile.txt

Of course, you can indicate a single line through its corresponding number instead of a range.

6. Using regular expressions (advanced substitution) – I

Sometimes configuration files are loaded with comments. While this is certainly useful, it may be helpful to display only the configuration directives sometimes if you want to view them all at a glance.

To remove empty lines or those beginning with # from the Apache configuration file, do:

# sed '/^#\|^$\| *#/d' httpd.conf

The caret sign followed by the number sign (^#) indicates the beginning of a line, whereas ^$ represents blank lines. The vertical bars indicate boolean operations, whereas the backward slash is used to escape the vertical bars.

In this particular case, the Apache configuration file has lines with #’s not at the beginning of some lines, so *# is used to remove those as well.

7. Using regular expressions (advanced substitution) – II

To replace a word beginning with uppercase or lowercase with another word, we can also use sed. To illustrate, let’s replace the word zip or Zip with rar in myfile.txt:

# sed 's/[Zz]ip/rar/g' myfile.txt

Don’t Miss: Use Awk with Regular Expressions to Filter Text in Files

7. Using regular expressions (advanced substitution) – II

To replace a word beginning with uppercase or lowercase with another word, we can also use sed. To illustrate, let’s replace the word zip or Zip with rar in myfile.txt:

# sed 's/[Zz]ip/rar/g' myfile.txt

8. Viewing lines containing with a given pattern

Another use of sed consists in printing the lines from a file that match a given regular expression. For example, we may be interested in viewing the authorization and authentication activities that took place on July 2, as per the /var/log/secure log in a CentOS 7 server.

In this case, the pattern to search for is Jul 2 at the beginning of each line:

# sed -n '/^Jul  1/ p' /var/log/secure



Every system administrator has to deal with plain text files on a daily basis. Knowing how to view certain sections, how to replace words, and how to filter content from those files are skills you need to have handy without having to do a Google search.
Linux Sed Command Examples

15 Useful ‘sed’ Command Tips and Tricks for Linux

In this article we will review sed, the well-known stream editor, and share 15 tips to use it in order to accomplish the goals mentioned earlier, and more.
1. Viewing a range of lines of a document

Tools such as head and tail allow us to view the bottom or the top of a file. What if we need to view a section in the middle? The following sed one-liner will return lines 5 through 10 from myfile.txt:

# sed -n '5,10p' myfile.txt

2. Viewing the entire file except a given range

On the other hand, it’s possible that you want to print the entire file except a certain range. To exclude lines 20 through 35 from myfile.txt, do:

# sed '20,35d' myfile.txt

3. Viewing non-consecutive lines and ranges

It’s possible that you’re interested in set of non-consecutive lines, or in more than one range. Let’s display lines 5-7 and 10-13 from myfile.txt:

# sed -n -e '5,7p' -e '10,13p' myfile.txt

As you can see, the -e option allows us to execute a given action (in this case, print lines) for each range.
4. Replacing words or characters (basic substitution)

To replace every instance of the word version with story in myfile.txt, do:

# sed 's/version/story/g' myfile.txt

Additionally, you may want to consider using gi instead of g in order to ignore character case:

# sed 's/version/story/gi' myfile.txt

To replace multiple blank spaces with a single space, we will use the output of ip route show and a pipeline:

# ip route show | sed 's/  */ /g'

Compare the output of ip route show with and without the pipeline:
Replace Words or Characters in File

Replace Words or Characters in File
5. Replacing words or characters inside a range

If you’re interested in replacing words only within a line range (30 through 40, for example), you can do:

# sed '30,40 s/version/story/g' myfile.txt

Of course, you can indicate a single line through its corresponding number instead of a range.
6. Using regular expressions (advanced substitution) – I

Sometimes configuration files are loaded with comments. While this is certainly useful, it may be helpful to display only the configuration directives sometimes if you want to view them all at a glance.

To remove empty lines or those beginning with # from the Apache configuration file, do:

# sed '/^#\|^$\| *#/d' httpd.conf

The caret sign followed by the number sign (^#) indicates the beginning of a line, whereas ^$ represents blank lines. The vertical bars indicate boolean operations, whereas the backward slash is used to escape the vertical bars.

In this particular case, the Apache configuration file has lines with #’s not at the beginning of some lines, so *# is used to remove those as well.
7. Using regular expressions (advanced substitution) – II

To replace a word beginning with uppercase or lowercase with another word, we can also use sed. To illustrate, let’s replace the word zip or Zip with rar in myfile.txt:

# sed 's/[Zz]ip/rar/g' myfile.txt

Don’t Miss: Use Awk with Regular Expressions to Filter Text in Files
8. Viewing lines containing with a given pattern

Another use of sed consists in printing the lines from a file that match a given regular expression. For example, we may be interested in viewing the authorization and authentication activities that took place on July 2, as per the /var/log/secure log in a CentOS 7 server.

In this case, the pattern to search for is Jul 2 at the beginning of each line:

# sed -n '/^Jul  1/ p' /var/log/secure

View Logs (Lines) of Particular Date

View Logs (Lines) of Particular Date
9. Inserting spaces in files

With sed, we can also insert spaces (blank lines) for each non-empty line in a file. To insert one blank line every other line in LICENSE, a plain text file, do:

# sed G myfile.txt

To insert two blank lines, do:

# sed 'G;G' myfile.txt

Add an uppercase G separated by a semicolon if you want to add more blank lines. The following image illustrates the example outlined in this tip





