
# Unix Cheatsheet: `find` Command
- **`find . -name "*.gif" -exec ls {} \;`**
  - Finds all `.gif` files in the current directory and its subdirectories and lists them using `ls`.

- **`find . -name "*.txt" -ok rm -f {} \;`**
  - Searches for all `.txt` files and prompts you before deleting each one.

- **`find . \( -name "a.out" -o -name "*.o" -o -name "core" \) -exec rm -f {} \;`**
  - Removes files named `a.out`, with extension `.o`, or named `core` from the current directory and subdirectories.

- **`find . -depth -print | cpio -pdmv /newdir`**
  - Recursively copies files and directories from the current directory to `/newdir` using `cpio`.

- **`find . -name "*.txt" -exec head -1 {} \; > report.txt`**
  - Extracts the first line from each `.txt` file and saves the result to `report.txt`.

- **`find $LOGDIR -type d -mtime +0 -exec compress -r {} \;`**
  - Compresses directories in `$LOGDIR` that were modified more than 0 days ago.

- **`find $LOGDIR -type d -mtime +5 -exec rm -f {} \;`**
  - Deletes directories in `$LOGDIR` that haven't been modified in the last 5 days.

- **`find /source_dir \( ! -user bill ! -group bill ! \( -perm 6000 \) \) | cpio –pdmv /target_dir`**
  - Finds files in `/source_dir` not owned by user `bill`, not in group `bill`, and not having permission `6000`, then copies them to `/target_dir`.

- **`find / \( type l \) –print | perl –nle '-e || print'`**
  - Finds all symbolic links in `/` and prints those that are broken.

- **`ls –i | grep 1234567890 | find . –inum 1234567890 –exec mv {} newname \;`**
  - Finds a file with inode number `1234567890` and renames it to `newname`.

- **`find . –size 0 –exec ls –l {} \;`**
  - Lists all empty files in the current directory and its subdirectories.

