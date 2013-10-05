# deployment_kitchen

Vagrant is used to create a 'virtual kitchen' with Chef provisioning
enabled; the first time you start the vagrant vm it will continue from
bootup to provisioning the chef recipes.

Try visiting `http://localhost:8080` on your machine to see nginx up and
running!  Feel free to `vagrant ssh` in and have a play with `git` and
`vim` etc.

## Usage

Clone this repo and simply run

```
$ bundle install                                      # to install chef, knife-solo, and berkshelf
$ berks install                                       # to pull in cookbooks used
$ vagrant plugin install vagrant-berkshelf            # install plugin for vagrant
$ vagrant up                                          # start testing environment
```

## HOWTO Recreate This Kitchen

This kitchen was generated with `knife solo init .` inside
`~/vagrant/deployment`.

### Vagrant Install

Install Ubuntu `precise64` and generate a `Vagrantfile`.  The
`Vagrantfile` in this git repo is configured to add Chef to our 'virtual
kitchen' &mdash; our `precise64` virtual machine.

```
$ vagrant box add precise64 http://files.vagrantup.com/precise64.box
$ vagrant init precise64
```

## Creating a Cookbook

```
-> % knife cookbook create serverbox -C "Michael de Silva" -m "michael@mwdesilva.com" -l mit -r md
** Creating cookbook serverbox
** Creating README for cookbook: serverbox
** Creating CHANGELOG for cookbook: serverbox
** Creating metadata for cookbook: serverbox
```

## References

* http://blog.atwam.com/blog/2013/04/27/preparing-a-rails-app-for-deployment-using-chef-solo/
* http://leopard.in.ua/2013/01/04/chef-solo-getting-started-part-1/
