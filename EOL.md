# EOL release

This document present the action taken when a release is "End Of Life".


__Bugzilla Side:__

* Before EOL (one week), run bugzilla and advertise that all f41 bug to be closed

* On EOL date, close EOL tickets.

* Disable the version to be selected for component


__Infra side:__

* Last push with only safe, non-breaking changes.

* Remove the EOL release from rpmfusion-tools various push scripts

* Remove koji build target

* Remove buildsys-override repos

* Remove all tags and let the builds go into GC

* Disable the collection in pkgdb: https://admin.rpmfusion.org/pkgdb/collections/


