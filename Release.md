---
layout: default
title: ReleaseProcess
---

# Release Process

## Prepare
* Create buildsys-build-rpmfusion for GA kernel

* (Generate the free/nonfree keys for Fedora N+2) not anymore

* Update the new gpg key to the wiki keys

* Publish the new gpg keys to the mock repository


## Release
* Create rpmfusion-free-release/rpmfusion-nonfree-release for Final
 * Verify base/updates repo is enabled, rawhide/updates-testing disabled
 * Verify that the metadata expire is set to 7days

* Push last packages (rpmfusion-free/nonfree-release)

* Tag (rpmfusion-free/nonfree-release) also in f32-*-updates-testing for transition (keep it there two weeks)

* Mash with repoview repo name changed( branch/release)

* Move the resulting repo from development/32 to releases/32
 * Create the symlink (cp -lr) to point to releases/32 from development/f32 (free/nonfree)
 * Create the symlink (ln -s) for rpmfusion-*-release-32.rpm to releases/32/os/../x86_64/rpmfusion*.rpm
 * Create an empty updates repos

*  Modify the push script to move packages into updates instead of f32-free

* Lock tags: koji-rpmfusion lock-tag  --master f32-free

* Add fedora updates repository to the just release tag

* Update the koji external repos tag to point to fedora releases

## Post GA
* Update wiki:
 *  Update the frontpage Wiki.
 *  Update Configuration Wiki page.
 *  Update Keys Wiki page. (Reference the new gpg keys in the wiki.) 
* Update mock-rpmfusion (the mock configurations fo rpmfusion).
* Check if rfpkg is working (python version compatibility, etc)
* Check if mirrors are updated i.e if mirrormanager was updated by Adrian. 
  This script can help out https://github.com/sergiomb2/rpmfusion_check/blob/master/check_mirrors.sh
* check if CommonBugs - RPM Fusion needs updates
* update bugzilla component version
* Prepare a "RPM Fusion is ready for F X" announcement mail 

## Post RPMFusion branched
* update wiki:
 * Update the frontpage Wiki.
 * Update Configuration Wiki page.
 * Update Keys Wiki page. (Reference the new gpg keys in the wiki.) 
* Update mock-rpmfusion (the mock configurations fo rpmfusion).
* Check if mirrors are updated i.e. if mirrormanager doesn't miss last stable branch

