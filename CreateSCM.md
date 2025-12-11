# Create SCM package (maintainer task)


1. Create the packagename using web ui, use the correct namespace (free, nonfree)

[Create a new package in pkgdb](https://admin.rpmfusion.org/pkgdb/new/package/)


2. Process new package (admin task)

```
rfpkgdb-admin process

pkgdb-admin --pkgdburl=https://admin.rpmfusion.org/pkgdb --fasurl=https://admin.rpmfusion.org/accounts/ --bzurl=https://bugzilla.rpmfusion.org
```

3. Create the Git repository and branches (admin task)

 This will create the needed files as user, then as admin.

```
ssh -A _username_@pkgs.rpmfusion.org
/usr/local/bin/genacls.sh
sudo /usr/local/bin/genacls.sh
```

4.  Add package to bugzilla (needs bugzilla admin rights).

