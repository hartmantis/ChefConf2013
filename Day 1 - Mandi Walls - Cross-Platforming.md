# Mandi Walls - Cross-Platform Friendly Cookbookbing #

## Intro ##

* Opscode Road Team
* Windows tourist
* Problem: Lots of community cookbooks are Ubuntu-only

## Platforms ##

* `node['platform_family']` - assembled in Ohai
    * See examples in apache2 cookbook
* `node['os']` - Ohai OS plugin
* `node['os_version']`
* May be able to simplify big case statements with value\_for\_platform function

    pkg_name = value_for_platform(%w{rhel suse} => 'pants')(?)

    service 'apache2' do
        case node['platform_family']
        ...
    end

* First option: attributes
* Another option: separate windows/linux/etc. recipes
* Final option: separate cookbooks (ick)

* Being a good community citizen = support as many platforms as you can
* Tools like Bento can help
