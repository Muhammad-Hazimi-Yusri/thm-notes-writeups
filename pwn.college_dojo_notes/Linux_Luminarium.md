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

