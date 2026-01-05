# Hello Hackers
no note, hello all
# Pondering Paths
pwd, cd,
# Comprehending Commands
- cat, grep, find, ls, ls -al.
- touch, mkdir, cp, mv
- diff, file
## Symbolic links (like shortcut? for soft link)
- ln -s (symlinks/soft link)
- theres also hard link
- these can be useful to access original restricted file content etc
- ./.... for explicit command in same dir, need to have ./ at start to differentiate with commands in paths.
# Digesting Documentation
- man [cmd], can search with / in manual page mode, PgUp/PgDn to scroll, n for next result, N for previous, ? to search backwards
- man man.
- sometimes [cmd] -h, or --help, or even -? or /? like in powershell
for builtins commands, use help [cmd] instead
# File Globbing
- like regex? pretty useful.
- \* for any wildcard, can be nothing, no length restriction
- ? for single char wildcard
- [abc] for specific single character, either a,b, or c here for example
- can use these mixed together, and to match paths as well, not just file.#
- use ! or ^ (in newer version of bash) for negative matching (exclusions)
- can also use for commands, but probably safer to use tab completion to make sure correct command is ran.
# Practicing Piping 
- \> to pipe output into a file, create or overwrite 
- \>\> to append to file
- add number as prefix which is File Descriptor (FD) to choose different STD, STDIN (0), STDOUT (1) and STDERROR (2) for .e.g:
`hacker@dojo:~$ some_command > output.log 2> errors.log`
- < to pipe input to cmd, such as `cmd < file`
- use grep on output file, `grep 'words-to-find' file.txt`
- | pipe operator used to pipe cmd output from left as input for right `cmd1 input | grep 'words-to-find-in-output-of-cmd1'`
- use `cmd input 2>& 1 | grep 'flag'` to change stderr to stdout file descriptor
- use -v argument for invert matching using grep `cmd input | grep -v 'fake-flag'`
- sed used for substitute patterns `sed "s/oldword/newword/g"` where s is substitute and g is global search
- use tee command to split like a T-splitter from plumbing pipes, useful to see both output while using piping
- everything is a file in linux, so u can treat command output as file and use diff on them by encapsulating in <(echo hi) for example. (process substitution? idk)
- subsequently, u can write to multiple file with >(rev) for example using rev comand: `echo HACK | tee >(rev)`, tbh i dont really get it but cool stuff
- thus `echo hi | rev` is same with `echo hi > >(rev)`, same with `echo hi | rev | rev` and `echo hi > >(rev | rev)`
- process substitution is specialised tool! dont use for everything, as seen the former for both is harder to read!
- Split-piping stderr and stdout challenge is a bit confusing, i solved using > and >() but not with |, idk how to incorporate | properly
- Named pipes. process substitution create temp pipes like /dev/fd/63 etc. we can create persistent pipes that stick around on the filesystem. These are called FIFO which stands for First (byte) In, First (byte) out. use `mkfifo my_pipe` command.
- One problem with FIFO is that theyll block any operations on them until both read side and write side of pipe are ready.
- that is useful because it ensure automatic sync
- FIFO used for these benefits: 1. no disk storage, epphremeral data, auto sync, and complex data flows
