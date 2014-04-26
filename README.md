fbackup
=======

Perform incremental backups using a fossil repository as a storage. Each
backup ends up in a new commit where files are added / removed / modified
according to their staus with respect to the previous commit.

Files to include / exclude from the backup are specified in a configuration
file (see -conf option below), which consists of one "include" and one
"exclude" section, in which files or directories to include / exclude from
the backup are listed, separated by whitespace (\n, \t, space, ...).
Directories are searched recursively. Example:

    include {
        /path/to/file/to/include
        /path/to/directory/to/include
        /another/1 another/2 another/3
    }
    exclude {
        /path/to/file/to/exclude
        /path/to/directory/to/exclude
    }

The software depends on <a href="http://fossil-scm.org/">fossil</a>, and <a href="http://core.tcl.tk/tcllib/">tcllib</a>. Files are hard-linked from their location on disk into the temporary checkout using cpio.

Usage:

    fbackup : ./fbackup.tcl [options]
    options:
     -conf   value    Path to the backup list file      <./fbackup.list>
     -cpio   value    Path to the "cpio" executable     </usr/bin/cpio>
     -fossil value    Path to the "fossil" executable   </usr/local/bin/fossil>
     -name   value    Name of the backup project        <Backup>
     -repo   value    Path to the repository file       <./fbackup.fossil>
     --               Forcibly stop option processing
     -help            Print this message
     -?               Print this message
