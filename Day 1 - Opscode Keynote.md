# Day 1 - Opscode Keynote #

## Intro ##

* ***Code can***
* Mitch ??? - CEO
* Chris Brown - CTO
* The business is changing more rapidly than our skills are developing
* "You can't roll back a burning building."
* Getting rid of healthcare mindset; hide the complexity, disguise true costs
* Flickr: 10 deploys/day in 2009
* Devops = platypus = Dev duck + beaver ops
* craft -> trade -> science; we're building the science of automation
    * Programmer -> software engineer -> computer scientist
    * Hacker -> systems admin -> ?
* Education: tech advances faster than schools can
* Books:
    * ***Guerilla Capacity Planning***
    * ***Network and System Administration***
    * ***The Art of Capacity Planning***

* Community: Behave responsibly
* "140 characters is just enough to say something mean about somebody else"
* Lead with questions, avoid passive agressiveness

* Hosted Chef = single largest Chef instance in the world, AFAWK
* learnchef.com
* Partnership w/ IBM to build AIX support
* knife-essentials - plugin now part of mainline Chef

## Coming Soon ##

* Awesome new web UI
    * Pretty graphs
    * Logs of all the nodes
    * Failed/successful/running client runs
* Push from server to nodes
    * `knife job list`
    * `knife node status`
    * `knife job start`; quorum option (run 50% of machines)
    * No longer need to rely on chef-client daemon or cron jobs

