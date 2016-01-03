# Rails

## Architecture
### Guidelines
+ Avoid having methods in objects that inherit from `ActiveRecord::Base` other than methods dealing with the active
record query interface - This helps in keeping models slim.

+ Avoid accessing the active record query interface from outside the specific `ActiveRecord::Base` model - This helps
in defining an interface in the models that reveals intention [A.13]. It also create a clear boundary with the remaining parts
of the system in terms of accessing the database columns. Only scopes, and methods defined by the programmer should be
accessible from the outside.

+ Don't add multiple responsibilities to an object - the concept of the responsibility might vary during the lifetime of
the application though. Extract responsibilities whenever they are identified. [A.5]

+ Use classes with gusto [A.1] - They are one of the main tools of the language to achieve modularization/encapsulation.
Using a pattern [A.7] boils down to using a distinct class for a specific purpose.

+ Use class names with verbs -  Keep in mind that software models not only things (e.g. user) but also processes
(e.g. account creation) therefore, it is perfectly acceptable for class names to contain verbs as well as nouns.

+ Figure out where the logic belongs in the domain model - Think of creating extracting responsibilities as making
aspects of the business domain explicit. Avoid stashing a bunch of apparently related procedures in a object without
adequately thinking of where it belongs in the domain. [A.11] [A.14]

+ Avoid using concerns/mixins/modules for the purposes of extracting responsibilities from classes - Modules are
appropriate for repeatable behaviour that needs to be shared across multiple objects - Comparable and Enumerable are
great examples of mixins. For most cases object composition (i.e. creating a new object) is more appropriate.

+ Prefer rich objects instead of booleans - Rich result objects to booleans are more expressive, they provide contenxt
[A.2].

+ Prefer instance methods to class methods - Class methods are global symbols and modularity is good [A.2] [A.15].

+ Don't use helpers - They are called without a receiver, so they are kind of global.  [A.16]

+ Don't keep complex logic in the view - Extract that logic into view models [A.7]

+ Avoid having logic in the controller apart from things related to processing input/ouput - Because it is not the
controller's responsibility to deal with domain related logic. [A.7] [A.6]

### Links
+ [A.1] - The Secret to Rails OO Design - http://blog.steveklabnik.com/posts/2011-09-06-the-secret-to-rails-oo-design

+ [A.2] - Anatomy of a Rails Service Object - http://multithreaded.stitchfix.com/blog/2015/06/02/anatomy-of-service-objects-in-rails/

+ [A.3] - Matt Wynne - Hexagonal Rails - https://vimeo.com/44807822

+ [A.4] - Rails Does Not Define Your Application Architecture - http://naildrivin5.com/blog/2014/05/27/rails-does-not-define-your-application-architecture.html

+ [A.5] - Single Responsibility Principle on Rails Explained - http://solnic.eu/2012/07/09/single-responsibility-principle-on-rails-explained.html

+ [A.6] - Single Responsibility Principle and Rails - http://naildrivin5.com/blog/2012/06/10/single-responsibility-principle-and-rails.html

+ [A.7] - 7 Patterns to Refactor Fat ActiveRecord Models - http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/

+ [A.8] - OOD Design in Rails, Yehuda Katz SO answer - http://stackoverflow.com/questions/1068558/oo-design-in-rails-where-to-put-stuff/1071510#1071510

+ [A.9] - Skinny Controllers, Skinny Models - https://robots.thoughtbot.com/skinny-controllers-skinny-models

+ [A.10] - How much should I refactor - https://robots.thoughtbot.com/how-much-should-i-refactor

+ [A.11] - [Ruby Tapas](http://www.rubytapas.com/) - is a great screencast about Ruby by Avdi. The episodes on OO design that I can remember are: #329, #331, #332, #333, #335, #346.

+ [A.12] - [Upcase](https://upcase.com) - a learning service by thoughbot, has its repository open for subscribers. By checking their source code you can see a lot of the practices explained in the links above being used in a real application in a sensible and pragmatic way. Additionally, their videos on SOLID principles, OO patterns are also very good.

+ [A.13] - Intention revealing names - http://ddd.fed.wiki.org/view/welcome-visitors/view/domain-driven-design/view/intention-revealing-interfaces

+ [A.14] - Domain Driven Design - http://www.amazon.co.uk/Domain-driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_1?ie=UTF8&qid=1451848209&sr=8-1&keywords=domain+driven+design

+ [A.15] - Better Ruby Presenters - http://blog.steveklabnik.com/posts/2011-09-09-better-ruby-presenters

+ [A.16] - Helpers are shit - http://nicksda.apotomo.de/2011/10/rails-misapprehensions-helpers-are-shit/

+ [A.17] - Sandi Metz Rules - https://robots.thoughtbot.com/sandi-metz-rules-for-developers

+ [A.18] - Practical Object-Oriented Design -http://www.amazon.com/Practical-Object-Oriented-Design-Ruby-Addison-Wesley/dp/0321721330

+ [A.19] - Understanding the Four Rules of Simple Design  - https://leanpub.com/4rulesofsimpledesign
