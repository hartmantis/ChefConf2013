# Miah Johnson - Managing Resources and Their Providers #

## 1st Generation Cookbook Pattern ##

* 1st gen cookbook pattern: default.rb + service + package
* Oh god, suddenly all these conditionals!
* Over 9000 attributes isn't flexible or scalable
* What happens if you want to use your own package
* Cookbooks are highly opinionated

## 2nd Generation Composable Pattern ##

    include_recipe 'nginx::_user'

* More flexible but still opinionated

## 3rd Generation Library Pettern ##

    nginx_instance 'example.com' do
        ...
        ...

* Removes lots of crazy case statements and attributes
* With a wrapper:

    nginx/recipes/default.rb:

    sites = data_bag('sites')

    sites.each do |instance|
    ...

* Providers can be overridden

    nginx_instance 'example.com' do
        provider Chef::Provider::CorpNginx::Instance
    end

* These providers are standard Ruby classes
* Kind of our own LXC
* Antipattern - Cookbooks with search built right into them
* "While I'm writing my cookbook, I can run a guard session so I know how badly I've broken things"
* Lots of cookbooks force an init system on you
* https://github.com/miah/nginx/blob/chefconf/libraries/provider\_nginx\_instance.rb
