# Complement
A food and beer pairing app

Link to deployed project:
https://bkhoffman.github.io/Complement/

Known issue:
The Edamam recipe search API is limited to 5 queries/minute because we are using the free-level of the API so if too many queries are attempted then any further queries will fail because of a 401 restricted error. If we continue to develop this app and want to market it then we would pay for a higher level of the API to remove this restrction.

Purpose:
We wanted to build an app that allowed you to take the ingredients you had on hand and get a list of possible recipes you could make as well as find out what beers would pair with your meal choice. We also wanted this to work in the opposite direction where you chose a type of beer, got a list of beers, and then found a food that would pair well with that beer.

How it works:
The app works by taking search queries presented by the user and performs an AJAX call on two different APIs. The first API we used was the Edamam Recipe Search which can take ingredients, types of food, or specific recipes. This returns a JSON array of up to 10 results with recipe titles, images, urls for the recipes, and arrays of ingredients. If a recipe isn't found then a modal pops up telling the user to try again with a less specific query. Validation of user input on the left side is performed using the JQuery Validation library that only allows alphabet characters and spaces. We selected which pieces of the AJAX response that we wanted and display them in bootstrap cards. This card when clicked then queries the second API, Punk, using the first word of the recipe title for the query. The Punk API JSON response includes food pairings for the beer so we perform the AJAX query for food pairings using that word. If the Punk API cannot find a matching beer for the food we catch the error and instead display no beer pairing found in the modal. This works in reverse if the user starts with a beer first. Upon a beer type being clicked, an AJAX call to Punk API is performed searching the beer type by title. From the response we pull the beer name, image, and ABV (alcohol by volume) for each beer and insert them into a bootstrap card. When that card is clicked we use the food pairing string from the beer result and use that as the query for the Edamam API.

How to use:
The user can either start on the left or right side of the page for inputs. On the left you can type in a list of ingredients, a specific meal/recipe, or even a type of food like thai, mexican, etc. This will return a list of up to 10 recipes. These recipes can then be clicked which pops up a modal with a link to the actual recipe, the list of ingredients, and the beer pairing. Each ingredient can then be clicked which will strike-through the item so you can use the app while shopping to cross out what you already have. The user can switch back and forth between the results and the search features by a button at the top. If the user instead starts on the right side of the page they must first choose a type of beer. This will then generate a list of up to 5 beers. Clicking on a beer will then generate the same modal but will find a recipe that pairs with the selected beer.

Functionality to add:
The Punk API only searches a single company's (BrewDog) database of beers. If we had access to other similar databases or had time we could write our own API to allow this to work with other local or micro breweries for promotion of their beers. We would like to add in the future include seperate lines for ingredient inputs that then act as chips so you can remove an ingredient to tweak the search query.

Some other future features include:

Saving favorite recipes
Comment section
Generate a printable shopping list from the ingredients you don't have on hand
Access the brewdog PDF page for the beer selected
Contributors:
This project is maintained and contributed to by Tyler Ward, Joshua Bradley, and Brad Hoffman. Background image was from subtlepatterns. All images were found using google search.
