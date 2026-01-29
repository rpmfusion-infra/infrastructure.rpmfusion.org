# Add packages into the override repository

* First drop a line about which package you are about to land into IRC '#rpmfusion-admin' and why.

* Also don't forget to clean-up older packages in overrides as the repo will override even newer EVR packages.

* Maintainers in the sysadmin-build group can ssh into the koji host.
```
ssh koji.rpmfusion.org -A
```

* Verify that you have the latest version on the rpmfusion-tools as ~/bin
```
git clone https://github.com/rpmfusion-infra/rpmfusion-tools.git ~/bin
```

* Verify that your default umask is 002 and use the default group as sysadmin-build. to setup in ~/.bashrc
```
umask 002
newgrp sysadmin-build
```

* Change to buildsys-override directory
```
cd /mnt/koji/buildsys-override
```

* get into the override directory for the koji build target
```
cd f43-free
```

* Fetch the koji build
```
koji -q  -p koji-fedora download-build gstreamer1-plugins-bad-free-1.26.10-1.fc43
```

* Dispatch the downloaded rpm pacakges into the related arched sub-directory
```
rpm-dispatch
```

* Regen the related repositories as needed.
```
koji-rpmfusion regen-repo f43-free-build --nowait
koji-rpmfusion regen-repo f43-free-multilibs-build --nowait
```

