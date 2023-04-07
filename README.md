# MobileApp - MVP Group // Group #19


# Tasty Recipe Creations

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)
3. [Milestone 1](#Milestone-1)
4. [Milestone 2](#Milestone-2)

## Overview
### Description
The Tasty Recipe Creations app will allow users to look up and capture online recipes. It will allow them to get ideas for a meal plan. It was also provide instructions on how to cook that specific meal.

### App Evaluation

- **Category:** Recipes 
- **Mobile:** Users can use the app to get recipes for certain meals.
- **Story:** Users can post before and after picture of how their meal looked. 
- **Market:** Anyone who enjoys cooking and learning new recipes will enjoy this app.
- **Habit:** Users can use this app at anytime of the day. They can get recipes for any meal of the day. Breakfast, snack, lunch, dinner and dessert.
- **Scope:** V1 would allow users can post and view recipes with images and to view a timeline of recipes posted by other users. V2 would allow user to comment on, like, and favorite other users' recipes. 

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

### 2. Screen Archetypes
* Login Screen (Only shows up when not logged in)
    * User can login here
* Sign Up Screen (Only shows up when not logged in)
    * User can create an account here
* Home Screen 
    * User can choose what type of recipes they want to see:
        * Breakfast
        * Lunch
        * Dinner
        * Dessert
    * User can view recipes
    * User can search recipes
    * User can favorite recipes
* Creation Screen
    * User can post a recipe with  directions and an image
* Saved Recipes Screen
    * User can view favorited/saved recipes
    * User can view favorited/saved recipes’ details
    * User can unfavorite recipes
  

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
<img src="https://media.giphy.com/media/93D02kRJMY6T9thuIw/giphy.gif" width=600>

### [BONUS] Digital Wireframes & Mockups
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
===

## Favorite Existing Apps - List
1. Food Network Kitchen
1. Shef
3. Tasty
4. Yummly Recipes
5. AllRecipes


## Favorite Existing Apps - Categorize and Evaluate
### Food Network Kitchen
   - **Category:** Photo & Video / Social 
   - **Mobile:** Website is view only, uses camera, mobile first experience.
   - **Story:** Allows users to share their lives in pictures and enhance their content with filters
   - **Market:** Anyone that takes pictures could enjoy this app. Ability to follow and hashtag based on interests and categories allows users with unique interests to engage with relevant content.
   - **Habit:** Users can post throughout the day many times. Features like "Stories" encourage more candid posting as well. Users can explore endless pictures in any category imaginable whenever they want. Very habbit forming!
   - **Scope:** Instagram started out extremely narrow focused, just posting pics and viewing feeds. Has expanded to a somewhat larger scope including "Instagram Stories" (a la SnapChat) and messenger features. 

## New App Ideas - List
1. Recipe Book App
3. Social Media App
4. Outfit Ideas depending on Weather
5. Messenger App
6. Homework Help App

## Top 3 New App Ideas
1. Recipe Book App
2. Social Media App
3. Outfit Ideas depending on Weather App

## New App Ideas - Evaluate and Categorize
1. Student Behavior Tracker
   - **Description**: Allows teachers, students and parents to stay up to date with student behavior in real time. Teachers can acknowledge positive student behavior when it happens, students can receive instant positive reinforcement and parents can be more tuned in to how their child is doing at school.
   - **Category:** Social Networking
   - **Mobile:** Mobile is essential for the instant logging of student behavior. Students use the app to purchase goods from the student store and other rewards. The camera is used to share images with parents.
   - **Story:** Creates a team between student, parent and teacher. Allows good behavior to not go unnoticed and for students to get rewards and positive reinforcement from teachers, parents and peers
   - **Market:** Any school district or individual classroom teacher of any grade could utilize this app. District wide licensing and custom features could be used for monetization. 
   - **Habit:** Teachers are using this constantly throughout the school day. Students are using the app daily to check their performance and cash in on rewards.
   - **Scope:** V1 would allow teachers to access a roster of students and input behavior logs. Could actually be tested by a real teacher with a class of students. V2 would incorporate a student facing version for students to see their performance. V3 would add a way for students to earn and obtain rewards for goals met. V4 would incorporate a parent facing version.

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


  ## Milestone 2
  
 This is our second milestone out of four. This milestone will allow the user to be able to login and choose the type of meal they want. Then they will be able to see recipes. 

Time spent: **8** hours spent in total

## User Stories

The following are completed functionalities:

- [x] User will be able to move to the favorite list screen
- [x] User will be able to travel to the creation screen
- [x] Create meal screen
- [x] Create Tab Controller

## Video Walkthrough

Here's a walkthrough of implemented user stories:

<img src='http://g.recordit.co/tZfWNMUXbi.gif' title='Video Walkthrough' width='400' alt='Video Walkthrough' />


  ## Milestone 3
  
   This is our third milestone out of four. This milestone will allow the user to be able to post a recipe and add descriptions with other ideas too. The user will also be able to view other recipes. 

Time spent: **6** hours spent in total
  
## User Stories
  
The following are completed functionalities:

- [x] User will be able to post a recipe with name; description; ingredients; directions; image; prep time; and cooking time
- [x] User can view all recipes
- [x] Create recipe screen
- [x] User is able to click the type of meal they want whether its breakfast, lunch, or dinner
- [x] User is able to create a post
- [x] User is able to see a list of recipes
  
  
  Here's a walkthrough of implemented user stories:
  
  <img src='https://github.com/The-MVPs/MobileApp/blob/main/Recipes-App/gifs/postRecipeAndViewAllRecipes.gif' title='Video Walkthrough' width='600' alt='Video Walkthrough' />

  
## Milestone 3.2
  
   This is a continuation of the third milestone out of four and further work will be done within the week on the favorite screen functionality. This milestone will allow the user to see the app icon on the home page and also added the button functionality of the favorite button. 

Time spent: **6** hours spent in total
  
## User Stories
  
The following are completed functionalities:

- [x] User will be able to see app icon on home screen
- [x] User can use the favorite button to like specific recipes
  
  Here's a walkthrough of implemented user stories:
  
  <img src='http://g.recordit.co/PZpPUY0C7x.gif' title='Video Walkthrough' width='300' alt='Video Walkthrough' />
