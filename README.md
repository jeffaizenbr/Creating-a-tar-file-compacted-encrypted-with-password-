# Creating-a-tar-file-compacted-encrypted-with-password


Encrypt File
```bash
tar cz diretorio/ | openssl enc -aes-256-cbc -e > /home/backups22-07-2021/encrypted.tar.gz.enc
```

Type password and make encrypted tar.gz.enc file



To decrypt
```bash
openssl aes-256-cbc -d -in encrypted.tar.gz.enc | tar xz
```

and type password to decrypt
