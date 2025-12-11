# Create SCM package (maintainer task)


l. Create the packagename using web ui, use the correct namespace (free, nonfree)

[[Create a new package|https://admin.rpmfusion.org/pkgdb/new/package/]]


l. Process new package (admin task)

```
rfpkgdb-admin process

pkgdb-admin --pkgdburl=https://admin.rpmfusion.org/pkgdb --fasurl=https://admin.rpmfusion.org/accounts/ --bzurl=https://bugzilla.rpmfusion.org
```

l. Create the Git repository and branches (admin task)

 This will create the needed files as user, then as admin.

```
ssh -A ``username``@pkgs.rpmfusion.org
/usr/local/bin/genacls.sh
sudo /usr/local/bin/genacls.sh
```

l.  Add package to bugzilla (needs bugzilla admin rights).

