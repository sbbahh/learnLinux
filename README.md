# Learn Linux Commands🐧

<!-- 🔒 🔓-->

<!-- Searching for a file or directory -->

### 5. Find
##### Used to find files or folders.
```bash
find . -name "*.js" # find file by name and extension
```

```bash
find . -type d -name src #to find a directory
```

```bash
find . -type f -name src #to find a file
```

###### 🍉 -name & -iname
> -name is the case sensitive.
> -iname to perform a case-insensitive search.

##### Exclude a path, using -not -path
```bash
find . -type f -name '*.md' -not -path 'markdown'
```
##### Search files that have more than 100 characters (bytes).
```bash
find . -type f -size +100c #c is stand for Char
find . -type f -size +100k -1M #k is stand for KB less than 1M
```
##### Search a file edited more than three days ago

```bash
find . -type -name 'index.js' -mtime -1 #Search files edited in the last 24 hours

find . -type -name 'file.js' -mtime +3 #Search files edited more than 3 days
```

##### You can execute a command on each result of the search. In this example we run cat to print the file content:

```bash
find . -type -exec cat {} \;
```


<!-- ln Links -->
## 6. ln
##### It's used to create links.

###### Links types
1. Hard Links
1. Soft Links

```bash
ln index.js file.js # this is the hard links
ln -s index.js file.js # this is the soft links
```


<!-- zip file -->
## 7. gzip
##### Compress a file using the gzip compression

```bash
gzip index.js
gzip -c index.js > index.js # to prevent this (-c) 🍉
gzip -r folder # compress all the files in a directory, recursively (-r) 🍉
```
##### To decompress a file, using the -d option
```bash
gzip -d file.js.gz
```


<!-- Unzip a file -->
## 8. gunzip
##### The gzip gunzip command is basically equivalent to the command, except the -d

```bash
$gunzip file.gz
```


<!-- tape archive -->
## 9. tar
##### Is used to create an archive, grouping multiple files in a single file.

```bash
tar -cf -archive.tar fileone.js filetwo.js # -cf create file
```
###### To extract files from an archive
```bash
tar -xf archive.tar
```
##### And to extract them to a specific directory, use:
```bash
tar -xf archive.tar -C Directory name
```
##### List the files in  the archive
```bash
tar -tf archive.tar
```
##### Creating a tar archive, and then running gzip on it.
```bash
tar -czf archive.tar.gz sbbah.js
tar -xf archive.tar.gz # extract files from 'archive.tar.gz'
```
## 10. alias
##### print info including the file modification date, the size, the owner, and the permissions.

```bash
ls -al
```
> **Output of _ls -al_**
drwxrwxr-x 2 sbbah sbbah  4096 Jun  9 04:18 .
drwxrwxr-x 6 sbbah sbbah  4096 Jun  9 04:05 ..
-rw-rw-r-- 1 sbbah sbbah 10240 Jun  9 04:01 archive.tar
-rw-rw-r-- 1 sbbah sbbah   171 Jun  9 04:13 archive.tar.gz
-rw-rw-r-- 1 sbbah sbbah    55 Jun  9 04:07 sbbah.js

## 11. cat
##### In its simplest usage, cat prints a file's content to the standard output.

```bash
cat file.js
```
###### and using the output redirection operator > you can concatenate the content of multiple files into a new file:
```bash
cat fileOne fileTwo > fileThree 
```
###### Using the (-n) 🍉 to print the number of line:
```bash
cat -n file.js
```
**The output**:
> 1	let name = "Sbbah";
2	
3	console.log(name);



## 12. Less
##### It shows you the content stored inside a file, in a nice and interactive UI.

```bash
less file.js
```



## 13. WC
##### gives us useful information about a file or input it receives via pipes.

```bash
ls -al | wc
```
**The output:**
>       7      56     305
__The first column returned is the number of lines. The
second is the number of words. The third is the
number of bytes.__

###### All that will be divided at the following method:
```bash
wc -l file.js # it will print the lines of the file.
wc -w file.js # it will print the words of the file.
wc -c file.js # it will print the bytes of the file.
```

###### Important note: 🍉🍉🍉
> Bytes in ASCII charsets equate to characters, but with non-ASCII charsets, the number of characters might differ because some characters might take multiple bytes, for example this happens in Unicode. In this case the (-m) flag will help getting the correct value.

```bash
wc -m file.js
# OutPut
# 40 file.js
```
