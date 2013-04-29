# Day 2 - JVM #

* Bryan Berry - Senior DevOps Engineer at Cycle Computing
* Java: Hate the language, love the runtime
* The Opscode java cookbook rocks
* FHS is a good idea, but confusing...
* ...so Chef people install by unpacking a binary tarball and linking...
* ...so I created the ark Chef resource
* Ark issue: Might accidentally DDOS Apache repo
* "Anyone use the collectd cookbook? Chef community DDOSed the Collectd maintainer and he blocked us."
* JVM shouldn't ever swap. BAAAAAD.
* System V init scripts suck
    * Upstart is only slightly better. Deprecated on RHEL in favor of System D.
* Runit = awesome. Slightly less if you need RHEL packages.
* Docker or SystemD: contain processes in LXC namespaces instead of with PIDs
* Collectd is awesome, has a sweet JMX plugin to monitor your JVM
* Local logs are dumb, send to Logstash!

