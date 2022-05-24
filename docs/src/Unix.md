# Modern Unix command
- `bat` _replacement for cat_
- `exa` _replacement for ls_ e.g. `exa --git -l --tree`
- `fd` _replacement for find_ e.g. fd '^foo'
- `rg` _replacement for grep_
- `jq` _sed for json data
- `cheat` - cheatsheet
- `tldr` - replace man
- `btm` - replace top, bottom
- `glances` - replace top
- `dog` - replace dig, DNS client
- `hyperfine` - benchmarking tool
- `gping` - ping replacement
- `curlie` - curl replacement
- `dust` _replacement for du_ disk usage statistic by file_
- `duf` _replacement for disk free space_
- `wrk` - monitoring and benchmark 

# Networking command
SSH username@ip-address or hostname	login into a remote Linux machine using SSH
Ping hostname="" or =""	To ping and Analyzing network and host connections
dir	Display files in the current directory of a remote computer
cd "dirname"	change directory to “dirname” on a remote computer
put file	upload ‘file’ from local to remote computer
get file	Download ‘file’ from remote to local computer
quit	Logout

# compression 
$ tar cvzf archive_name.tar dirname/
$ tar xvf archive_name.tar

# rg - grep file 
rg

# find file
fd

# sed command examples
Print file content in reverse order
$sed 's/.$//' filename

Add line number for all non-empty-lines in a file
$ sed -n '1!G;h;$p' thegeekstuff.txt

# shutdown -h now
Shutdown the system after 10 minutes.

# shutdown -h +10
Reboot the system using shutdown command.

# shutdown -r now
Force the filesystem check during reboot.

# shutdown -Fr now
$ sed '/./=' thegeekstuff.txt | sed 'N; s/\n/ /'

# awk - Remove duplicate lines using awk
$ awk '!($0 in array) { array[$0]; print }' temp

#   Sort a file in ascending order
$ sort names.txt

#11. xargs command examples Copy all images to external hard-drive
Search all jpg images in the system and archive it.
`ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory`

# find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz
Download all the URLs mentioned in the url-list.txt file
`cat url-list.txt | xargs wget –c`

Check the status of a service:

# service ssh status
Check the status of all the services.
`service --status-all`

# IO Direction
cmd < file
Input of cmd from file
cmd1 <(cmd2)
Output of cmd2 as file input to cmd1
cmd > file
Standard output (stdout) of cmd to file
cmd > /dev/null
Discard stdout of cmd
cmd >> file
Append stdout to file
cmd 2> file
Error output (stderr) of cmd to file
cmd 1>&2
stdout to same place as stderr
cmd 2>&1
stderr to same place as stdout
cmd &> file
Every output of cmd to file
cmd refers to a command.

# Pipes
cmd1 | cmd2
stdout of cmd1 to cmd2
cmd1 |& cmd2
stderr of cmd1 to cmd2

# Command Lists
cmd1 ; cmd2
Run cmd1 then cmd2
cmd1 && cmd2
Run cmd2 if cmd1 is successful
cmd1 || cmd2
Run cmd2 if cmd1 is not successful
cmd &
Run cmd in a subshell

# reference
[sed and awk cheatsheet](https://www.thegeekstuff.com/sed-awk-101-hacks-ebook/)
[Practical Unix (in awk)](https://practicalunix.org/)
[Modern Unix](https://github.com/ibraheemdev/modern-Unix)