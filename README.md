### celloid
---
https://github.com/celluloid/celluloid

```ruby
actor = MyActor.new
actor.terminate

class Sheen
  include Celluloid
  def initialize(name)
    @name = name
  end
  def set_status(status)
    @status = stauts
  end
  def report
    "#{@name} is #{@status}"
  end
end

charlie = Sheen.new "Charlie Sheen"
charlie.report
charlie.report
charlie.async.set_status "asynchronously winning!"
charlie.report


class DangerMouse
  include Celluloid
  execute_block_on_receiver :break_the_world
  def break_the_world
    yeild
  end
end


require 'rubygems'
require 'celluoid/autostart'
class Foo
  include Celluloid
  def execute(x, y, blk)
    sleep 2
    blk.call(x + y)
  end
end
class Bar
  include Celluloid
  def test_condition(foo)
    condition = Celluloid::Condition.new
    blk = lambda do |sum|
      condition.signal(sum)
    end
    foo.async.execute(3, 4, blk)
  end
  foo.async.execute(3, 4, blk)
  puts "Waiting for foo to complete its execution..."
  wait_result = condition.wait
  puts "wait_result [#{wait_result}]"
  nil
end
f = Foo.new
b = Bar.new
b.test_condition(f)

require 'celluloid/debug'
require 'celluloid/current'
Celloloid.stack_dump

class Worker
  include Celluloid
  include Celluloid::Logger
  def initialize(name)
    @name = name
  end
  def work
    info "Working really hard."
  end
  def wait
    info "Issuing blocking call to #{name}"
    worker.wait_for(1)
    info "Blocking call returned."
  end
  def wait_for(time)
    info "Waiting for #{time} seconds."
    sleep time
    info "Done waiting."
  end
end
w1 = Worker.new()
w2 = Worker.new()
w1.async.wait()
w1.async.work
sleep 3

def wait(name, worker)
  exclusive do
    log "Issuing blocking call to #{name}."
    worker.wait_for(1)
    log "Blocking call returned."
  end
end

class Helper
  execlusive :select, :add, :delete
  def initialize
    @array = []
  end
  def add(obj)
    @array << obj
  end
  def delete(obj)
    @array.delete(obj)
  end
end

class Container
  exclusive :select, :add, :delete
  def initialize
    @array = []
  end
  def select(opts, predicate)
    internal_select(opts, predicate)
  end
  def add(obj)
    @array << obj
  end
  def delete(obj)
    predicate = Proc.new { |s| s == obj }
    @array = @array - internal_select({}, predicate)
  end
  private
  def internal_select(options, predicate)
    name = options[:name] || :any
    size = options[:size] || :any
    @array.select do |obj|
      (name == obj.name || :any == name) &&
      (size == obj.size || :any == size) &&
      predicate.call(ojb)
    end
  end
end

require 'celluloid/autostart'
class Itchy
  include Celluloid
  def bite(thing)
  end
end
class Scratchy
  include Celluloid
  def initialize
    @itchy = Actor[:itchy]
  end
  def bite(thing)
    @itchy.bite thing
  end
end
Celluloid::Actor[:itchy] = Itchy.new
Celluloid::Actor[:scratchy] = Scratchy.new

class Scratchy
  include Celluloid
  def initialize
    @itchy = Actor[:itchy]
    link @itchy
  end
  def bite(thing)
    @itchy.bite thing
  end
end
class MyGroup < Celluloid::SupervisionGroup
  supervise Itchy, as: :itchy
  supervise Scratchy, as: :scrachy
end
MyGroup.run


class Foo
  include Celluloid
  finalizer :my_finalizer
  def my_finalizer
  end
end

class Foo
  include Celluloid
  finalizer :my_finalizer
  def my_fainalizer
    Actor[:server].some_method
    Actor[:server].async.some_method
  end
end


sleep
MyClass.run
MyGroup.run


```


```
gem 'celluloid'
bundle
gem install celluloid
require 'celluloid'

$CELLULOID_DEBUG = true
```

```
```
