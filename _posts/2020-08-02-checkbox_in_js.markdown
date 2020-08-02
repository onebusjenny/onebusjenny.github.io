---
layout: post
title:      "Checkbox in JS "
date:       2020-08-02 21:07:03 +0000
permalink:  checkbox_in_js
---

For this project, I'm using the same concept as my rails project for JS project. It's called "Boba Menu Generator", it's goal is to let user create boba they want (customizing its name, flavor and ingredients), and after the user create the boba(submitting the form). The newly created boba will be displayed right underneath the boba form, showing the rendered "li", which will have "Boba Name", "Tea Flavor" and "Ingredients" you chose. Along with a delete button, so you can delete the boba. 


One of the thing I spent most time on it was to display the ingredients, since I'm using a checkbox for showing ingredients selection, and also to save the selected ingredients and send that back to my db. Since my bobaName and bobaFlavor are both input "", so I can easily grab the value of it and display. However, for my ingredient checkboxes. I had to grab the checked boxes, create an array and then send it back in. After setting up Ingredient Adapter and the function get Ingredients(), so it goes and get my ingredients and trun it into json. Where my Bobas class will have access to. 

```
class IngredientAdapter{
        constructor(){
            this.baseUrl = 'http://localhost:3000/api/v1/ingredients'
    }

    getIngredients(){
        return fetch(this.baseUrl).then(res => res.json()
        )
    }
```

So after that, it comes to doing my checkbox for my ingredient in my main_right.js. Where in my createBoba function:

```
const ingredient_ids = Array.from(e.target).filter(
            ing => ing.type === 'checkbox' && ing.checked).map(
            input => input.value)
```

The Array.from() static method creates a new, shallow-copied Array instance from an array-like or iterable object, so I want to grab the checked boxes and create an array for ingredient_ids in to and iterate through it. I also called .filter() on it, in its literally way, I want the type of ing to equals in 'checkbox' and only grab the checked one. When I say .map() I want it to create a new array with the checked ingredients in it, which means the value of the input. 

So after all that work, it comes to where I use my renderCheckbox() function to render it in my Ingredient class:

```
class Ingredient {
    constructor(ingredientJSON){
        this.id = ingredientJSON.id
        this.name = ingredientJSON.name
    }

    renderCheckbox(){
        return `<input type="checkbox" name=${this.name} value= ${this.id} >
                <label>${this.name}</label>` 
    }
}
```

so I want the renderCheckbox() to return a checkbox with my ingredient's names on the side of each checkbox(which depends on how many ingredients I've set in my seed file, if I have 6 ingredients in my seed file, there will be 6 checkboxes, also by saying this.name, I can easily create label for each ingredients, so It can show on the page. 


