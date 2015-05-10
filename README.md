# openntpd.tcz
OpenNTPD package for Tiny Core Linux

This repository contains the sources for OpenNTPD Portable extension for Tiny Core Linux, including scripts and configuration files, but not the openntpd binary (only the packaged TCZ and the Appliance contains it).

Why? Because I need a lithweight NTP server, and the Busybox ntpd have known issues.

Compiling OpenNTPD portable statically (be sure to have a recent GCC i386 aor multilib support):

$ git clone https://github.com/openntpd-portable/openntpd-portable.git
$ cd openntpd-portable
$ ./configure CFLAGS=-m32 LDFLAGS="-m32 -static -static-libgcc -static-libstdc++" --build=i386-linux-gnu --host=i386-linux-gnu --target=i386-linux-gnu --without-crypto --prefix=$HOME/ntp --exec-prefix=$HOME/ntp/usr
$ make
$ make install

This will install openntpd in your personal folder. Copy just the ntpd binary to the correspondient directory, and thename it to "openntpd" (to avoid confussion to the busybox ntpd).

To build the TCZ package, just run mksquashfs and name the oputut file to "openntpd.tcz"
