## Technologies used

* Crystal Lang
* Git + [CGIT UI tool](https://git.zx2c4.com/cgit/about/)
* Docker (all small components in docker containers) and later ZOS-Containers
* 3bot server mainly the BCDB as backend for the .toml files

## 3git command line

* -p --path= the path to process
    * if not specified the local path
* --dest
    * destination path where all the content will be put
    * if not specified ~/3git/
* -n --name
    * overrule name (if name used can only process 1 git dir)
    * std the name is the directory name of the git repo
* -d --delete 
    * delete the dest dir & do full scan
* -f --full
    * redo the full scan
* --check 
    * check that the links exist
* --filepath= …  
    * Path where the hashed files will come
* --fileurl=...
    * Url which will be used to replace in the markdown docs
    * e.g. [https://kristof.3bot.me/files](https://kristof.3bot.me/files)
* --develop=[http://localhost:8080](http://localhost:8080) (**)
    * Run the 3cm tool in development mode on url as specified
* --monitor
    * keep on monitor file changes, if found process
    * can be slow for lots of files !!! 

will be executed per .git repo it finds under -p


## process files

### git powered

- we remember the last state of git (what was processed)
- only process commits after the last one
- only process files which were changed since last one
- --force means we walk over all files, independent of last git state

### wiki

- [see wiki specs](wiki.md)

### data files

- [see data specs](data.md)


## Development mode (**)

* Run webserver on port 8080 or other port as specified (use full url http or https…)
* Purpose
    * Provide immediate visibility for the wiki or other content worked on
    * Wiki software = docsify (html code on git repo which get’s cloned)
* Expose webserver on url as specified
* check for changes on the filesystem & when change, process the changed files only (is same as --monitor but here also with webserver)

### paths

* /wiki/$name/ .. starting point of the wiki files
* /files/..  where the deduped files are


## How to deal with files?

Idea is to copy files out of the git repo into a content addressed directory structure.

* Files > 100 KB 
* Copy to \$FILEPATH/\$HASH2LETTERS/\$HASH.\$FILEEXT
* Replace link to \$FILEURL/\$FILENAMEORG__\$HASH.\$FILEEXT
    * we add the filenameorg so its easier to see what file was
    * the webserver software will only use the hash part to find the file back 
* In directory where the file was put (this is to keep the link to the original file)
    * \$FILENAMEORG.\$FILEEXT.meta
        * Which is data in toml file
        * Toml data
            * size = size in kbytes
            * Url = … the url where the file now can be found
                * \$FILEURL/\$FILENAMEORG__\$HASH.\$FILEEXT

Remarks

* HASH2LETTERS = is the first 2 letters of the hash of the file
    * Done for more scalability on filesystem
* FILEEXT = extension of the file e.g. jpg
* FILENAMEORG = original name of the file
* FILEPATH = is the locxation where all the files will be stored deduped

# Remarks

## Next gen = (**)

Means version 2 of this software.

