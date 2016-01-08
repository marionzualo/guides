# Testing

- Prefer tests where all its 4 steps (setup/exercise/verfication/teardown) are clearly identifiable - This helps make
tests easy to understand. [1] [2]

- Avoid the use of let/let!/before - The use of these Rspec constructs over nested describe/context blocks tends to
spread the multiple steps of testing over different blocks which makes what is happening in these steps harder to
understand. [3]

- Use Rspec contexts as a way to show that blocks of code are related - Avoid using context blocks as a way to remove
incidental duplicaton between blocks. Use contexts so that their description shows how blocks of code are related.
Contexts should be used as a way to group high level concepts together. This is a corollary of the guideline above. [18]

- Don't test private methods - Private method tests create unnecessary coupling between the tests and the implementation
details of an object and they break encapsulation. Testing private methods is an additional barrier to refactoring
(because tests also have to be changed even if the object's API and behaviour is kept the same). Testing private methods
is unnecessary because their behaviour is covered by public methods. [6] [5] [4]

- Remember that the purpose of tests is to catch regressions, provide documentation, and reduce costs (i.e. time
and money) and help with application design - When in doubt remember this. [1] [6]

- Don't stub the system under test (SUT) - If an object is so complicated that there is a need to stub it in order to test it then
that should be used as a guide to change the design. Also stubbing the sytem under test kind of violates the
encapsulation of that object. [7] A reasonable exception to this are cases in which one cannot change the SUT (e.g.
framework code, or legacy code) [8]

- Remember that tests are a tradeoff of confidence, coverage and speed - The tradeoffs one does depend largely on the
context. This impacts in which layer to test (i.e. unit, integration), what to test (e.g. sad path, happy path), which
tools to use (e.g. database, mocks, real objects, fakes) [9] [1]

- Only load ActiveRecord/Rails for tests that require it - loading Rails takes significant time when running tests. Fast
tests are good. `spec_helper`, `rails_helper` and `active_record_helper` are your friends. [10] [11]

- Prefer using `Model.new`, `FactoryGirl.build_stubbed(:model)`, `FactoryGirl.build(:model)`, `FactoryGirl.create(:model)`
(in this order) - not all tests need persisted data. not all tests need to hit the database. tests that don't hit the
database are faster. [13] [14]

- Specify a single behaviour in each example - this constrasts with the common advice of using only one assertion per
example in Rspec. Multiple expectations might imply a single behaviour. [15]

- Always pass attributes to FactoryGirl which are relevant to the test - this gives needed information to the person
reading the test regarding the causes on which it depends. Specifying everything in the factory leads to the same issues
that fixtures have and FactoryGirl attempts to avoid. [16] [1]

- What to test: Incoming messages should be tested for their return values; Outgoing messages that have side effects
should be tested to ensure they get sent; Outgoing messages without side effects should not be tested. [17] [6]

- In unit tests, units are not classes - A test is a unit if it runs fast and if it is easy to localize the source of
test failures, therefore a unit might be a representation of multiple classes collaborating. [8] [19] [20]

- Use tests as a way to define proper contracts and boundaries between components [21]

## Links
- [1] [Testing Rails](https://gumroad.com/l/testing-rails) - a book that contains a nice introduction to testing on
Rails by thoughbot.
- [2] [Four-phase test](https://robots.thoughtbot.com/four-phase-test) - introduction to the four phases of testing.
- [3] [Let's not](https://robots.thoughtbot.com/lets-not) - a discussion on the issues of overusing certain RSpec
features.
- [4] [Fragile tests](http://xunitpatterns.com/Fragile%20Test.html) - description of the fragile test anti pattern.
- [5] [Testing private methods](https://practicingruby.com/articles/testing-private-methods) - discussion around why
testing private methods is not recommended and how to deal with it.
- [6] [Practical Object Oriented Design in Ruby](http://www.amazon.com/Practical-Object-Oriented-Design-Ruby-Addison-Wesley/dp/0321721330)
- This is book is a must read if you program in Ruby or in any OO language. There is a great chapter (i.e. chapter 9)
on testing.
- [7] [Don't stub the system under test](https://robots.thoughtbot.com/don-t-stub-the-system-under-test) -
- [8] [Working effectively with legacy code](http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052)
- A compilation of recipes to introduce tests in legacy codebases. This was a hard read for me.
- [9] [Rails Test Types and the Testing Pyramid](https://robots.thoughtbot.com/rails-test-types-and-the-testing-pyramid)
- [10] [RSpec rails default helper files](https://relishapp.com/rspec/rspec-rails/docs/upgrade#default-helper-files)
- Announcement of two helpers, rails_helper and spec_helper in order to have a way to not load Rails in some tests.
- [11] [Fast Rails Tests](https://www.youtube.com/watch?v=bNn6M2vqxHE) - Corey Haines talk on fast tests
- [12] [Speeding Up ActiveRecord Tests](http://articles.coreyhaines.com/posts/active-record-spec-helper/) - Corey Haines
bog post in which he introduces an active_record_helper
- [13] [Speed Up Tests by Selectively Avoiding Factory Girl](https://robots.thoughtbot.com/speed-up-tests-by-selectively-avoiding-factory-girl)
- [14] [Use Factory Girl's build_stubbed for a Faster Test Suite](https://robots.thoughtbot.com/use-factory-girls-build-stubbed-for-a-faster-test)
- [15] [Single expectation test discussion](https://github.com/andreareginato/betterspecs/issues/5#issuecomment-9110114)
- [16] [Rails Testing Antipatterns: Fixtures and Factories](https://semaphoreci.com/blog/2014/01/14/rails-testing-antipatterns-fixtures-and-factories.html)
- [17] [The magic tricks of testing](https://www.youtube.com/watch?v=URSWYvyc42M) - a great talk on testing by Sandi
Metz. Some of the things she covers are explained in her book [6]
- [18] [RR 186 with Corey Haines](https://devchat.tv/ruby-rogues/186-rr-the-4-rules-of-simple-design-with-corey-haines)
- it has some great gems on Rails, architecture and gems.
- [19] [Unit tests vs class tests](http://blog.arkency.com/2014/09/unit-tests-vs-class-tests/)
- [20] [Units are Not Classes: Improving Unit Testing By Removing Artificial Boundaries]
- (https://www.rallydev.com/blog/engineering/units-are-not-classes-improving-unit-testing-removing-artificial-boundaries)
- [21] [Mocks and explicit contracts](http://blog.plataformatec.com.br/2015/10/mocks-and-explicit-contracts/)
- [22] [xUnit Test Patterns: Refactoring Test Code](http://www.amazon.com/xUnit-Test-Patterns-Refactoring-Code/dp/0131495054)
- Most resources that talk about anti patterns in tests end up referring to this book. I heard great things of it, but I
haven't read it yet.
- [23] [XUnit Test Patterns wiki](http://xunitpatterns.com/) - the wiki of the book [22] which contains some of the content described in the
book. It is a great resource.
- [24] [Mocks Aren't Stubs](http://martinfowler.com/articles/mocksArentStubs.html) - A great article by Martin Fowler
in which he explains the difference between mocks and stubs. He also explains the differences in the classical and
mockist approach to testing.
- [25] [Refactoring legacy code with tests](https://github.com/testdouble/contributing-tests/wiki/Refactoring-Legacy-code-with-tests)
- [26] [How to Stop Hating your Test Suite by Justin Searls](https://www.youtube.com/watch?v=VD51AkG8EZw&list=PLE7tQUdRKcyYqT3LHMg4iH270kfyENCpp&index=10)

