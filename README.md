dwm-clean-patches
=================

*The following description needs to be updated to comply with git!*

This repository contains a selection of patches for different versions
of dwm. For every version of dwm there is a directory. Every directory
contains with the changeset id as its name. Below this directory the
patches are stored, together with a detailed README file.

The two scripts `clean.mk` and `clean.sh` are used for creating clean
patches.

Check out the dwm-patches repository:
$ hg qclone https://bitbucket.org/jceb81/dwm-patches
$ cd dwm-patches

Check out the dwm-clean-patches repository:
$ hg clone https://bitbucket.org/jceb81/dwm-clean-patches

Create symlinks to `clean.mk` and `clean.sh`:
$ ln -s dwm-clean-patches/clean.* .

Update all patches from the dwm-patches repository to apply cleanly
against the tip of the dwm repository.:
$ make -f clean.mk

Certainly errors will occur when running the above command. Fix the
error an run:
$ hg refresh

Continue updating patches till all apply cleanly:
$ make -f clean.mk

Specific patches can be updated by passing them as arguments:
$ make -f clean.mk args="patches"

Finally upload the resulting directory containing only patches that
apply cleanly against the tip of the dwm repository.
$ cp -r $VERSION dwm-clean-patches/

Don't forget to revert the changes you did to the patches of the
dwm-patches repository:
$ cd .hg/patches
$ hg revert *
$ rm *.orig
