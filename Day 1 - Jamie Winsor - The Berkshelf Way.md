# Jamie Winsor - The Berkshelf Way #

* "Siri, new environment. Large!"
* My name is Jamie Winsor and I love video games
* Unlike my banking software, when LOL goes down, I table flip
* Me in 2009 - What's a cookbook? What's with these Chef primitives with weird names?
* Me in 2010 - Oh god, this Chef repo!
* Me in 2011 - Git submodules! ... ... Oh hell.
* Me in 2012 - Each cookbook is its own artifact, not one huge repo
    * So we need a tool!
* SCM similar to Mix, Go, or Leiningen
* "We were going to name it Bookshelf, but that's as easy to Google as Chef is."
* "I prefer RBEnv" (Are Bee Envv)

    berks init

* metadata is IMPORTANT, stop leaving it blank!
* Follow semver!
* Central berkshelf - Every version you install, we keep it there

    berks upload


## "Work at verticals from the outside in" ##

    * "We don't provide CentOS to customers; we provide LOL"
* Application cookbook pattern
    * Start with application, one recipe for each component

    myface::database_server
    myface::_common_system

* Private recipes vs public recipes
* Public recipe: database\_server
* Private recipe: \_common\_system

## Favor Data-Driven Cookbooks ##

* Encourage reusability
* Favor configuring with attributes
* I'd favor an attributes file for each recipe

### When to Use Data Bags ###

* Org-level configs: users, groups, yum/apt, things configured by base
* Encrypt for sensitive info

## Write Well-Encapsulated Cookbooks ##

## Stop using roles! ##

* Not versioned, packaged, distributed, namespaced
* Org-level data

* Default recipe is special; bunch of includes

## Library Cookbook Pattern ##

* 0 or 1 recipes
* Provides providers, libraries, etc.
* See yum cookbook

## Wrapper Cookbook Pattern ##

* 1-3 recipes, super lightweight, no LWRPs
* Attribute overrides
* e.g. Riot-Java, installs/configures Java version we need

## Have Short Iteration Loops ##

* Workflow: Edit cookbook; vagrant up/provision; Test/SSH/validate

## That Siri Demo ##

* Siri talks to our new cloud orchestrator
* ***We were hoping to open source this today, but some stuff more to do***

