## Setup cluster with multi VMs
```ruby
config.vm.define "master" do |master|
    master.vm.box = 'ubuntu/xenial64'
    master.vm.hostname = 'master'
end

config.vm.define "worker1" do |worker1|
    worker1.vm.box = 'ubuntu/xenial64'
    worker1.vm.hostname = 'worker1'
end

config.vm.define "worker2" do |worker2|
    worker2.vm.box = 'ubuntu/xenial64'
    worker2.vm.hostname = 'worker2'
end

config.vm.define "dev" do |dev|
    dev.vm.box = 'ubuntu/xenial64'
    dev.vm.hostname = 'dev'
end
```
