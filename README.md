# Apache HTTPD 2.4 "ServerTokens Off" Patch

Forked from this upstream repo: https://github.com/Bill-SD/Apache-HTTP-Server-Patch-ServerTokensOff

This repo updates the patch for the newest httpd 2.4 releases and also includes a specfile for building RPMs from the sources provided by the IUS repo: https://ius.io

### Prerequisites

You'll need the EPEL and IUS repos enabled. The following packages are required to properly build an RPM:
```
epel-rpm-macros rpmdevtools brotli-devel openssl-devel keyutils-libs-devel lua-devel zlib-devel openldap-devel libcom_err-devel pcre-devel krb5-devel apr15u-util-devel xz-devel expat-devel libdb-devel libxml2-devel libnghttp2-devel systemd-devel libsepol-devel apr15u-devel cyrus-sasl-devel libverto-devel libselinux-devel glibc-devel
```

### Build Steps

```
$ rpmdev-setuptree
$ rpm -i https://repo.ius.io/7/src/packages/h/httpd24u-2.4.39-2.el7.ius.src.rpm
$ cp httpd-2.4.39.ServerTokensOff.patch rpmbuild/SOURCES/
$ patch -p0 < httpd24u.spec.patch
$ rpmbuild -bb rpmbuild/SPECS/httpd24u.spec
```

### How To Use

Edit your httpd.conf and set:
```
ServerTokens Off
```

Run curl against your site to verify absence of the "Server:" header.

Congratulations, you are now more secure through obscurity and your ISSO is pleased.

