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

*  Add package to bugzilla (needs bugzilla admin rights).

TODO: have a script.

Final: close the review ticket.
