# Create SCM package

This page explains how to create a new package within the RPM Fusion infra. This is restricted to users in the 'sysadmin-scm' group.

* Create the packagename using web ui (maintainer task)

[Create a new package in pkgdb](https://admin.rpmfusion.org/pkgdb/new/package/)

* Verify to use the correct namespace (free, nonfree, cuda) (admin task)

*  Process new package (admin task)

```
rfpkgdb-admin process

pkgdb-admin --pkgdburl=https://admin.rpmfusion.org/pkgdb --fasurl=https://admin.rpmfusion.org/accounts/ --bzurl=https://bugzilla.rpmfusion.org
```

* Create the Git repository and branches (admin task)

    press Request new package
    https://admin.rpmfusion.org/pkgdb/request/package/
    ticket 7359
    press sync
    (package name is filled)
    choose branches
    choose namespece free or nonfree or cuda
    press create

    log :
    user: sergiomb request package: intel-vision on branch master
    user: sergiomb request package: intel-vision on branch f44

    rfpkgdb-admin list
    #1059 (Awaiting Review) - sergiomb requested the new package "free/intel-vision-kmod" on "master"
        review: https://bugzilla.rpmfusion.org/7359
    #1060 (Awaiting Review) - sergiomb requested the new package "free/intel-vision-kmod" on "f44"
        review: https://bugzilla.rpmfusion.org/7359
    #1061 (Awaiting Review) - sergiomb requested the new package "free/intel-vision" on "master"
        review: https://bugzilla.rpmfusion.org/7360
    #1062 (Awaiting Review) - sergiomb requested the new package "free/intel-vision" on "f44"
        review: https://bugzilla.rpmfusion.org/7360
    Total: 4 actions

    rfpkgdb-admin process 1059
    #1059 (Awaiting Review) - sergiomb requested the new package "free/intel-vision-kmod" on "master"
        review: https://bugzilla.rpmfusion.org/7359
    FAS password for user sergiomb:
    [+] Review approved by packager `b'Nicolas Chauvet' (b'kwizart') <kwizart@gmail.com>`
    [+] Requester sergiomb is a packager
    [-] The bug title does not fit the expected one
    exp: "Review Request: intel-vision-kmod - b'The intel-vision drivers for Lnuar Lake cvs-enabled platform'" vs obs: "b'Review request: intel-vision-kmod - The intel-vision drivers for Lnuar Lake cvs-enabled platform'"
    [-] Wrong bug component
    exp: "Package Review" vs obs: "Review Request"
    [-] Wrong bug product
    exp: "Fedora" vs obs: "Package Reviews"
    [-] Review bug created by `b'[Unknown]' (b'smallorange') <hpa@redhat.com>` but request by sergiomb

    What should we do about this requests?
    approve, deny, pass: approve
    FAS password for user sergiomb:
    Package created

    rfpkgdb-admin process 10560

    #1060 (Awaiting Review) - sergiomb requested the new package "free/intel-vision-kmod" on "f44"
        review: https://bugzilla.rpmfusion.org/7359
    Package intel-vision-kmod found, requalifying request.package in request.branch
    Auto approving Fedora Branch request for package admin sergiomb
    user: sergiomb set for sergiomb acl: commit of package: intel-vision-kmod from:  to: Approved on branch: f44
    user: sergiomb set for sergiomb acl: watchbugzilla of package: intel-vision-kmod from:  to: Approved on branch: f44
    user: sergiomb set for sergiomb acl: watchcommits of package: intel-vision-kmod from:  to: Approved on branch: f44
    user: sergiomb set for sergiomb acl: approveacls of package: intel-vision-kmod from:  to: Approved on branch: f44

    rfpkgdb-admin process 1061
    rfpkgdb-admin process 1062

 This will create the needed files as user, then as admin to update some files with acls.

```
ssh -A _username_@pkgs.rpmfusion.org
/usr/local/bin/genacls.sh
sudo /usr/local/bin/genacls.sh
```

* Add package to github (admin task)

Both scripts need to be run on pkgs01, the first will update the list of module and create new-free, new-nonfree, new-cuda files when new packages

``` pkgs2github
create2github new-free free
git commit rpmfusion-liste* -m "Update list"
git push
```

Once the gh command to create github components are output by the create2github script, you can run it on you local host assuming the gh cli is installed and the appropriate token set.

```
gh repo create -d "obs-studio-plugin-distroav - nonfree" --homepage http://rpmfusion.org/Package/obs-studio-plugin-distroav --disable-issues --disable-wiki --public -t packager rpmfusion/obs-studio-plugin-distroav
✓ Created repository rpmfusion/obs-studio-plugin-distroav on github.com
  https://github.com/rpmfusion/obs-studio-plugin-distroav
```

If we want update one package on github , for example openhantek

```
cd /srv/git/repositories/nonfree/openhantek.git/;  echo "$PWD" > /run/rpmfusion-github-mirror
```

in limit list and update all packages

```
 for d in /srv/git/repositories/free/*/; do cd "$d" || continue; echo "$PWD";   cd ..; done
 for d in /srv/git/repositories/nonfree/*/; do cd "$d" || continue; echo "$PWD";   cd ..; done
 for d in /srv/git/repositories/free/*/; do cd "$d" || continue; echo "$PWD" > /run/rpmfusion-github-mirror;   cd ..; done
 for d in /srv/git/repositories/nonfree/*/; do cd "$d" || continue; echo "$PWD" > /run/rpmfusion-github-mirror;   cd ..; done
```

*  Add package to bugzilla (needs bugzilla admin rights).

TODO: have a script.

Final: close the review ticket.
