# Compute Engine VM instance

Create nginx-gb instance on gcloud
SSH from WebGUI

```console
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 6.5.0-1022-gcp x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Mon Jun 17 18:46:01 UTC 2024

  System load:  0.0               Processes:             101
  Usage of /:   19.6% of 9.51GB   Users logged in:       0
  Memory usage: 5%                IPv4 address for ens4: 10.138.0.2
  Swap usage:   0%

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

didi_ameli@nginx-gb:~$ chmod o+X .
didi_ameli@nginx-gb:~$ git clone https://github.com/bfritscher/guestbook-src.git
Cloning into 'guestbook-src'...
remote: Enumerating objects: 1261, done.
remote: Counting objects: 100% (128/128), done.
remote: Compressing objects: 100% (57/57), done.
remote: Total 1261 (delta 77), reused 85 (delta 70), pack-reused 1133
Receiving objects: 100% (1261/1261), 442.83 KiB | 10.80 MiB/s, done.
Resolving deltas: 100% (628/628), done.
didi_ameli@nginx-gb:~$ cd guestbook-src/
didi_ameli@nginx-gb:~/guestbook-src$ cd 03_nginx_gunicorn_certbot/
didi_ameli@nginx-gb:~/guestbook-src/03_nginx_gunicorn_certbot$ 

```