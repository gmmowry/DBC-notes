# Dalal

Virtual Attributes
* Helpful for changing forms in the view and to split information
* Example: 'full_name' field in the form but with a getter and setter method for first_name and last_name
* Helpful for testing, legacy databases


# Raj

Strong Parameters

* Data that you've entered in to your database with "required" in the actual html view is never validated, its just ensuring the field is filled out
* Therefore, your data is untrusted
* Strong parameters allows you to avoid crazy assignments 

```ruby

class PeopleController < ActionController::Base

def create
	Person.create(params[:person])
end

def update
	person = current_account.people.find(params[:id])
	person.update_attributes!(person_params)
	redirect_to person
end

private
	def person_params
	#pass a hash here setting params[:person]
	end

end

```
* Gem StrongParameters
* The issue is privileges like admin vs regular user
* new way to put it in Rails is to say params.permit(())


# Lele

Active Record 'serialize'

* A way of taking your database and returning strings
* Example: selling books online and books have specific attributes, but now we've dominated the marketplace - let's sell coffee pots! Coffee pots don't have the same attributes as books
```ruby
class Product < ActiveRecord::Base
	serialize :misc_attributes, Hash
end
```
* this can ONLY take ONE parameter because you're passing it a hash
* You can write your own serialize method if you want to, its complicated though
* Serialize uses 'dump' and 'load' --> they tell it to convert things into yaml strings
* Every time you save the object, it will try to reload it even if it hasn't been changed
* When you call Product.first.misc_attributes, it returns a hash



# Michael

Rails 3 v Rails 4

* Any version below Ruby 1.9.3 is not supported
* used to be a plugin folder under vendor - that is no longer there
* Tests have changed. Rails 3
** Models: test/units
** Helpers: test/units/helpers
** Controllers: test/function
* Tests in Rails 4
** test/models
** test/helpers
** test/controllers
** test/mailers
*ActiveRecord has changed: Post.find(:all, :condition {}) is now Post.where(condition)
** Now 'find' only returns the first object where the condition is true
* When a column or table is renamed, all the related indexes are renamed automatically for you
* No longer an ActiveRecord sessions storing method for security reasons
* New caching scheme
* 'hstore' - very similar to serializing your data
* New data types have been added
* live-streaming is now supported
* Encrypted cookies - be wary of storing sensitive information because its not BCrypted


| Rails 3 | Rails 4 |
| ---------|-----------|
| mass assignment | strong parameters |
| ```ruby
class User
	attr_accessible :name, :admin
end

class UserController <AR::Base
	def update
		user = User.find[:id]
		if user.amdmin?
			params.delete[:admin]
		end
	user.update_attributes
end ```
| 
```ruby
class UserController
	def update
		user = User.find[:id]
		user.update_attributes[:user_params]
	end
	def user_params
		p = params.require[:user]parames[:none]
		p.permit[:name].if user.admin?
		p
	end
end
```
|


# Helpers

Helpers are ONLY for views


