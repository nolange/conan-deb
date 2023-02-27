# What and why

This is a relative "proper" packaging for [conan](https://conan.io/),
reason being that so far the only options are to either use a prepared
debian package that might cause issues and seems pretty much
not a well supported variant.

Or to build via python pip which is a bit too much if you
just want to use the application.

This variant will use already packaged libraries from debian,
where available. Thats keeping the installation both small and
the library versions are mainted/checked by debian.

The ugly:

-   python-patch-ng is only in unstable, so it wont be available
    until debian 12 is out.

# How:

Download conans sourced, unpack them and add the `debian` directory
(next to `setup.py`).
Cd into the directory containing `setup.py`, and run

```bash
dpkg-buildpackage
```
Install the missing packages, you will likely have to manually
find and install [python3-patch-ng](https://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=python3-patch-ng).

Run `dpkg-buildpackage` again.

Optionally you can run `dpkg-buildpackage -S -d` to get a source package,
and then use `sbuild` but I wont detail those steps.

