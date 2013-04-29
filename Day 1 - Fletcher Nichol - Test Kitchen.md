# Day 1 - Test Kitchen #

## Part 1 ##

* HELP! We need to test on all the platforms private Chef supports
* Declarative, extensible, usable w/ Ruby and/or Erlang projects
* NOT created for cookbook testing; for testing our software
* Heavy inspiration from Travis

## Part 2 ##

* Hey, we could use TK for cookbook testing
* Gather requirements
    * Cross platform
    * Regression testing
    * Lint/unit/spec
    * Functional/integration
* We can Jenkins test cookbooks, yay!
* Limitations: Hard to add new providers; hard to override local configs

## Part 3 ##

* Jamie out of TK not clicking with me
* Problem: RVM cookbook can take hours to test (compiles Ruby); has tons of LWRPs
* -> insane Vagrantfile
* -> Need code to generate my Vagrantfile
* -> Ruby library -> Jamie

## Part 4 ##

* Sent email to Opscode
* "I need Test Kitchen w/ external drivers, more declarative config"

## Part 5: Kitchen Concepts ##

* .kitchen.yml based on travis.yml
* Declarative and static; keep it simple; don't make a new DSL
* Platform = Distro + version + Chef version + etc.
* Suite = Name, run\_list, attributes
* Instance = Platform + Suite
* Actions: create, converge, setup, verify, destroy (or do all w/ test)
* `kitchen test` won't clean up if it fails
* Plugin system to plug in different test harnesses
    * Even just a bash script, exit 0 or 1
* Chef solo only _right now_
* Driver: implementation of instance actions
* Each instance can have its own driver

    platforms:
    - name: smartos
    driver_plugin: vagrant
    driver_config:
        ...


    kitchen init

## The future ##

* Docs, better error output
* Provisioner extraction
* One shared Fog driver
* TK Jenkins plugin
* Far future: multi-VM cluster support
