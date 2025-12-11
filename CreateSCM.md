# Create SCM package


* Create the packagename using web ui (maintainer task)

[Create a new package in pkgdb](https://admin.rpmfusion.org/pkgdb/new/package/)

* Verify to use the correct namespace (free, nonfree) (admin task)

*  Process new package (admin task)

```
rfpkgdb-admin process

pkgdb-admin --pkgdburl=https://admin.rpmfusion.org/pkgdb --fasurl=https://admin.rpmfusion.org/accounts/ --bzurl=https://bugzilla.rpmfusion.org
```

* Create the Git repository and branches (admin task)

 This will create the needed files as user, then as admin.

```
ssh -A _username_@pkgs.rpmfusion.org
/usr/local/bin/genacls.sh
sudo /usr/local/bin/genacls.sh
```

*  Add package to bugzilla (needs bugzilla admin rights).

