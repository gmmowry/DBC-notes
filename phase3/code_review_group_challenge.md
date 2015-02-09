# Code Review Notes from Rebecca


* Make sure to link to github user profiles
* How to Install on ReadMe should be how a developer would install it
* Make sure commit messages aren't vague


Specs
* use 'describe' in higher level tests for controllers
* for route tests, you can put them in a new folder called 'requests' subfolder in spec folder. Requests folder is a new thing, so we may just have an older version of rspec 
* Add things like 'describe 'GET #index' do' 
* Never push commented out code to master, even when you're working on a function that's not done and need help - always have people pull from your branch
* for testing a method to create new user/comment/etc. use factorygirl and then test to make sure it increased the count by 1
* get rid of the deprecation warning for 'should' with the shoulda matcher tests with doing 'it { expect(subject).to validate_presence_of :email }'


Code
* need to add the csrf authenticity token into the json to get around the errors
* For strong_params, you can use params.merge( {commenter_id: current_user.id, post_id: post.id} ) OR use strong_params then iterate through the block and set author_id, commenter_id, etc to something else with current_user or post.id, etc. 
* can say 'render json: {comment: @comment, user: current_user }' instead of the whole 'respond_to do |format|....end' so the ajax can know that information 
* Dont use .find_by anymore since its no longer supported
* be consistent about using 'current_user' if you provide it
* Pay attention to readability of the code - add a few extra lines of whitespace for readability after the code is functional
* Refactor the vote code to clean it up, set defaults, etc.
* sessions_controller: 'render :js => "window.location = '/'"' hurts Rebecca's heart! As does 'remote true' because things start to get messy
* You can put things that are included in multiple models (like votes) into the concerns directory
* Move the comment/reply form options hash into a helper to refactor and be able to test it
* Make sure to handle errors with the ajax calls for appending new comments/replies (look at the user one)
* The authenticity token for the header and the comments/replies don't match. You need to put into the form the csrf token by putting in '_hidden' - there is a link over the weekend to a stackoverflow that explains this
* Might as well just write all the ajax in the application.js file/directory - try not to do it all over. Don't forget to handle errors!
* split the ajax into multiple files
* Try to do OOJS in the ajax so you can set up objects! You could keep things in their own separate place. Require the other .js files in the application.js file but store them in the same directory
* render the partial as html not as Json since we're already rendering it
* Looks at application first for all your css, and you can change that if you want by setting it up in the production/dev/test environment files if you want
* 