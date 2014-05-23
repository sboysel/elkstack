## ELK Stack (Elasticsearch, Logstash, Kibana)
Just a personal project with Vagrant, Chef, and Berkshelf.

### Notes
* Install [Vagrant](http://www.vagrantup.com/downloads.html) and [Chef-DK](http://www.getchef.com/downloads/chef-dk/) (for Berkshelf)
* Clone this repo into working directory:
```
git clone https://github.com/sboysel/elkstack.git
```
* Install vagrant-berkshelf plugin
```
vagrant install plugin vagrant-berkshelf --plugin-version '>= 2.0.1'
```
* Add `config.berkshelf.enabled = true` to your Vagrantfile
```
Vagrant.configure("2") do |config|
    ...
    config.berkshelf.enabled = true
    ...
end
```
