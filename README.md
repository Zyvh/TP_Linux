# TP Linux

## Références

- Documents issus de vos propres recherches sur Internet
- Si vous le souhaitez, le [document compagnon du MOOC « Maîtriser le shell Bash »](http://www.opimedia.be/DS/languages/Bash/MOOC-Maitriser-le-shell-Bash--Document-compagnon--v2-6-2019.pdf), en français et relativement bien fait

## Méthodologie

- Vous utiliserez un éditeur de texte simple pour vos réponses (pas de Google Docs ou autre format riche)
- Vous utiliserez la [syntaxe Markdown](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#quoting-code) (fichiers `.md`) pour rédiger ; Markdown est un langage de balisage léger, facile à lire et à écrire, qui peut être converti en HTML ou en d'autres formats, nativement supporté par GitHub, et très approprié pour écrire de la documentation technique
- Pour chaque question, vous préciserez :
  - la commande utilisée (si une commande est demandée)
  - la sortie de la commande le cas échéant (ce qui s'affiche à l'écran)
  - votre réponse argumentée si nécessaire
- La commande doit être clairement différenciée de la sortie en étant précédée d'un caractère de prompt (`$`). Par exemple :

```bash
$ echo "ceci est la sortie de la commande"
ceci est la sortie de la commande
```

- Vous utiliserez la syntaxe Markdown de code (\`\`\`) pour formater les commandes et les sorties de commandes
- Vous versionerez ces fichiers-réponses avec Git

## Travaux pratiques

### 1. Gestion de fichiers

- Commandes : `pwd, cd, ls, file, less, head, tail, mkdir, cp, mv, rm, rmdir, touch, echo, set, unset, export, env, alias, history, nl, find, grep, sed`
- Notions :
  - « Globbing » de fichier
  - Variables Shell
  - Variables d'environnement (commandes `export` et `env`)
  - Alias de commandes (commande `alias`)
  - Historique de commandes
  - Redirection d'entrées/sorties (STDOUT, STDERR, STDIN, utilisations des caractères `<` et `>` dans les commandes)
  - « Piping » (caractère `|` dans les commandes, bien comprendre différence avec `>`)
  - Sous-commandes (`$(commande a executer)` à l'intérieur d'une autre commande)
  - Expressions régulières
  - Bien comprendre `find` (recherche fichiers) et `grep` (recherche dans fichiers)
  - Commande `sed` pour éditer un fichier en ligne de commande (automatiquement), par exemple pour remplacer une chaîne de caractère par une autre
  - Commandes d'archivage et de compression : `tar`, `gzip`, `gunzip` `bz2`, `xz`

1. Ouvrir un terminal
2. Afficher le répertoire courant
```
$ls
```

3. En utilisant un chemin absolu, aller sur le répertoire `/etc`
```
$cd /etc/
```

4. En utilisant un chemin relatif, aller sur le répertoire `/etc/skel`
```
$cd skel
```

5. En utilisant un chemin relatif, remonter sur `etc`
```
$cd .. 
```

6. Afficher les fichiers du répertoire courant
```
$ls
```

PackageKit              fstab           mime.types           sensors.d
X11                     fuse.conf       mke2fs.conf          sensors3.conf
adduser.conf            gai.conf        modprobe.d           services
alternatives            glvnd           modules              sgml
apparmor                gnutls          modules-load.d       shadow
apparmor.d              gprofng.rc      mtab                 shadow-
apport                  groff           nanorc               shells
apt                     group           netconfig            skel
bash.bashrc             group-          netplan              ssh
bash_completion         gshadow         networkd-dispatcher  ssl
bash_completion.d       gshadow-        networks             subgid
bindresvport.blacklist  gss             newt                 subgid-
binfmt.d                gtk-3.0         nsswitch.conf        subuid
byobu                   host.conf       opt                  subuid-
ca-certificates         hostname        os-release           sudo.conf
ca-certificates.conf    hosts           pam.conf             sudo_logsrvd.conf
cloud                   init.d          pam.d                sudoers
console-setup           inputrc         passwd               sudoers.d
credstore               iproute2        passwd-              supercat
credstore.encrypted     issue           perl                 sysctl.conf
cron.d                  issue.net       pm                   sysctl.d
cron.daily              kernel          polkit-1             systemd
cron.hourly             landscape       profile              terminfo
cron.monthly            ld.so.cache     profile.d            timezone
cron.weekly             ld.so.conf      protocols            tmpfiles.d
cron.yearly             ld.so.conf.d    python3              ubuntu-advantage
crontab                 ldap            python3.12           ucf.conf
dbus-1                  legal           rc0.d                udev
dconf                   libaudit.conf   rc1.d                update-manager
debconf.conf            locale.alias    rc2.d                update-motd.d
debian_version          locale.conf     rc3.d                vconsole.conf
default                 locale.gen      rc4.d                vim
deluser.conf            localtime       rc5.d                vtrgb
depmod.d                logcheck        rc6.d                vulkan
dhcp                    login.defs      rcS.d                wgetrc
dhcpcd.conf             logrotate.conf  resolv.conf          wsl.conf
dpkg                    logrotate.d     rmt                  xattr.conf
e2scrub.conf            lsb-release     rpc                  xdg
environment             machine-id      rsyslog.conf         xml
environment.d           magic           rsyslog.d            zsh_command_not_found
ethertypes              magic.mime      security
fonts                   manpath.config  selinux

7. Même chose en « affichage détaillé »
```
$ls -l
```

total 788
drwxr-xr-x 2 root root       4096 Jan  6 21:15 PackageKit
drwxr-xr-x 7 root root       4096 Jan  6 21:15 X11
-rw-r--r-- 1 root root       3444 Jul  5  2023 adduser.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:15 alternatives
drwxr-xr-x 2 root root       4096 Jan  6 21:15 apparmor
drwxr-xr-x 9 root root       4096 Jan  6 21:15 apparmor.d
drwxr-xr-x 3 root root       4096 Jan  6 21:15 apport
drwxr-xr-x 8 root root       4096 Jan  6 21:15 apt
-rw-r--r-- 1 root root       2319 Mar 31  2024 bash.bashrc
-rw-r--r-- 1 root root         45 Jan 24  2020 bash_completion
drwxr-xr-x 2 root root       4096 Jan  6 21:15 bash_completion.d
-rw-r--r-- 1 root root        367 Aug  2  2022 bindresvport.blacklist
drwxr-xr-x 2 root root       4096 Apr 19  2024 binfmt.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 byobu
drwxr-xr-x 3 root root       4096 Jan  6 21:14 ca-certificates
-rw-r--r-- 1 root root       6288 Jan  6 21:14 ca-certificates.conf
drwxr-xr-x 5 root root       4096 Jan  6 21:15 cloud
drwxr-xr-x 2 root root       4096 Jan  6 21:14 console-setup
drwx------ 2 root root       4096 Apr 19  2024 credstore
drwx------ 2 root root       4096 Apr 19  2024 credstore.encrypted
drwxr-xr-x 2 root root       4096 Jan  6 21:14 cron.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 cron.daily
drwxr-xr-x 2 root root       4096 Jan  6 21:14 cron.hourly
drwxr-xr-x 2 root root       4096 Jan  6 21:14 cron.monthly
drwxr-xr-x 2 root root       4096 Jan  6 21:15 cron.weekly
drwxr-xr-x 2 root root       4096 Jan  6 21:14 cron.yearly
-rw-r--r-- 1 root root       1136 Mar 31  2024 crontab
drwxr-xr-x 4 root root       4096 Jan  6 21:14 dbus-1
drwxr-xr-x 3 root root       4096 Jan  6 21:15 dconf
-rw-r--r-- 1 root root       2967 Apr 12  2024 debconf.conf
-rw-r--r-- 1 root root         11 Apr 22  2024 debian_version
drwxr-xr-x 2 root root       4096 Jan  6 21:15 default
-rw-r--r-- 1 root root       1706 Jul  5  2023 deluser.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:14 depmod.d
drwxr-xr-x 3 root root       4096 Jan  6 21:14 dhcp
-rw-r--r-- 1 root root       1429 Mar 31  2024 dhcpcd.conf
drwxr-xr-x 4 root root       4096 Jan  6 21:14 dpkg
-rw-r--r-- 1 root root        685 Apr  8  2024 e2scrub.conf
-rw-r--r-- 1 root root        106 Jan  6 21:13 environment
drwxr-xr-x 2 root root       4096 Jan  6 21:15 environment.d
-rw-r--r-- 1 root root       1853 Oct 18  2022 ethertypes
drwxr-xr-x 4 root root       4096 Jan  6 21:15 fonts
-rw-r--r-- 1 root root         37 Jan  6 21:13 fstab
-rw-r--r-- 1 root root        694 Apr  8  2024 fuse.conf
-rw-r--r-- 1 root root       2584 Jan 31  2024 gai.conf
drwxr-xr-x 3 root root       4096 Jan  6 21:15 glvnd
drwxr-xr-x 2 root root       4096 Jan  6 21:14 gnutls
-rw-r--r-- 1 root root       3986 Aug  7 12:15 gprofng.rc
drwxr-xr-x 2 root root       4096 Jan  6 21:15 groff
-rw-r--r-- 1 root root        795 Jan 16 11:20 group
-rw-r--r-- 1 root root        734 Jan 16 11:20 group-
-rw-r----- 1 root shadow      680 Jan 16 11:20 gshadow
-rw-r----- 1 root shadow      619 Jan 16 11:20 gshadow-
drwxr-xr-x 3 root root       4096 Jan  6 21:14 gss
drwxr-xr-x 2 root root       4096 Jan  6 21:15 gtk-3.0
-rw-r--r-- 1 root root         92 Apr 22  2024 host.conf
-rw-r--r-- 1 root root         16 Jan 16 11:20 hostname
-rw-r--r-- 1 root root        416 Jan 16 11:20 hosts
drwxr-xr-x 2 root root       4096 Jan  6 21:15 init.d
-rw-r--r-- 1 root root       1875 Mar 31  2024 inputrc
drwxr-xr-x 4 root root       4096 Jan  6 21:14 iproute2
-rw-r--r-- 1 root root         26 Aug 23 16:20 issue
-rw-r--r-- 1 root root         19 Aug 23 16:20 issue.net
drwxr-xr-x 4 root root       4096 Jan  6 21:14 kernel
drwxrwxr-x 2 root landscape  4096 Jan  6 21:15 landscape
-rw-r--r-- 1 root root      17607 Jan 16 11:20 ld.so.cache
-rw-r--r-- 1 root root         34 Aug  2  2022 ld.so.conf
drwxr-xr-x 2 root root       4096 Jan 16 11:19 ld.so.conf.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 ldap
-rw-r--r-- 1 root root        267 Apr 22  2024 legal
-rw-r--r-- 1 root root        191 Mar 31  2024 libaudit.conf
-rw-r--r-- 1 root root       2996 Mar 30  2024 locale.alias
-rw-r--r-- 1 root root         13 Jan  6 21:14 locale.conf
-rw-r--r-- 1 root root       9565 Jan  6 21:14 locale.gen
lrwxrwxrwx 1 root root         32 Jan 16 11:20 localtime -> /usr/share/zoneinfo/Europe/Paris
drwxr-xr-x 3 root root       4096 Jan  6 21:14 logcheck
-rw-r--r-- 1 root root      12345 Feb 22  2024 login.defs
-rw-r--r-- 1 root root        586 Apr  8  2024 logrotate.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:15 logrotate.d
-rw-r--r-- 1 root root        104 Aug 23 16:20 lsb-release
-r--r--r-- 1 root root         33 Jan 16 11:19 machine-id
-rw-r--r-- 1 root root        111 Mar 31  2024 magic
-rw-r--r-- 1 root root        111 Mar 31  2024 magic.mime
-rw-r--r-- 1 root root       5230 Apr  8  2024 manpath.config
-rw-r--r-- 1 root root      75113 Jul 12  2023 mime.types
-rw-r--r-- 1 root root        744 Apr  8  2024 mke2fs.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:14 modprobe.d
-rw-r--r-- 1 root root        212 Jan  6 21:14 modules
drwxr-xr-x 2 root root       4096 Jan  6 21:14 modules-load.d
lrwxrwxrwx 1 root root         19 Jan  6 21:14 mtab -> ../proc/self/mounts
-rw-r--r-- 1 root root      11424 May 23  2023 nanorc
-rw-r--r-- 1 root root        767 Mar 31  2024 netconfig
drwxr-xr-x 2 root root       4096 Apr 18  2024 netplan
drwxr-xr-x 8 root root       4096 Jan  6 21:14 networkd-dispatcher
-rw-r--r-- 1 root root         91 Apr 22  2024 networks
drwxr-xr-x 2 root root       4096 Jan  6 21:14 newt
-rw-r--r-- 1 root root        526 Jan  6 21:14 nsswitch.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:13 opt
lrwxrwxrwx 1 root root         21 Aug 23 16:20 os-release -> ../usr/lib/os-release
-rw-r--r-- 1 root root        552 Oct 13  2022 pam.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:14 pam.d
-rw-r--r-- 1 root root       1426 Jan 16 11:20 passwd
-rw-r--r-- 1 root root       1423 Jan 16 11:20 passwd-
drwxr-xr-x 3 root root       4096 Jan  6 21:14 perl
drwxr-xr-x 3 root root       4096 Jan  6 21:15 pm
drwxr-xr-x 3 root root       4096 Jan  6 21:15 polkit-1
-rw-r--r-- 1 root root        582 Apr 22  2024 profile
drwxr-xr-x 2 root root       4096 Jan  6 21:15 profile.d
-rw-r--r-- 1 root root       3144 Oct 18  2022 protocols
drwxr-xr-x 2 root root       4096 Jan  6 21:14 python3
drwxr-xr-x 2 root root       4096 Jan  6 21:14 python3.12
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc0.d
drwxr-xr-x 2 root root       4096 Jan  6 21:14 rc1.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc2.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc3.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc4.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc5.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rc6.d
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rcS.d
lrwxrwxrwx 1 root root         20 Jan 16 11:20 resolv.conf -> /mnt/wsl/resolv.conf
lrwxrwxrwx 1 root root         13 Apr  8  2024 rmt -> /usr/sbin/rmt
-rw-r--r-- 1 root root        911 Oct 18  2022 rpc
-rw-r--r-- 1 root root       1213 Mar 22  2024 rsyslog.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:15 rsyslog.d
drwxr-xr-x 4 root root       4096 Jan  6 21:14 security
drwxr-xr-x 2 root root       4096 Jan  6 21:13 selinux
drwxr-xr-x 2 root root       4096 Jan  6 21:15 sensors.d
-rw-r--r-- 1 root root      10593 Mar 31  2024 sensors3.conf
-rw-r--r-- 1 root root      12813 Mar 27  2021 services
drwxr-xr-x 2 root root       4096 Jan  6 21:15 sgml
-rw-r----- 1 root shadow      802 Jan 16 11:20 shadow
-rw-r----- 1 root shadow      702 Jan  6 21:15 shadow-
-rw-r--r-- 1 root root        132 Jan  6 21:15 shells
drwxr-xr-x 2 root root       4096 Jan  6 21:13 skel
drwxr-xr-x 3 root root       4096 Jan  6 21:15 ssh
drwxr-xr-x 4 root root       4096 Jan  6 21:14 ssl
-rw-r--r-- 1 root root         20 Jan 16 11:20 subgid
-rw-r--r-- 1 root root          0 Jan  6 21:13 subgid-
-rw-r--r-- 1 root root         20 Jan 16 11:20 subuid
-rw-r--r-- 1 root root          0 Jan  6 21:13 subuid-
-rw-r--r-- 1 root root       4343 Apr  8  2024 sudo.conf
-rw-r--r-- 1 root root       9804 Apr  8  2024 sudo_logsrvd.conf
-r--r----- 1 root root       1800 Jan 29  2024 sudoers
drwxr-xr-x 2 root root       4096 Jan  6 21:14 sudoers.d
drwxr-xr-x 2 root root       4096 Jan  6 21:14 supercat
-rw-r--r-- 1 root root       2209 Mar 24  2024 sysctl.conf
drwxr-xr-x 2 root root       4096 Jan  6 21:14 sysctl.d
drwxr-xr-x 6 root root       4096 Jan  6 21:14 systemd
drwxr-xr-x 2 root root       4096 Jan  6 21:13 terminfo
-rw-r--r-- 1 root root         13 Jan 16 11:20 timezone
drwxr-xr-x 2 root root       4096 Apr 19  2024 tmpfiles.d
drwxr-xr-x 2 root root       4096 Jan  6 21:14 ubuntu-advantage
-rw-r--r-- 1 root root       1260 Jan 27  2023 ucf.conf
drwxr-xr-x 4 root root       4096 Jan  6 21:14 udev
drwxr-xr-x 3 root root       4096 Jan  6 21:16 update-manager
drwxr-xr-x 2 root root       4096 Jan  6 21:15 update-motd.d
lrwxrwxrwx 1 root root         16 Jan  6 21:14 vconsole.conf -> default/keyboard
drwxr-xr-x 2 root root       4096 Jan  6 21:14 vim
lrwxrwxrwx 1 root root         23 Feb 26  2024 vtrgb -> /etc/alternatives/vtrgb
drwxr-xr-x 5 root root       4096 Jan  6 21:15 vulkan
-rw-r--r-- 1 root root       4942 Jun 19  2024 wgetrc
-rw-r--r-- 1 root root         20 Jan  6 21:15 wsl.conf
-rw-r--r-- 1 root root        681 Apr  8  2024 xattr.conf
drwxr-xr-x 5 root root       4096 Jan  6 21:15 xdg
drwxr-xr-x 2 root root       4096 Jan  6 21:15 xml
-rw-r--r-- 1 root root        460 Jan 20  2023 zsh_command_not_found


8. Afficher tous les fichiers du répertoire courant qui commencent par `s`
```
$ls s*
```

sensors3.conf  shadow   shells  subgid-  subuid-    sudo_logsrvd.conf  sysctl.conf
services       shadow-  subgid  subuid   sudo.conf  sudoers

security:
access.conf      group.conf   namespace.conf  opasswd         sepermit.conf
capability.conf  limits.conf  namespace.d     pam_env.conf    time.conf
faillock.conf    limits.d     namespace.init  pwhistory.conf

selinux:
semanage.conf

sensors.d:

sgml:
catalog  xml-core.cat

skel:

ssh:
ssh_config  ssh_config.d

ssl:
certs  openssl.cnf  private

sudoers.d:
README

supercat:
spcrc-crontab  spcrc-crontab-light

sysctl.d:
10-bufferbloat.conf       10-magic-sysrq.conf       10-zeropage.conf
10-console-messages.conf  10-map-count.conf         99-sysctl.conf
10-ipv6-privacy.conf      10-network-security.conf  README.sysctl
10-kernel-hardening.conf  10-ptrace.conf

systemd:
journald.conf  networkd.conf  sleep.conf         system.conf     user.conf
logind.conf    pstore.conf    system             timesyncd.conf
network        resolved.conf  system-generators  user


9. Lancer la commande qui permet de déterminer le type de contenu dans le fichier `/etc/group`
```
$file /etc/group
```
/etc/group: ASCII text


10. Afficher les cinq dernières lignes du fichier `/etc/group`
```
$tail -n 5 /etc/group
```

landscape:x:105:
polkitd:x:990:
admin:x:106:
netdev:x:107:nassim
nassim:x:1000:

11. Exécuter la commande qui revient directement à votre répertoire personnel
```
$cd
```

12. Créer un répertoire nommé `temp` dans votre répertoire personnel
```
$mkdir temp
```

13. Copier le fichier `/etc/passwd` dans le répertoire `temp`
```
$cp /etc/passwd /temp
```
14. Copier le répertoire `/etc/ppp` dans le répertoire courant (ignorer toutes les erreurs "permission denied") (utiliser un autre répertoire pas trop « gros », comme `/etc/ssh`, si `/etc/ppp` n'est pas sur votre système)
```
$sudo cp -r /etc/ssh /home/nassim
```

15. Renommer le répertoire `ppp` du répertoire courant en `peers`
```
$mv ssh/ peers/
```

16. Mettre à jour le timestamp du fichier `temp/passwd` à la date et heure courantes
```
$touch temp/passwd
```

17. Créer un nouveau fichier vide nommé `test` dans le répertoire `temp`
```
$touch test
```

18. Supprimer le fichier `temp/passwd`
```
$rm passwd
```

19. Supprimer le répertoire `peers`
rm -r /home/nassim/peers

### 2. Fonctionnalités du Shell

1. Afficher le contenu de la variable `HOME`
2. Afficher toutes les variables shell avec leur contenu
3. Afficher le contenu de la variable `TEST` (noter que cette variable n'a en fait aucun contenu actuellement)
4. Changer le shell courant afin qu'un message d'erreur s'affiche quand une variable indéfinie est utilisée
5. Modifier la variable `PATH` pour ajouter le répertoire `/opt`
6. Créer une variable d'environnement appelée `EVENT` et lui donner la valeur "maintenant" en utilisant une seule commande
7. Afficher toutes les variables d'environnement
8. Créer un alias dans le shell courant pour la commande `ls` de telle sorte que ça lance la commande `ls -a`
9. Afficher tous les alias du shell courant
10. Supprimer l'alias défini en 8 du shell courant
11. Afficher une liste des commandes précédemment exécutées
12. Re-exécuter la dernière commande `ls` de l'historique
13. Changer le nombre maximum de commandes stockées dans l'historique du shell courant (2000)
14. Exécuter la commande `ps -ef` et utiliser un *pipe* pour passer la sortie à la commande `less`
15. Afficher tous les fichiers dans la structure du répertoire `etc` (sous-répertoires inclus) dont le groupe propriétaire est le groupe `lp` (ou n'importe quel autre groupe existant si le groupe `lp` n'existe pas sur votre système)
16. Afficher tous les lignes dans le fichier `etc/passwd` qui contiennent au moins trois nombres d'affilé
17. Afficher le fichier `etc/passwd` avec toutes les occurrences de `root` remplacées par `XXXX`

### 3. Compression

1. En utilisant l'option « verbose », créer un fichier tar appelé `etcppp.tar` qui contient le contenu du répertoire `etc/ppp` (ignorer les messages d'erreurs potentiels)
2. Afficher le contenu de l'archive `etcppp.tar` (sans l'extraire)
3. Créer un répertoire `extraction-tar` dans le répertoire courant
4. Extraire le contenu de l'archive `etcppp.tar` dans le répertoire `extraction-tar`
5. Compresser l'archive `etcppp.tar` en utilisant la commande `gzip`, sans écraser le fichier `etcppp.tar` ; le fichier résultant devra se nommer `etcppp.tar.gz`
6. Compresser l'archive `etcppp.tar` en utilisant la commande `bzip2`, sans écraser ; le fichier résultant devra se nommer `etcppp.tar.bz2`
7. Comparer les tailles des deux fichiers compressés (`.gzip` et `.bz2`) ; lequel des deux algorithmes semble avoir un meilleur taux de compression ?
8. Supprimer le fichier `etcppp.tar`
9. Décompresser le fichier `etcppp.tar.gz`

### 4. Obtenir de l'aide

- `man` et ses options (pour les commandes générales et les fichiers de configuration), `help` (pour les commandes shell seulement, comme `cd`), `whatis`, `info`
- Sur n'importe quelle commande, souvent une option `--help` (parfois `-h`) pour une aide plus brève

### 5. Identifier et résoudre les problèmes liés à une commande

Étapes générales de résolution d'un problème (valable au-delà des problèmes de commandes systèmes) :

- **Réunir des informations** : lire les messages d'erreurs, essayer une autre commande basique sur le même fichier (problème d'existence/d'accès ?)
- **Déterminer la cause probable** : utiliser `--help` ou `man/info`, internet (notamment, faire une recherche sur le message d'erreur spécifique), un ami/collègue, voire l'admin système (en fournissant les détails)...
- **S'assurer que toutes les actions sont documentées** : en a-t-on compris suffisamment et a-t-on tout ce qu'il faut pour aller à la fin de la procédure ? Pourra-ton « défaire » chaque étape si ça ne fonctionne pas ?
- **Effectuer les actions** : s'assurer que chaque action produit le résultat intermédiaire attendu avant de poursuivre ; toute la procédure tombe par terre sinon, et il pourra être difficile de « défaire » si on ne sait pas ce qui a été « fait »
- **Vérifier que le problème est résolu** : si ce n'est pas le cas, faut-il « défaire » ce qui a été essayé auparavant ? Souvent oui, car ces actions pourraient interférer avec une nouvelle solution potentielle et/ou créer des problèmes futurs
- **Vérifier, dans la mesure du possible, qu'il n'y a pas d'autres problèmes** : parfois un *fix* d'un problème cause d'autres problèmes d'une ampleur encore plus importante (problème d'accès d'un utilisateur ? => on édite en root un fichier de configuration pour accorder les droits => on ferme par la même les droits d'autres utilisateurs, ou bien on introduit un problème de sécurité...)
- **Prendre note de la solution** : trouvez un système qui vous permet de documenter les solutions qui ont fonctionné pour un problème donné. Se dire « c'est bon, je m'en souviendrai » *ne fonctionne quasiment jamais* pour un problème au-delà du trivial. Utilisez plutôt un outil numérique qui permettra des recherches aisées, des copier/coller de lignes de commandes, un système de tags, etc.

1. Essayer d'exécuter la commande `ls /var/logs`
2. La commande précédente échoue. Lire le message d'erreur et expliquer pourquoi
3. Quelle commande pourrait-on exécuter pour déterminer le nom correct du répertoire de logs ?
4. Exécuter la commande correcte
5. Essayer `head -N 7 /etc/passwd`
6. Marche pas. Quelle commande peut-on exécuter pour connaître la bonne option ?
7. Exécuter la commande correcte
8. Essayer `cp /etc/passwd /var`
9. Boum. Que se passe-t-il ?
10. Comment ferait-on pour effectivement travailler sur une copie du fichier ?

### 6. Configurer les comptes groupes

(L'importance des comptes utilisateurs et groupes en termes de sécurité ne peut pas être suffisamment soulignée)

- Notions : ajouter/modifier/supprimer des groupes ; ajouter/supprimer un utilisateur à un groupe ; groupe primaire / groupes secondaires d'un utilisateur
- Typiquement, on va créer un groupe pour chaque service, un groupe pour un projet sur lequel travaillent plusieurs personnes (potentiellement pas du même service), un groupe pour les différents titres (ingénieurs, managers, etc.) ; cela permettra une gestion individuelle des permissions sur chaque groupe
- Commandes : `id, groups, chgrp, newgrp, grpadd, groupmod, groupdel, usermod, gpasswd`
- Fichiers : `/etc/group`, `/etc/gshadow`

1. Afficher l'ID de l'utilisateur courant et ses groupes
2. Afficher les groupes du compte root. Quel est son groupe primaire ? Quels sont ses groupes secondaires ?
3. Rechercher la ligne concernant le groupe `adm` dans `etc/group` ; explicitez les informations données sur cette ligne
4. Déterminer le propriétaire et le groupe propriétaire du fichier `/etc/group`
5. Afficher les informations du compte groupe `games` (ou un autre groupe quelconque si votre système ne définit pas le groupe `games`)
6. Afficher, pour le compte groupe `games`, la ligne d'informations issue du fichier `/etc/passwd`
7. Exécuter `su -` (différence avec `su` ?)
8. Créer un nouveau groupe `test`
9. Afficher les informations du compte groupe `test`
10. Changer le nom en `grouptest`
11. Ajouter votre compte utilisateur personnel en tant que second membre du groupe `grouptest` *sans écraser vos autres groupes actuels* (trouvez l'option avant d'exécuter la commande)
12. Expliquez ce que fait la commande `find / -group grouptest -exec chgrp compta {} \;`
13. Supprimer le groupe `grouptest`
14. Répondez à la question suivante de l'un de vos utilisateurs : « Je veux créer des fichiers qui auront pour groupe propriétaire le groupe `projet-x`. Comment je fais pour changer temporairement mon groupe primaire pour que les fichiers soient créés avec le bon groupe ? »

### 7. Configurer un administrateur de groupe

Créez un utilisateur `dummy`. Créez un nouveau groupe `supports` et ajoutez-y l'utilisateur `dummy`. Faites de `dummy` un administrateur du groupe. Confirmez ce nouveau statut en examinant `/etc/gshadow`. Pour tester, loggez-vous en tant que `dummy` et ajoutez l'utilisateur `bin` au groupe `supports` (vous devriez alors pouvoir le faire sans `sudo`) puis affichez les groupes de `bin`.

### 8. Configurer les comptes utilisateurs

- Notions : ajouter/modifier/supprimer des utilisateurs, permissions utilisateurs
- Commandes : `useradd, passwd`
- Fichiers : `/etc/passwd, /etc/shadow, /etc/group, /etc/gshadow`

1. Afficher les informations du compte `bin` (y compris le shell et le répertoire utilisateur)
2. Afficher les informations de mot de passe de votre compte (y compris le mot de passe haché)
3. Créer un utilisateur `nadine` en spécifiant explicitement la création du répertoire utilisateur (sinon ce répertoire n'est pas forcément créé)
4. Appliquer un mot de passe fort pour `nadine` : `couscousavecdesmerguezdanstaface`
5. Afficher les valeurs par défaut utilisées lorsqu'un nouveau compte est créé
6. Afficher le fichier qui contient les informations de temps d'expiration par défaut pour les mots de passe
7. Afficher le fichier qui contient les informations sur le shell par défaut
8. Supprimer le compte `nadine` ainsi que son répertoire utilisateur (en une seule commande)
