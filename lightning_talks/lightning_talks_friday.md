# Nicole

Using AJAX with Rails

These notes are not complete, get Nicole's fake repo. 

controller
```ruby
class TasksController < AC

	respond_to :html, :js

end
```

index.html.erb
```ruby
<%= link_to 'New Task', new_task_path, remote: true%>
```

new.html.erb
```ruby
$('#form-container').html("<%= j (render 'form) %>")
```

_form.html.erb
```ruby
<%= simple_form_for @task, remote: true do |f| %>

```

create.html.erb
```ruby
$('#tasks').html("<% j (render @tasks) %>");
```




# Nell

HAML 

HTML abstraction mark-up language
Ruby-based, DRY, generates the mark-up for you under the hood
Able to exist and communicate with the browser, but cuts out work for you
Preserves all the semantics
You can add blocks and loops into it, you can render partials easily

HAML
```html
#classname
	stuff
	.idname
		morestuff

#newclassname
	stuff
```

How to add a block
```html
#classname
	stuff
	-ruby do loop
		content
```
