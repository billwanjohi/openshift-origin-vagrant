# OpenShift Origin Vagrant

OpenShift Origin is a promising open-source provider-agnostic
platform-as-a-service.

This project is an attempt to follow along with the OpenShift Origin guide to
[Getting Started for Administers](https://docs.openshift.org/latest/getting_started/administrators.html)

## Implementation

The origin docs recommend three simple installation methods. I opted for
the first, running the service in a docker container bound to a CentOS
Linux distribution. Since my local dev environment is Mac OS X, I
virtualized CentOS using a Vagrant Box published to Atlas by Puppet
Labs, running on VirtualBox. I used the ansible_local and docker
provisioners to configure this image, but intend to drop the latter.

## TODO

- Successfully render a sample web application
- Figure out firewall problems
- [Explore Aggregate Logging](https://docs.openshift.org/latest/install_config/aggregate_logging.html)
