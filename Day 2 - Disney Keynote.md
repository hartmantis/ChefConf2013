# Day 2 - Disney Keynote #

* How a mouse became a Chef
* We were/are using Rackspace
* Legacy Ops = painful, -> Chef
* Picking a tool + Changing culture
* Virtual team of SMEs + stakeholders
* Lots of training and docs
* Opscode came to Bristol for ESPN, to LA, to Seattle
* Build one team of SMEs, parachute them into other divisions to train them, fan out
* Don't be afraid of Ruby
* Budget mostly spent on training
* 200 chefs @ Disney
* 4k Chef nodes
* Hundreds of cookbooks
* We built our own testing framework
* ***Chef on our F5s***
* Private OpenStack cloud
* 

## What's Next ##

* Cookbooks as a Service
* Elastic Infrastructure

## Marvel XP ##

* First product we automated with Chef
* We need no more SCP + rsync madness
* Frontent + App server + Drupal data
* Started w/ Artifactory, now using Nexus, for artifacts

### Frontend ###

* Apache
* Artifact repo

### Appserver ###

* Java
* Tomcat

### Drupal ###

* Apache, PHP
* Drupal
* drush

* Use Rundeck for orchestration layer, rolling out across Disney

* Started wanting community cookbooks, but lots of them assumed Ubuntu, EC2, access to public internet
    * We don't have any of those things in some cases

### Getting Started ###

* Start with source control
    * GitHub Enterprise for all of Disney!
    * Paves way toward CI
* Run tests w/ CI and upload to artifact repo
    * Moved to Nexus b/c enough teams wanted to pay
    * Can hit from everything you build or deploy on
* Orchestration layer
    * ***Rundeck***
    * Started as a cron replacement for clusters doing staggered cron jobs
    * Used Rundeck workflow in place of cron
* Configuration management
    * Chef!
* Combine all above = Earth's mightiest heroes

## Person 3 ##

* ServiceDesk for all tickets; created knife-servicedesk plugin!
    * ServiceDesk Chef handler; a node can submit its own change order
* Added network\_location as an Ohai plugin

    if node['network_facility'] = 'x' then node.set['nameserver'] = '1.2.3.4'

* We use F5s, let's automate them!
    * f5\_node resource and provider

    twdc_f5_node ...

* We use Nexus, let's automate it!
    * twdc\_nexus\_file resource
* zipp resource: decompress the .zip artifacts we get out of Nexus
* OS patching

## Testing Framework (Remy) ##

* Existed before Test Kitchen
* Cookbook updates were leading to failures
* Test all your roles across platforms, environments, data centers, chef versions
* Keep in mind, this is back when all cookbooks were one source repo
* Need to test pull requests when they're submitted, before pull reviews
    * Chef repo -> Sanity checks, parser tests, Foodcritic, ***yard-chef***, unit tests
        * yard-chef only looks at metadata, doesn't help that much
        * Only unit test for more complex CBs with lots of Ruby, otherwise just use functional tests
    * -> test empty Chef server
        * Would use Ridley instead of janky bash script if writing today
        * Spiceweasel - "Look at these objects, put them on the server"
    * -> converge instances
        * Love Vagrant, but needed Windows things at the time
        * minitest-chef-handler w/ functional tests
            * Format them as junit, plox
    * == 4-5 hour test cycle :(
    * -> Converge in internal OpenStack environment
        == 15-min test cycle
    * Next: LXC, probably
* Remy provides lots of nifty graphs in Jenkins
    * Foodcritic warnings, syntax warnings

* Next, next things
    * Refactor to use chef-workflow
        * Test against entire stacks/clusters
    * Better docs
    * Remy As a Testing Service

