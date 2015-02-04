Rspec Documentation: relishapp.com

rspec to test for associations

```ruby
describe Employee do
	let(:employee) { Employee.new }

	describe "validations" do
		it "has many positions" do
			expect(Employee.new).to respond_to(:positions)
		end

		it "has many evalutions" do
			expect(Employee.new).to respond_to(:evaluations)
		end

	describe "#increment_probation_count" do
		it "sets to 1 on first probation" 
			expect {
				employee.increment_probation_count
			}.to change { employee.probation_count }
		end

		it "saves the update to the database" do
			employee.name = "Rebecca"
			employee.emmail = "rmw@dbc.com"
			employee.probation_count = 7
			employee.save

			expect {
				employee.increment_probation_count
				employee.reload
				#employee reload will cache the object in the database
			}.to change { employee.probation_count}
		end
	end

	describe "#determine_sentiment" do

		let(:evaluation) { Evaluation.create!(body: "string of actual evaluation") }

	end
end
```

```ruby

describe "callbacks" do
	it "call #determine_sentime after save" do
		e = Evaluation.new(body: "Great job!")
		rqeuire(e).to receive(:determine sentiment
		e.save
	end
end
```


Mocks vs. Stubs

```ruby
expect {
	some stuff
}.to change() 
#This does an action, then sets expectations

analayst = double(SentimentAnalyzer.new)
allow(Sentiment Analyzer).to receive(:new)with(evluation.body) 
#this sets expectations, then does the action
```

Spies
```ruby
it "doesn't call #update_employee_probation_count on update" do
	e=spy('evaluation')
	e.sentiment = 2
	e.save
	expect(e).to_not have_received(:update_employee_probation_count)
end
```
Spies area like doubles, but better.


