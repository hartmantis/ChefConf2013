# Chef and OpenStack #

## Intro ##

* @mattray

* OpenStack beginning - NASA hires Anso Labs
* Rackspace's business model = other people's software + fanatical support
* 7 parts
    * Compute - Nova
    * Obj Storage - Swift
    * Image Registry - Glance
    * Identity - Keystone
    * Dashboard - Horizon
    * Networking - Quantum (Quantum HD maker hated this)
    * Block Storage - Cinder

### Nova ###

* Recently added cells and availability zones
* KVM, Xen, LXC, Hyper-V, VMWare, bare metal
    * Most popular: KVM
    * Adding support for heterogeneous hypervisors
        * "I need a Windows server. Okay, Hyper-V is over there"
    * VMWare relationship on/off again

### Cinder ###

* Virtual block storage
* Drivers for storage vendors: NetApp, Solidfire, Ceph, Nexenta

### Quantum ###

* Virtualized networking
* Drivers for Ryu, Floodlight, Nicira, Midokura, Cisco, +++

### Glance ###

* Catalog only, use e.g. Swift as storage backend
* Talk of using BitTorrent to distribute images

### Keystoen ###

* Limited LDAP support right now
* Easy to overload Keystone w/ Swift, etc. queries

### Swift ###

* Petabytes of reliable storage
* High operational friendliness, low-ish speed
* It just works

### Horizon ###

* Django app
* People skin, add plugins

* github.com/openstack
* Gerrit - review.openstack.org
* jenkins.openstack.org
* Rackspace runs from trunk
* devstack.org

### Incubating ###

* Commons - Oslo
* Metering - Ceilometer
* Orchestration - Heat

### Being discussed ###

* Queueing
* ***Email***
* HadoopAAS

## Chef for OpenStack ##

### What is it? ###

* Cookbook repo
* Cookbooks for each 7 components
* Poor documentation
* Essex right now (working on it)
* knife-openstack
* github.com/opscode/openstack-chef-repo

### What will it be? ###

* Our own packages, not waiting for builders
* CI
* Postgres, Ceph, Midokura, RHEL, Docs, HA

* github.com/att-cloud
* crowbar.github.com
* github.com/dreamhost

## knife-openstack ##

* Working on a shared plugin for things common to Rackspace/OpenStack/etc.

## OpenStack Cookbooks ##

* github.com/osops is being resurrected
* Cookbooks all end in -cookbook in repo name
* Ops cookbooks (logging, monitoring, etc) outside this scope
* Goal: Have OpenStack Jenkins building w/ Chef cookbooks

### Style Guide ###

* ***As few attributes in roles as possible***
* Attributes can short-circuit search
* Environment-driven attributes
* ***Platform logic in attribute files***

### Grizzly Roadmap ###

### Other ###

* RHEL, Postgres, Quantum, HA, etc.
* Crowbar 2.0

### Other Other ###

* Cross-distro testing - the future of Test Kitchen

## Crowbar ##

* Grew out of frustration with customers not having what they needed to install OpenStack
    * DHCP huh? PXE wha?
* 1.0 - Tightly built around Chef, not even its own DB, performance hits b/c/ Chef 10
* 2.0 - Pulled some out of Chef
* Test it out - https://github.com/crowbar/crowbar-utils/tree/master/vagrant_crowbar
* BarClamp = Chef cookbooks + Ruby code to integrate thos into the orchestration system
* Woo, Sensu!

## Other ##

* Rackspace Private Cloud
