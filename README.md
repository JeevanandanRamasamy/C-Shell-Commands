# C-Shell-Commands

## ls with no command-line options

The ls command prints all files/directories in the current working directory.

Running ls in this directory should print

find.c

ls.c

tree.c

The files/directories are sorted in case-insensitive lexicographic order:

. < 0 < 1 < ··· < 9 < a < b < ··· < z

## ls with the -l command-line option

If the user invokes ls -l (lowercase “l” for “long”), ls prints a “long format” with extra information about each file.

-rw-rw-r-- bob users 1562 Sep 29 12:00 find.c

-rw-rw-r-- bob users 1024 Sep 29 12:05 ls.c

-rw-rw-r-- bob users 2044 Sep 27 18:23 tree.c

The first column contains a 10-character permissions string.

- the first character is ‘-’ for files, ‘d’ for directories

- the next three are read, write, and execute permissions for the user

- the next three are read, write, and execute permissions for the group

- the next three are read, write, and execute permissions for others

Permissions should be denoted by a ‘r’, ‘w’, or ‘x’ if present, or ‘-’ otherwise.

The second and third columns show the file owner’s user name and group name (or user ID / group ID if a name can’t be found).

The next column shows the file size in bytes.

Next is the file’s modification time (mtime) formatted as in the example above.

Finally, the filename is listed.

## find

The find command takes a pattern as a command-line argument and recursively searches through directories to find a filename matching that pattern. It  prints a relative path starting with “./” for every file/directory that matches.

For example, running ./find ls.c from within this directory should print ./ls.c. If run from the parent directory, the output would be ./C-Shell-Commands/ls.c.

There may be multiple matches. If we run ./find .c from within this directory, we should see:

./find.c

./ls.c

./tree.c

The output is not necessarily sorted. If nothing matches, it does not print anything. Pattern matching is case sensitive.

## tree

The tree command prints all files/directories contained in the current directory as a tree. If we run ./tree from this directory, we should see:

.

\- find.c

\- ls.c

\- tree.c

The first line of output is always “.” to denote the current directory. tree recurses into directories to print all files/directories within them. For each subdirectory, two spaces of indentation are added. For example, if we had a file test/src/foo.c, tree would print:

.

\- test

&nbsp;&nbsp;\- src

&nbsp;&nbsp;&nbsp;&nbsp;\- foo.c

Files/directories within each subdirectory are sorted with the same case-insensitive lexicographic order as ls.
