# Script per donar la benvinguda al nostre servidor

Tant bon punt s'inicia una sessió en el servidor, rebem aquest missatge de benvinguda.

```bash
login as: joanpardo
joanpardo@192.168.154.128's password: *********

Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-131-generic ...

 * Documentation: https://help.ubuntu.com
 * Management: https://landscape.canonical.com
 * Support: https://ubuntu.com/advantage

186 packages can be updated.
129 updates are security updates.

New release '18.04.4 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Thu Dec 12 15:11:12 2019 from 192.168.154.1
joanpardo@ubuntu:~$
```

Aquest missatge és el resultat de l'execució del primer (**```00-header```**), d'un seguit d'**```scripts```** que es troben a **```/etc/update-motd.d/```**.

El contingut de l'**```script```** original **```00-header```** és el següent:
```bash
#!/bin/sh
#
#    00-header - create the header of the MOTD
#    Copyright (c) 2013 Nick Charlton
#    Copyright (c) 2009-2010 Canonical Ltd.
#
#    Authors: Nick Charlton <hello@nickcharlton.net>
#             Dustin Kirkland <kirkland@canonical.com>
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License along
#    with this program; if not, write to the Free Software Foundation, Inc.,
#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

[ -r /etc/lsb-release ] && . /etc/lsb-release

if [ -z "$DISTRIB_DESCRIPTION" ] && [ -x /usr/bin/lsb_release ]; then
        # Fall back to using the very slow lsb_release utility
        DISTRIB_DESCRIPTION=$(lsb_release -s -d)
fi

figlet $(hostname)
printf "\n"

printf "Welcome to %s (%s).\n" "$DISTRIB_DESCRIPTION" "$(uname -r)"
printf "\n"
```

I una de les posibles solucions a la practica la podeu trobar al següent enllaç [00-header](/00-header).
