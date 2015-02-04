Lightning Talk Notes

If you want a rabbit hole: http://martinfowler.com/articles/mocksArentStubs.html

* Background on TDD

Most of the time, TDD is referring to unit testing. The class you are testing is called SUT - System Under Test. Very few classes operate entirely in isolation, so they rely on other classes/objects to function. These other classes are known as Collaborators. 

 * What is a Double?
 	* generic term for any object that stands in for a real object during a test, most of the time a Collaborator
 	* name came from "stunt double"
 	* doubles are "strict" - any message you have not allowed or expected will trigger an error
 	* you can switch a double to "loose": chain 'as_null_object' off of 'double' and then it will return itself for any message/return value that is not explicity allowed or accepted
 	* pass a hash of allowed messages and return values for it to return true

 ```ruby
 Rspec.describe "A test double" do
 	it "returns canned responses from the methods named in the provided hash" do
 		dbl = double("Some Collaborator", :foo => 3, :bar => 4)
 		expect(dbl.foo).to eq(3)
 		expect(dbl.bar).to eq(4)
 	end
 end
 ```

 * What are the kinds of doubles?
  * Dummy (placeholder, don't really care what it does because it just needs to exist, don't care about missing method bodies)
  * Stub (placeholder but we do care about what it does, but it usually returns canned responses)
  * Spies (like a stub, but is used to maintain state and make assertions)
  * Fake (like a stub, but cannot be used for production because it usually contains a shortcut)
 * What is a Mock?  help control the context in a code example by letting you set the known return values, fake implementations of methods, and even set expectations that specific messages are received by an object. You can do these things on test doubles or you can do them on objects that are a part of your system. 
 Still a double, but while the other kinds of doubles build upon each other, mocks are different. All these test doubles before handle assertions on state but mocks make assertions on behavior. Mocks say that when you call a method with this parameter, and if you don't, there's an error.
 * Three phases of Mocks
  * Creating the instance
  * Defining the behaviour
  * Asserting the calls

 Must call 'verify' at the end - this is the key differentiator between mocks and other doubles

 ```ruby
 fooMock = mock(Foo.class);
 when(fooMock.bar()).thenReturn("baz", "qux");
 verify(fooMock, times(2)).bar();
 ```
 	
* Why use a mock? when you want to handle state and behavior at the same time! 


Example time! Transfer class that handles transfers between two accounts, source and destination. Source and Destination are our Collaborators. 

First context is an interaction, hence the use of a mock (behavior and state!). Notice how the stub and mock change between the two methods, depending on the test and who it is referring to. 

 ```ruby
describe Transfer do
  context "transfer with amount of 10" do
    it "should decrease source account by 10" do
      source_account      = mock('source account')
      destination_account = stub('destination_account').as_null_object
     
      source_account.should_receive('decrease').with(10)
     
      transfer = Transfer.new(source_account, destination_account, 10)
      transfer.call
    end
 
    it "should increase destination account by 10" do
      source_account      = stub('source account').as_null_object
      destination_account = mock('destination_account')
     
      destination_account.should_receive('increase').with(10)
     
      transfer = Transfer.new(source_account, destination_account, 10)
      transfer.call
    end
  end
end
```

OR you can make them both doubles to refactor your test code. Notice how the doubles have hash values in order to specify what they are expecting back. 

```ruby
describe Transfer do
  context "transfer with amount of 10" do
    let(:source_account) { double('source account', :decrease => nil) }
    let(:destination_account) { double('destination_account', :increase => nil) }
 
    it "should decrease source account by 10" do
      source_account.should_receive('decrease').with(10)
     
      transfer = Transfer.new(source_account, destination_account, 10)
      transfer.call
    end
 
    it "should increase destination account by 10" do
      destination_account.should_receive('increase').with(10)
     
      transfer = Transfer.new(source_account, destination_account, 10)
      transfer.call
    end
  end
end
```