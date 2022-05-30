# Modern Unix command
- `bat`: modern of `cat`
- `exa`: modern of `ls`, e.g. `$exa --git -l --tree`
- `fd`: modern of `find`, e.g. `$fd ^foo`
- `rg`: modern of `grep`
- `jq`: sed for json data
- `cheat`: cheatsheet, modern of `man`
- `tldr`: modern of `man`
- `btm`: modern of `top`, `bottom`
- `glances`: modern of `top`
- `dog`: DNS client, modern of `dig`
- `hyperfine`: benchmarking tool
- `gping`: modern of `ping`
- `curlie`: modern of `curl`
- `dust`: modern of `du`, disk usage statistic by file
- `duf`: modern of `du`, show disk free space
- `wrk`: monitoring and benchmark 

# ssh - Send file to remote ssh host
- `$SSH username@ip-address`: login into a remote Linux machine using SSH
- `$put file`: upload ‘file’ from local to remote computer
- `$get file`: Download ‘file’ from remote to local computer
- `$quit`: Logout

# tar - compression 
`$ tar cvzf archive_name.tar dirname/`: compress
`$ tar xvf archive_name.tar`: uncompress

# sed - text processor
`$sed 's/.$//' filename`: Print file content in reverse order
`$sed -n '1!G;h;$p' thegeekstuff.txt` Add line number for all non-empty-lines in a file

# awk - remove duplicate lines using awk
`$ awk '!($0 in array) { array[$0]; print }' temp`

# sort - sort file in ascending order
`$sort names.txt`

# xargs - exectue util
- `$ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory`: search all jpg images in the system and archive it.
- `$find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz`
- `$cat url-list.txt | xargs wget –c`: Download all the URLs mentioned in the url-list.txt file

# service - Check the status of all the services.
`$service --status-all`

# IO Direction
- `$cmd < file`: Input of cmd from file
- `$cmd1 <(cmd2)`: Output of cmd2 as file input to cmd1
- `$cmd > file`: Standard output (stdout) of cmd to file
- `$cmd > /dev/null`: Discard stdout of cmd
- `$cmd >> file`: Append stdout to file
- `$cmd 2> file`: Error output (stderr) of cmd to file
- `$cmd 1>&2`: stdout to same place as stderr
- `$cmd 2>&1`: stderr to same place as stdout
- `$cmd &> file`: Every output of cmd to file

# Pipes
- `$cmd1 | cmd2`: stdout of cmd1 to cmd2
- `$cmd1 |& cmd2`: stderr of cmd1 to cmd2

# Command Lists
- `$cmd1 ; cmd2`: Run cmd1 then cmd2
- `$cmd1 && cmd2`: Run cmd2 if cmd1 is successful
- `$cmd1 || cmd2`: Run cmd2 if cmd1 is not successful
- `$cmd &`: Run cmd in a subshell
 
# Reference
- [sed and awk cheatsheet](https://www.thegeekstuff.com/sed-awk-101-hacks-ebook/)
- [Practical Unix from Stanford](https://practicalunix.org/)
- [Modern Unix](https://github.com/ibraheemdev/modern-Unix)
- [top awk example](https://hackr.io/blog/awk-command-unix-linux-examples)