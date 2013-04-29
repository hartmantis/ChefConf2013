# Day 2 - Eat the Whole Bowl w/ Omnibus #

* Omnibus: A full stack installer
* Because setting up your own Chef 10 server SUCKED
* Prototype: Clojure project named Fatty by Adam Jacob
* We now use Omnibus for all our projects
* Eliminate variation between platforms
* 1.0 release was all rake tasks; now has CLI too

    gem install omnibus
    omnibus project wang
    ...vim...
    omnibus build project wang
    ...
    omnibus clean wang --purge

* Does healthchecks to make sure only linking against internal things, no system libraries
* Near-term: Aruba functional tests
