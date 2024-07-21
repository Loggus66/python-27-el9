# python-27-el9
Python 2 for EL9, rebuilt from the EL8 SRPM.

Built on Oracle Linux, should be a drop-in for any EL9 fork (Rocky, Alma, RHEL etc).

Built with the "rpmbuild -bb --without rpmwheels --without tests python2.spec" command (subject to change)

Failing tests are

test_minidom, test_xml_etree, test_xml_etree_c

Likely due to the expat library v2.5.0 as described here: https://www.linuxfromscratch.org/~ken/inkscape-python-deps/blfs-book-sysv/general/python2.html

BuildRequires openssl11-devel, unlike in the original .spec, I am including these too. It's basically openssl-1.1.1k from EL8 but with the modified name and several other changes in patches and the unix Makefile because I had to make sure openssl-libs, openssl-devel (this is the required one) and their configs install fine alongside the system openssl-libs v3, which is the systemd dependency. IIRC SSL-related tests don't fail for Python2 but I haven't done any further testing on this.

SRPMs links that I based my versions on are:

https://yum.oracle.com/repo/OracleLinux/OL8/baseos/latest/x86_64/getPackageSource/openssl-1.1.1k-9.el8_7.src.rpm

https://yum.oracle.com/repo/OracleLinux/OL8/appstream/x86_64/getPackageSource/python2-2.7.18-7.0.1.module+el8.5.0+20361+8a9d3d27.src.rpm

