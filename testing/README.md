# Testing

- Prefer tests where all its 4 steps (setup/exercise/verfication/teardown) are clearly identifiable - This helps make
tests easy to understand. [1] [2]

- Avoid the use of let/let!/before - The use of these Rspec constructs over nested describe/context blocks tends to
spread the multiple steps of testing over different blocks which makes what is happening in these steps harder to
understand. [3]

- Don't test private methods - Private method tests create unnecessary coupling between the tests and the implementation
details of an object and they break encapsulation. Testing private methods is an additional barrier to refactoring
(because tests also have to be changed even if the object's API and behaviour is kept the same). Testing private methods
is unnecessary because their behaviour is covered by public methods. [6] [5] [4]

- Remember that the purpose of tests is to catch regressions, provide documentation, and reduce costs (i.e. time
and money) and help with application design - When in doubt remember this. [1][6]

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
- This is book is a must read if you program in Ruby or in any OO language. There is a great section on testing.
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
