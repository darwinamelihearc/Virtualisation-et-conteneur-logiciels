# Install SSH Server

```console
debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ sudo apt-get install openssh-server
...

debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ ip address
1: lo: 127.0.0.1

2: eth0: 172.28.70.77

```

Maintenant sur notre client Windows (ou Linux dans mon cas)

```console
darwin@LAPTOP-MMLBEP53:~$ sudo apt-get install openssh-client
...

darwin@LAPTOP-MMLBEP53:~$ ssh debian@172.28.70.77
The authenticity of host '172.28.70.77 (172.28.70.77)' can't be established.
ED25519 key fingerprint is SHA256:jwc6LVne4AlojlB/ggSbxLGVlUdUgfv5qTEiFenMCII.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added '172.28.70.77' (ED25519) to the list of known hosts.
debian@172.28.70.77's password:
Linux debian 6.1.0-18-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.76-1 (2024-02-01) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
debian@debian:~$ id
uid=1000(debian) gid=1000(debian) groupes=1000(debian),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),106(netdev),112(bluetooth),114(lpadmin),117(scanner)
debian@debian:~$
```

# Generate SSH Keys

```console
darwin@LAPTOP-MMLBEP53:~$ ssh-keygen
...

debian@debian:~$ exit
déconnexion
Connection to 172.28.70.77 closed.
darwin@LAPTOP-MMLBEP53:~$ ssh-copy-id debian@172.28.70.77
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/darwin/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
debian@172.28.70.77's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'debian@172.28.70.77'"
and check to make sure that only the key(s) you wanted were added.

darwin@LAPTOP-MMLBEP53:~$ ssh debian@172.28.70.77
Linux debian 6.1.0-18-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.76-1 (2024-02-01) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Fri Feb 23 09:17:51 2024 from 172.28.64.1
debian@debian:~$ exit
```

# Port Forwarding

```console
darwin@LAPTOP-MMLBEP53:~$ ssh -L 5432:127.0.0.1:5432 debian@172.28.64.1
debian@debian:~$
```

On change de PC, j'utilise PS pour pas confondre du coup.

# SSH Keys with GitHub

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account


# SSH Keys with Switch Engine

On login sur https://engines.switch.ch/horizon/quickstart/#/

Change la région en LS

# Google Compute Engine


```console
darwin@DarwinPC:~/undergit/Virtualisation-et-conteneur-logiciels$ ssh -D 7777 darwin@34.171.72.158
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.15.0-1062-gcp x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Mon Jun 17 18:14:50 UTC 2024

  System load:  0.0               Processes:             107
  Usage of /:   19.9% of 9.51GB   Users logged in:       0
  Memory usage: 22%               IPv4 address for ens4: 10.128.0.2
  Swap usage:   0%


Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status

New release '22.04.3 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Mon Jun 17 18:14:01 2024 from 84.75.116.29
darwin@instance-20240617-180520:~$
```