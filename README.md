# Creating-a-tar-file-compacted-encrypted-with-password


Encrypt File
```bash
tar cz diretorio/ | openssl enc -aes-256-cbc -e > /home/backups22-07-2021/encrypted.tar.gz.enc
```
OR

```bash
tar cz teste/ | openssl enc -aes-256-cbc -e -k 123 > /tmp/encrypted.tar.gz.enc
```

Type password and make encrypted tar.gz.enc file



To decrypt
```bash
openssl aes-256-cbc -d -in encrypted.tar.gz.enc | tar xz
```

and type password to decrypt

#Create a script to encrypt a list of files and move all to backup folder


vim /root/script.sh
```bash
#!/bin/bash

for f in `ls -d /root/BACKUP/* | xargs`

do

##If you want do encrypt##
tar cz $f | openssl enc -aes-256-cbc -e -k 123 > ${f%/}.tar.gz.enc

##If you want do decrypt##
#openssl aes-256-cbc -d -in $f -k "123" | tar xz


##Move the files in encrypt process to some backup folder##
mv $f*.tar.gz.enc /root/BACKUP

done


##To Decrypt a single file##
#openssl aes-256-cbc -d -in FILE.tar.gz.enc | tar xz ##

```
