# etyl-ruby
Etyl in a JRuby suit


### Installing jbundler
```
  jruby -S gem install jbundler
```


### Install jar dependencies
```
  jruby -S jbundle install
```

### Start application
```
  jruby init.rb
```
### Minimal Working Example
```
# main.rb
require_relative 'etyl.rb'

java_import 'com.harium.etyl.Etyl'
java_import 'com.harium.etyl.commons.graphics.Color'
java_import 'com.harium.etyl.commons.context.Application'

class Main < Etyl
  field_accessor :w, :h

  def initialize
    super 960, 480
    set_title "Hello JRuby"
  end

  def startApplication
    SampleApplication.new w, h
  end

  class SampleApplication < Application
    def load
    end

    def draw g
      g.set_color Color::RED
      g.fill_rect self
    end
  end
end

# Starting Main
opening = Main.new
opening.init
```

Run the example with
```
  jruby main.rb
```
