# Install Hyper-V 

- Activer Hyper-v dans les fonctionnalités Windows
- Créer une machine
- Désactiver le secure boot
- Boot sur l'iso

Keyboard:             swiss french
Hostname:             debian
Domain:               lab.local
User Account:         debian
Partition Disk:       use entier disk / all files in one partition
Desktop Environment:  optional, we only require a shell.

# Setup Sudoers

```console
debian@debian:~$ whoami
debian
debian@debian:~$ groups
debian cdrom floppy audio deip video plugdev users netdev bluetooth lpadmin scanner
debian@debian:~$ su -
Mot de passe : [password]
root@debian:~# usermod -aG sudo debian
root@debian:~# exit
déconnexion
debian@debian:~$ su - debian
Mot de passe : [password]
debian@debian:~$ whoami
debian
debian@debian:~$ groups
debian cdrom floppy sudo audio deip video plugdev users netdev bluetooth lpadmin scanner
debian@debian:~$ sudo whoami
[sudo] Mot de passe de debian : [password]
root
debian@debian:~$
```

# Guestbook App

```console
debian@debian:~$ sudo apt-get install python3 python3-pip python3-venv git -y
...
debian@debian:~$ git clone https://github.com/bfritscher/guestbook-src.git
...

debian@debian:~$ python3 -v venv venv
debian@debian:~$ cd guestboook-src/02_mvp_modules_sqlite3/
debian@debian:~$ source ~/venv/bin/activate
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ pip install -r requirements.txt
... 
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ ip address
1: lo: 127.0.0.1/8

2: eth0: 172.28.79.77/20
```

# Install Database

```console
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ sudo apt-get install postgresql postgresql-client
...
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ sudo -u postgres psql
psql (15.6)

postgres=# CREATE DATABASE guestbook;
CREATE DATABASE
postgres=# CREATE USER guestbook WITH ENCRYPTED PASSWORD 'mypass';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE guestbook TO guestbook;
GRANT
postgres=# ALTER DATABASE guestbook OWNER TO guestbook;
ALTER DATABASE
postgres=# \q

(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ touch .env
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ nano .env
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ cat .env
DB_HOST=localhost
DB_PORT=5432 # Default PostgreSQL port
DB_NAME=guestbook
DB_USER=guestbook
DB_PASS=mypass
GUESTBOOK_SERVICE=postgres

(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ nano gbmodel/__init__.py
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ cat gbmodel/__init__.py
import os
...
# model_backend = os.getenv('GUESTBOOK_SERVICE', 'sqlite3')
model_backend = 'postgres'
# model_backend = 'pylist'
...
```

On a changé le backend de sqlite3 à postgres

```console
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ python3 app.py
 * Serving Flash app 'app'
 ...
(venv) debian@debian:~/guestboook-src/02_mvp_modules_sqlite3$ sudo -u postgres psql
...

postgres=# \c guestbook
guestbook=# \d
        List of relations
 Schema |      Name       |   Type   |  Owner   
 -------+-----------------+----------+----------
 public | entries         | table    | guestbook
 public | entries_id_seq  | sequence | guestbook
 (2 rows)

guestbook=# SELECT * FROM entries ;

id |     name     |         email          |         signed_on          |            message 
---+--------------+------------------------+----------------------------+--------------------------------   
 1 | Darwin Ameli | darwin.ameli@he-arc.ch | 2024-02-21 16:52:49.507987 | First message from debian\r+

(1 row)
```
