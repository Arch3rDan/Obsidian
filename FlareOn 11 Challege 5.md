Server has crashed and we have to know why
literally an entire filesystem

Going to have a few relevant and a lot that aren't
	using [[find]] and [[grep]] are VERY important
	Poking around finds some weird stuff
	Running "[[podman]]" allows you to analyze the [[binary]] of something
	flag.txt = big chungus :D

var/lib/systemd/coredump 
	[[GDB]] can open
	[[IDA]] is another option
	Using the existing tools is better because they're likely to work better
	[[Stackframe]] 0x00000000000 called [[null]] <--- big hint

Checking stack, who called [[null]]? Deleted file

dlsym()
	Dynamically load into process
	normally automatically, can dlopen or dlsym for some reason (look into later)
Why is LZMA (compression library) trying to call RSA functions
Why is the function string name located in the LZMA binary
"rsa_public_decript"

Who went to LZMA? Farther up the call stack
	Supposed to go to 
	[[sshd]] when loaded need openssl need RSA...
	[[Linux]] then gets the above, loads openssl.sa
		within this is the code for everything, points to code!
	instead went to LZMA

Time to inspect [[LZMA]]
	[[PLT]] = procedure linkage table
	Pointed to [[LZMA]] for malicious reasons
Error happened because they accidentally added an extra space sot RSA_public_decrypt#',0 where # was extra space

Look at the function that called null by accident
	Found using XREF but one can also rebase the pogram and jump
	RDI RSI RDX RCX R8 R9
	RSI is user controlled! Pay attention in [[Assembly]] code
	are the rest user controlled??? It's not about which are user controlled (they all are?) 
		Either change the nature of the function entirely
		or jump to a copy of the code with malicious code in the background to appear the same
rsi is sent into rbp, from parameters are carrying rsi?
[[getuid]] is a called thing

whoa hey look theres a sub 9520 and sub 93F0
what is it tho?
	also [[mmpa]] call and [[memcpy]] eventually labeled [[payload]] and [[r8]]

Decript the [[keystring]] using "expand 32 k" 

8 or 12 bytes into r11
	rbp + 24h == pointing to nonce
	key is 24 bytes ahead?
32 bytes into r10
	rbp + 4 == pointing to key because offset by 4
	magic is 4 bytes ahead
[[chacha]] = plaintext to 

where is key!?
check coredump for key

[[magic value]] search:
	some bytes for [[key]] find
	yippie
decrypt the [[shellcode]]
	dlopen it and address of function, using the magic key
	function called that runs the shellcode
shellcode doesn't give us the flag

Alternative Hook was called
	They ran from [[openssl]].sa to [[LZMA]].sa

[[strace]](1) revealed a failed call to [[connect]](2) silly address and port was [[1337]] >:D
	data was likely being stolen btw

need to extract shellcode by dumping it by reading from binary or something
	or GDB start address and end address

[[Binary Ninja]]
address and port are hardcoded 10.0.2.15:1337 (btw this doesn't exist lol)

shellcode was re-encrypted, file contents was not re-encrypted and the key isn't either.
	both are probably still in the [[core dump]] :D

Would you look at that they're still there
	because the goober who made it added a space
	additionally found the path

now we have filepath and the key
	but the deleted file wasn't there :0
	outside wanted a code and then deleted the file, disappointed because not in [[filesystem]]

[[Encrypted]] bytes of the file are still in the [[coredump]], but had the [[key]]. The expand 32bit K but k was uppercase

was a [[symmetric cypher]] and goes backwards. and it goes and spits out the [[flag]] :D

other terms
	sshd
	sbin
	ChaCha20
	Salsa20