## OpenSceneGraph Gitbuildpackage (GBP) Repository ##

This repository packages OpenSceneGraph into a buildable debian package.
It also includes modifications to fix support for virtual machines on Mac hosts.

**Initialize cowbuilder:**
```bash
$ sudo apt-get install cowbuilder
$ DIST=trusty sudo cowbuilder --create --distribution trusty --components "main universe"
```
**Build debian package:**
```bash
$ git clone https://github.com/mkoval/openscenegraph-release.git
$ cd openrave-release
$ gbp buildpackage --git-pbuilder -uc -us
```
### Advanced Usage ###

**Update existing cowbuilder instance:**
```bash
$ sudo cowbuilder --update
```
**Import new upstream source:**
```bash
$ curl -L https://api.github.com/repos/openscenegraph/osg/tarball/master > master.tar.gz
$ git clone https://github.com/mkoval/openscenegraph-release.git
$ cd openscenegraph-release
$ gbp import-orig --pristine-tar ../master.tar.gz
    What is the upstream version? [] <enter version higher than the previous>
$ gbp dch --release
$ git commit -m "Updated changelog for version <your version>."
$ gbp buildpackage --git-pbuilder -uc -us
```
