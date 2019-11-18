---
layout: post
title:      "Having multiple ingredients in my bubble tea object"
date:       2019-11-18 06:23:58 +0000
permalink:  having_multiple_ingredients_in_my_bubble_tea_object
---


While working on my project, I ran into a big problem where it takes me forever to figure out. I'm going to talk briefly about what my project is about. My app is a bubble tea generator, I came up with this idea just because bubble tea is my favorite drink. 
So, how does it actually work. I want my user to be able to name their own bubble tea, type out the tea flavors the user want and most importantly, to be able to choose multiple ingredients for their personalized bubble tea. 
The project is asking to use belongs_to and has_many between models, where I thought wasn't confusing at all. However, when I was creating my form for bubble_teas/new (when I want to create a new bubble tea) I got the first two input parts fine, which is where the input is text part with the name and the tea flavor.

<h1>Customize your bubble tea</h1>

<form action="/bubble_teas" method="POST">
<label>Name:</label>

  <br><br>

<input type="text" name="bubble_tea[name]" id="bubble_tea_name">

  <br><br>

 <label>Tea Flavor:</label>
 <br><br>
 <input type="text" name="bubble_tea[flavor]" id="bubble_tea_flavor">

When it comes to ingredients, nothing showed. WHY?
So I went back to my models thinking why this is still not working. I ended up creating a join table for Ingredients and Bubble Tea since there's one bubble tea with multiple ingredients and different user should be able to select different ingredients. Also, the ingredient doesn't belong to just one bubble tea object. So that's when join table comes in. Bubble tea #1 has ingredient #1 and #2 and Bubble tea #2 has ingredient #1 and #3.

These are the models I have: bubble_tea, bubble_tea_ingredient and Ingredient models and User

class BubbleTea < ActiveRecord::Base

    belongs_to :user
    has_many :bubble_tea_ingredients
    has_many :ingredients, through: :bubble_tea_ingredients
    validates :name, :flavor, presence: true

    def has_ingredients?
        self.ingredients.any?
    end
		
class BubbleTeaIngredient < ActiveRecord::Base

    
    belongs_to :bubble_tea
    belongs_to :ingredient

    validates :bubble_tea, :ingredient, presence: true

end

class Ingredient < ActiveRecord::Base

    has_many :bubble_tea_ingredients
    belongs_to :bubble_tea
    validates :name, presence: true
end


class User < ActiveRecord::Base

    validates_presence_of :user_name, :user_email, :password
    has_secure_password
    has_many :bubble_teas
  end
	
and the last part where I display all my ingredients in checkbox form that users will be able to select the ingredients they want for their bubble tea and that the ingredient will be reusable for other users.

<% @ingredients.each do |ingredient| %>
    <input type="checkbox" name="bubble_tea[ingredient_ids][]" 
    id= "<%= ingredient.id%>" value = "<%= ingredient.id%>">
    <%=ingredient.name%> 
    <br><br>
  <% end %>
  
	
	and of course the submit button in the end with the text "Create bubble tea" on the button that user will press when they submit the form.
  
  <input type="submit" value="Create bubble tea">
</form>

In addition, for my ingredients to have their individual names. I didn't hard code in the list, instead I went to my seed file to manually add the name of each ingredients into my database, so I can have something to work with.

Ingredient.create(name: "Tapioca")
Ingredient.create(name: "Coconut Jelly")
Ingredient.create(name: "Red Bean")
Ingredient.create(name: "Pop Jelly")
Ingredient.create(name: "Brown Sugar Tapioca")
Ingredient.create(name: "Aloe")

