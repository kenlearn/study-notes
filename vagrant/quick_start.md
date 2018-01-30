# Vagrant Quick Start

## Quick Start
```bash
vagrant init ubuntu/xenial64
```

## Sample Config
```ruby
config.vm.hostname = 'master'
config.vm.box_check_update = false
config.vm.network "private_network", ip: "192.168.33.10"

config.vm.provider "virtualbox" do |vb|
  vb.gui = false
  vb.memory = "2048"
end
```

## Change Hostname
```ruby
config.vm.hostname = 'master'
```

## Use bridge/public network
```ruby
config.vm.network "public_network"
```

## Change VM memory size
```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = "1024"
end
```
## Disable box update
```ruby
config.vm.box_check_update = false
```
