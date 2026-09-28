This challenge will give you experience using basic [[Linux]] tools to find messages hidden with [[steganography]]. An image was altered slightly to embed a hidden [[Flags]] somewhere in the raw binary of the image. 

A hidden flag can be found with the strings function within linux

The following greps for SKY out of Steg1.jpg file

```bash
strings Steg1.jpg | grep SKY
```

