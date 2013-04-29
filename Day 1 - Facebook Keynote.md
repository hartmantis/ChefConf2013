# Day 1 - Phil Dibowitz - Facebook Keynote #

* Metallica everywhere
* The goal: 4 people, tens of Ks of heterogeneous systems, service owners own their infrastructure
* Building blocks
    * Distributed - everything on the client
    * Deterministic - The system you want on every run
    * Idempotent - Only the needed changes
    * Extensible - Tied into internal systems
    * Flexible - No dictated workflow
* Configuration as data
    * Service owners shouldn't need to know how to setup sysctl, configure VIPs, etc.
* Problem (for us):
    * Node.save sends data back to server, 15k nodes = lots of data
    * Solved w/ whitelist\_node\_attrs
        * Deletes non-whitelisted attrs before sending back to server
        * Re-opens Node.save
        * Can still Ohai attrs on client, just not on server
    * Flexible!
* Moving idempotency UP
    * What if I want to get rid of a cron job?
        * Chef won't delete it if it's just removed from the cookbook
        * Chef should manage ALL of cron, be authoritative
    * Case study: fb\_sysctl
        * We build a hash of sysctls and control ALL OF sysctls
        * Idempotent!
    * Does this mean .d-styles are obsoleted?
    * `node.default['fb']['fb_networking']['want_ipv6'] = true`
    * DSR
        * Inbound traffic through LB, outbound back direct to client
        * Saves bw

## Our Chef Infrastructure ##

* Open source AND private Chef
    * Private gets support and got 11's HA features first
    * Open = we share with community, they with us
    * You CAN run FB-size clusters on community
* Stateless Chef servers
    * No search or data bags
    * Every cluster has its own server
    * Tiered model - Separated Chef backends and frontends
    * Backend servers check out of SVN, update every minute
        * grocery\_delivery does the syncing
    * Ohai plugin pulls data from Systems of Record (SOR) which holds the state that'd normally be in Chef Server
    * ***github.com/facebook/chef-utils***
* Scale
    * 10k nodes/cluster
    * Lots of clusters
    * 15-min convergence (14-min splay)
    * 17k nodes, 80% CPU idle w/ Chef 11
    * "We can probably put more thrust on that [Chef 10] pig." - Adam Jacob
    * Chef 10 idle backup using more CPU than Chef 11 w/ 4k nodes

## Testing ##

* Testing in CFEngine sucks
* Use orgs in private Chef/hosted Chef
* Testing against real systems is useful and necessary

## Lessons ##

* My Chef team is 4 people
* >17k nodes


