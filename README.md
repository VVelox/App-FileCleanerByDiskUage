# App-FileCleanerByDiskUage

Removes old files based on total amount of disk used till disk usage drops below the specified amount.

# SYNOPSIS

file_cleaner_by_du B<-p> <path> B<-d> <du> [B<-m> <min_files>] [B<--pretty>] [B<--dry_run>]

# DESCRIPTION

This works via doing the following.

1: Check if disk usage is above the specified threshold. If not it ends here.

2: Search for files under the specified path.

3: If the number of found files is less than the number of files to keep regardless
of disk size it ends here. So if min_files is set to 32 and there are only 3 files,
then it would just return.

4: Get the stats for all the found files.

5: If min_files is specified, remove that many of the files from the list, starting
with the newest.

6: Removes the oldest file.

7: Check disk usage again and if it is less it ends here.

8: Go back to 6.

The results are then printed as JSON. To find information on the keys, please
see L<App::FileCleanerByDiskUage>.

If there were no errors, it will exit zero.

# FLAGS

```
-d <du>        Target disk usage.

-p <path>      The path to operate on.

-i <regex>     Optional ignore regex.

-i <min files> Optional minimum number of files to keep regardless of disk usage.

--pretty       Pretty print the results.

--dry_run      Do not actually delete anything. Instead just check if
               what it would delete is writable by the current user.

-v             Print version.
--version      Print version.

-h             Print help.
--help         Print help,
```

# INSTALLATION

# cpanm

```
cpanm  App::FileCleanerByDiskUage
```

## source

```
perl Makefile.PL
make
make install
```
