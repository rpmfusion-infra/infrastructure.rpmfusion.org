# Push Packages
This describes the methods to sign and publish packages into the primary mirror that will later propagate to others mirrors.
There are few importants points: 
* Packages in candidate will be moved to testing
* Packages in testing will be moved to updates
* If some components are missing, there is a need to revert back before preparing the repositories
* Special attention to freeworld packages is needed

## Sign Packages

* TODO with sigul

## Send report and move builds

* TODO

## Prepare de repositories

* TODO with mash scripts (currently automated for fedora and el regular repositories).

* TODO some corners cases (steam, nvidia, tainted)


## Push the repositories

* Push packages from download0 to download1 primary mirror with theses scripts
```
ssh pkgs.rpmfusion.org -A
rpmfusion_free_fedora_push
rpmfusion_nonfree_fedora_push
rpmfusion_free_el_push
rpmfusion_nonfree_el_push
```



