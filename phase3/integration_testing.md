Integration Testing 

How do you go from user stories to rspec tests? 
The tests and the application you are defining are driven by user stories, also known as behavior driven development.

1. Pick a user story and create the steps that go along with it.
2. Create a unit test.
3. Go back to your code and see what fails.
4. Write another user test.
5. Repeat. 

Don't forget to add Capybara gem and Selenium webdriver!!

Add specific features that you want for the user in spec/features

Feature and scenario are basically similar to 'describe' and 'context' but are from capybara.

Don't forget to put pending in front of your tests until you're ready for them. Helpful to pseudocode it out but not overwhelm yourself. 


spec/features/user_sees_all_purchases
```ruby
require 'rails_helper'

feature "user sees list of purchases" do
	scenario "ther are purchases" do
		visit '/purchases/new'
		fill_in "Amount", with: 2000
		fill_in "First name", with: "Duke"
		fill_in "Last name", with: "Greene"
		fill_in "CC number", with: '411111111111'
		fill_in "CC exp month", with: '11'
		fill_in "CC exp year", with: '18'
		click_button "Buy it now!"
	end

	expect(Purchase.count).to_not eq(0)

	expect(current_path).to eq('/purchases')

	purchase = Purchase.last
	expect(page).to
	expect(page).to
	expect(page).to
	
end
```
button name must match the name in the view, double check dummy.
Make sure that you redirect in the controller to match the redirect in the spec. Create routes and make sure you're moving on from each error to another error. 



config/routes.rb
```ruby
Rails.application.routes.draw 




