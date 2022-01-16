---
title: Sign commits with GPG keys
author: Jegors Čemisovs
summary: Sign commits with GPG keys on Ubuntu
---

## Configure the environment

### Install GPG2

```shell
sudo apt -y install gnupg2 gnupg-agent pinentry-gnome3 
```

### Verify installation

```shell
gpgconf
```

Expected output is like the following:
```text
gpg:OpenPGP:/usr/bin/gpg 
gpg-agent:Private Keys:/usr/bin/gpg-agent 
scdaemon:Smartcards:/usr/lib/gnupg/scdaemon 
gpgsm:S/MIME:/usr/bin/gpgsm 
dirmngr:Network:/usr/bin/dirmngr 
```

### Generate GPG keys

```shell
gpg --full-generate-key
```

Answer the questions that the tool will return. The recommended choices are:

- Type of the key: RSA
- Key size: at least 4096 bits
- Key validity period: 1 year 

### Check imported keys

```shell
gpg --list-keys
```
### Configure IntelliJ IDE

Settings | Version Control | Git | Configure GPG Key

![Configure GPG Key](../assets/images/2022-01-16/settings-git-configure-gpg-key.png)

![Commits are signed](../assets/images/2022-01-16/commits-are-signed.png)

### Export the keypair to a file

Use the same email address that you used for generating the key pair:

```shell
gpg --export -a "email@address.com" > public.key
```

