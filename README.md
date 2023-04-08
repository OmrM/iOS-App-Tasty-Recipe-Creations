# MobileApp - MVP Group // Group #19


# Tasty Recipe Creations

### Description
I collaborated in a group project to develop an iOS app called Tasty Recipe Creations that helps users discover and save recipes. I contributed to the planning, wireframing, and development of user stories and interfaces. We used Figma, Xcode, and Parse Server to create an interactive prototype and implement features such as user login, recipe posting, recipe feed, recipe search, and favorite recipe list. I also participated in milestone planning and development, including creating a launch screen, login screen, adding app icon functionality, and the favorite button.
## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)
3. [Milestone 1](#Milestone-1)
4. [Milestone 2](#Milestone-2)

## Overview
The Tasty Recipe Creations app helps users discover and save recipes. Users can post their recipes, view a feed of other users' recipes, search for recipes, and add recipes to their favorite list.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User can login 
* User can sign up
* User can post photos 
* User can view a feed of recipes
* User can search for recipes
* User can favorite a recipe
* User can have a favorite list
* User can view others meals

**Optional Nice-to-have Stories**

* User can add someone
* User can add a comment to a photo
* User can like a photo
* User can talk with other users
* User can get help from others

### 3. Navigation

**Tab Navigation** (Tab to Screen)
* Home Screen
* Post Recipe Screen
* Saved Recipes Screen

**Flow Navigation** (Screen to Screen)
* Login Screen
    * => Sign Up Screen
    * => Home Screen
* Sign Up Screen
    * => Home Screen
* Home Screen (main page - allows us to select food category)
    * => Home Feed Screen (displays recipes of the selected category)
* Post Recipe Screen
    * => Post Success Screen
* Saved Recipes Screen
    * => Recipe Details Screen


## Wireframes
#### Login Flow
<img
src="https://i.imgur.com/cmMzouF.jpg" width=600>
#### App Flow
<img
src="https://i.imgur.com/BrGf7eI.jpg" width=600>


### [BONUS] Interactive Prototype

![](https://media.giphy.com/media/87rw1zTPSzW23lJ6QZ/giphy.gif)
[](https://www.figma.com/proto/ynUmzvnTVpUYKy2m0ljzIf/MVP-Recipes-app?page-id=0%3A1&node-id=11%3A1036&viewport=278%2C281%2C0.19&scaling=scale-down&starting-point-node-id=1%3A2)
> [Link to prototype: https://www.figma.com/proto/ynUmzvnTVpUYKy2m0ljzIf/MVP-Recipes-app?page-id=0%3A1&node-id=11%3A1036&viewport=278%2C281%2C0.19&scaling=scale-down&starting-point-node-id=1%3A2]

App Brainstorming


## Schema 
### Models
#### Recipe

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user posted recipe (default field) |
   | author        | Pointer to User| author of recipe posted|
   | recipeName    | String   | display name of recipe |
   | description   | String   | subtitle or description of recipe |
   | category      | String   | type of recipe (breakfast, lunch, dinner or dessert) |
   | image | File   | display image for the recipe |
   | directions    | String   | directions for the recipe |
   | preparationTime| Number | time in minutes that it will take to prepare the recipe |
   | cookingTime   | Number | time in minutes that it will take to cook the recipe |
   | createdAt     | DateTime | date when recipe is created (default field) |
   | updatedAt     | DateTime | date when recipe is last update (default field) |
   
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all Recipes where user is author
         ```swift
         let query = PFQuery(className:"Recipe")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let recipes = recipes {
               print("Successfully retrieved \(recipes.count) recipes.")
           // TODO: Do something with recipes...
            }
         }
         ```
      - (Read/Get) get all recipes of a specific category
         ```swift
         let query = PFQuery(className:"Recipe")
         query.whereKey("category", equalTo: selectedRecipeCategory)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let recipes = recipes {
               print("Successfully retrieved \(recipes.count) recipes.")
            }
         }
        ```
   - Create Recipe Screen
      - (Create/POST) Create a new recipe object
   - Profile Screen
      - (Read/GET) Query logged in user object
   - Saved Recipes screen
      - (Read/GET) Query user's favorited/saved recipes
      - (Delete) Delete saved recipes from saved list
      
      
      
 ## Milestone 1
 
This is the first milestone that will lead to the completion of our recipe book. It will allow a user to login or create an account.

Time spent: **7** hours spent in total

## User Stories

The following are completed functionalities:

- [x] User will be able to input login
- [x] User will be able to input password
- [x] Create launch screen
- [x] Create login screen

## Video Walkthrough

Here's a walkthrough of implemented user stories:

<img src='https://github.com/The-MVPs/MobileApp/blob/main/Recipes-App/gifs/milestone1loginpage.gif' title='Video Walkthrough' width='600' alt='Video Walkthrough' />


  
## Milestone 3.2
  
   This is a continuation of the third milestone out of four and further work will be done within the week on the favorite screen functionality. This milestone will allow the user to see the app icon on the home page and also added the button functionality of the favorite button. 

Time spent: **6** hours spent in total
  
## User Stories
  
The following are completed functionalities:

- [x] User will be able to see app icon on home screen
- [x] User can use the favorite button to like specific recipes
  
  Here's a walkthrough of implemented user stories:
  
  <img src='http://g.recordit.co/PZpPUY0C7x.gif' title='Video Walkthrough' width='300' alt='Video Walkthrough' />
