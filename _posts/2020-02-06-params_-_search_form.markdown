---
layout: post
title:      "Params - search form "
date:       2020-02-07 00:25:39 +0000
permalink:  params_-_search_form
---


I'm doing this short blog about params to get a better understanding of params. So basically I'm adding a new function to my Boba app.

So you access data with params, where in my code, I'm accessing my tea's data. Inside of my controller, I call params to access form and URL query data. Also, it returns an params object.

	if params[:tea]
		@teas = Tea.where('name LIKE?', "%#{params[:tea]}"
	
Here, I want to read one value from this params hash. It's checking if the value exists, it will be nil if it doesn't exist. .where is filtering through the whole tea list that's stored in database based on what the user type in the search bar. 

and if whatever I typed in doesn't match any results, it will show the list of tea in the order I set in my model.

			else
					@teas = Tea.ordered
			end


So basically, when I hit search, its going to make a GET request. If the user didnt press search, or is landing on localhost:3000/teas or whatever that action routes will do Tea.ordered

This is my search form:

```
<%= form_tag(teas_path) do %>
  Tea <%= text_field_tag :tea, params[:tea] %>
  <%= submit_tag 'Search' %>
<% end %>
```







