# Refactoring Cookbooks #

* How do you refactor when you don't have tests?
* Example: hostsfile cookbook
* Pt1 - Template it
* Pt2 - Shove shit in an attribute + template
    * Goddamn, which of these 400 cookbooks wrote that hosts attribute?
    * Oh shit, I accidentally overrode the entire attribute
* Pt3 - Monkey patch Chef to raise an exception if you rewrite that attribute
    * Boooooo
* Pt4 - Have a recipe do a check to validate hosts attribute
    * That is not how cookbooks work
* Maybe put hosts in a data bag?
    * Okay! And we can write ChefSpec tests for it!
    * But we can't write a data bag with info from the Redis server we need to get records from
    * But other cookbooks need to create hosts entries!
* Enter LWRP
    * Provider kept growing and growing
    * Time for a refactor!
* Refactor
    * Delegate to a Ruby gem
    * Easier to test! So many tools for Ruby code
    * Don't need ChefSpec/Fauxhai/etc.
* At this point, why can't it just be a Ruby gem?
    * entry.rb and manipulator.rb -> Gem
    * Now we need this Gem in Chef...?
    * LWRP needs a default recipe to call chef\_gem
    * Let Puppet users use it if they want
* https://github.com/customink-webops/hostsfile/blob/master/libraries/manipulator.rb
