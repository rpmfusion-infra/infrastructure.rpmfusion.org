# Getting Started into RPM Fusion administration

## There are two areas related to RPM Fusion administration:
* sysadmin: the group responsible of handling various infra services.
* releng:  the group responsible for package content including signing and pushing content.


## The skills you may want to learn to do this work include:
* Mastering Ansible.Take a look at  [Ansible RPM Fusion](https://github.com/rpmfusion-infra/ansible-rpmfusion/)
* Knowing how to write scripts for system administration
* Knowing how to write web applications using Python and SQL or equivalent technologies
* Knowing how to debug and specially how to audit systems, services and applications.
* Knowing how the RPM Fusion project works behind the scenes

## Other pluses:
* Have previous systems admin experience
* Have access to your own testing machines for testing and staging prod ('''Huge plus!'''  Our resources are limited obviously, especially for testing which we haven't)
* Work in other areas of RPM Fusion like Packaging or Documentation
* Work in Fedora Infrastructure team or have knowledge on services that Fedora Infrastructure runs.

## How to Get In:
Joining the Infrastructure group is easy.
* Sign up for a [RPM Fusion Account](https://admin.rpmfusion.org/accounts/user/new).
* Subscribe to the developper mailing list and introduce yourself.
* Come and join on ``IRC``

## Synopsis for landing or updating services:
If you can help to create a new service or update an existing service for the RPM Fusion project.
* Get familar the Fedora project process if any [Fedora Infra Docs](https://docs.fedoraproject.org/en-US/infra/)
* Research for existing infrastructure request in our [bugzilla](https://bugzilla.rpmfusion.org/buglist.cgi?bug_status=__open__&list_id=25328&order=Importance&product=Infrastructure&query_format=specific) and engage discussions.
* Adapt the deployment role from the [Fedora Ansible](https://infrastructure.fedoraproject.org/infra/ansible.git/) to [RPM Fusion Ansible](https://github.com/rpmfusion-infra/ansible-rpmfusion/), or create a new role.
* Create a local self instance with non-relevant roles commented-out.
* At some point, you can ask for a test VM so everything can be wired as appropriate.

Even if you don't want to be involved on a regular basis at this point, please feel free to watch over things and report bugs as you see fit.
Showing interest now is a great way to make it easier to join the team's activities later.


