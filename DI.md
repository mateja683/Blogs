DI BLOG
=========

![Image](./decoupling_meme.jpg)

What is dependency injection?
------------------------------------
It allows you to inject dependencies, like other classes, into a class at runtime. The most useful reason for doing this is testing - it allows you to insert doubles into your unit tests, as opposed to using actual objects on which there are dependencies .

Give an example of a class or method that does not use dependency injection
------------------------------------
```ruby
class Motorbike

  def initialize
      @engine = Engine.new
    end
end
```

Explain why it is bad design
------------------------------------
The main issue is that the above method will make it difficult to test the motorbike class in isolation (hard to decouple).

It also does not allow the flexibility of inserting an engine object which you have already created separately. For example, the above method will prevent you using a specific engine instance you have modified the attributes of ('pimped up big style'),  which you want to insert in your new bike.

Refactor the class/method to use DI
------------------------------------
Example 1

```ruby
class Motorbike
  def initialize(engine = Engine.new)
    @engine = engine
  end
end

```
Example 2

``` ruby
class Motorbike
  def initialize(engine)
    @engine = engine
  end

  def self.build(horse_power = 500)
    new(Engine.new(:horse_power => horse_power))
  end
end
```
