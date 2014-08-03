FROM base/archlinux

MAINTAINER Spencer Rinehart <anubis@overthemonkey.com>

COPY php/php-5.4.0-1-x86_64.pkg.tar.xz /tmp/php-5.4.0-1-x86_64.pkg.tar.xz

RUN pacman --upgrade --noconfirm --noprogressbar /tmp/php-5.4.0-1-x86_64.pkg.tar.xz

# Remove packages that aren't used at all
#RUN pacman --remove --noconfirm cronie dbus device-mapper dhcpcd diffutils file gettext glib2 grep gzip hwids inetutils iptables iproute2 iputils kbd kmod less libdbus libffi libseccomp libsystemd libunistring libusb licenses logrotate nano netctl openresolv popt procps-ng psmisc shadow sysfsutils systemd systemd-sysvcompat tar texinfo usbutils util-linux vi which

# Remove packages that aren't needed for PHP
#RUN sed -i 's/^HoldPkg.*/#\0/' /etc/pacman.conf
#RUN pacman --remove --noconfirm --nodeps --nodeps --nosave acl archlinux-keyring attr bash bzip2 ca-certificates coreutils cracklib curl db dirmngr e2fsprogs expat findutils gawk gdbm gmp gnupg gpgme iana-etc keyutils krb5 libarchive libassuan libcap libgcrypt libgpg-error libksba libldap libsasl libssh2 libtirpc libutil-linux linux-api-headers lzo2 mpfr ncurses openssl pacman pacman-mirrorlist pam pambase perl pinentry pth readline run-parts sed tzdata xz zlib

#RUN rm -fr /opt /srv /var /usr/local /usr/share /usr/include /usr/src /tmp/php-5.4.0-1-x86_64.pkg.tar.xz

ADD php.ini /etc/php/php.ini

CMD ["php"]
