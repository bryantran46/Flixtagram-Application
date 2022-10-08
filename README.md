# Flixtagram

## Table of Contents
1. [Overview](#Overview)
2. [Product Spec](#Product-Spec)
3. [Wireframes](#Wireframes)
4. [Build Progress](#Build-Progress)

## Overview
### Description
Social media app that allows friends to talk share their love for movies. Users can see what movies are currently in theaters and post what movies they're going to watch. An extra feature would be allowing users to purchase movie tickets within the app. 

### App Evaluation
- **Category:** Social, Movies
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer, such as tinder or other similar apps. Functionality wouldn't be limited to mobile devices, however mobile version could potentially have more features.
- **Story:** App has the current lineup of movies in theaters. Additionally, there will be accounts to follow your friends and create meetups. 
- **Market:** Movie goers
- **Habit:** Everytime a user wants to watch a movie in theaters, they will check the app and can message their friends to tag along
- **Scope:** World Wide

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

- [X] User can see movies 
- [X] User can create an account
- [X] User can login
- [X] User can logout
- [X] User can create posts
- [X] User can view posts from friends
- [X] User can comment on posts

**Optional Nice-to-have Stories**

- [ ] User can delete posts
- [ ] User can like posts 
- [ ] User can add friends 
- [ ] Send a notification of new movies
- [ ] User can add a profile picture
- [ ] Profile pictures are shown for posts and comments

### 2. Screen Archetypes

* Login
    * User can login
* Register 
   * User can create a new account 
* Profile Screen 
   * Allows user to upload a photo and fill in basic information
* Now playing
   * User can access movies and their synopsis
   * User will be given a notifications of new movies coming out
* Stream
    * User can view a feed of posts
    * User can heart a headsUp to like the post
* Creation
    * User can post to their feed

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Movie Browsing
* Posts Feed

**Flow Navigation** (Screen to Screen)

* Login/Registration
   * Movie Browsing
* HeadsUp Feed
   * Post Creation

## Wireframes
<img src="https://github.com/CodePath-IOS-2022-Project/SurfsUp/blob/main/sketch.png" width=600>

### [BONUS] Digital Wireframes & Mockups
<img src="https://github.com/CodePath-IOS-2022-Project/SurfsUp/blob/main/FigmaWireframe.png" width=600>

### [BONUS] Interactive Prototype
<img src="https://github.com/CodePath-IOS-2022-Project/SurfsUp/blob/main/prototype.gif">

## Schema 
### Models

Login
| Property | Type | Desciption |
| -------- | -------- | -------- |
| objectId    |String    | unique id for user|
|username|ptr to string|user's username|
|password|ptr to string|user's password|

Home
| Property | Type | Description |
| -------- | -------- | -------- |
| objectId    | String | unique id for each movie |
| movieTitle | String | title of the movie |
|movieImage | file | poster of the movie |
|synopsis| string | synopsis of the movie |


Feed
| Property |Type | Description |
| -------- | -------- | -------- |
| objectId  | String     |unique id for the user post (default field)    |
|author|	Pointer to User	|image author|
|image|	File|	image that user posts|
|caption	|String	|image caption by author
|commentsCount|	Number|	number of comments that has been posted to an image|
|createdAt	|DateTime|	date when post is created (default field)|
|updatedAt|	DateTime|	date when post is last updated (default field)|


Post
| Property |Type | Description |
| -------- | -------- | -------- |
| objectId  | String     |unique id for the user post (default field)    |
|author|	Pointer to User	|image author|
|image|	File|	image that user posts|
|caption	|String	|image caption by author
|commentsCount|	Number|	number of comments that has been posted to an image|
|createdAt	|DateTime|	date when post is created (default field)|
|updatedAt|	DateTime|	date when post is last updated (default field)|

### Networking
* Login Screen
    - Creates new data on parse
    - Retrieves existing data on parse  

* Home 
    - Query movie title, poster, and synopsis

* Post
    - Adds to data base 

* Feed 
    - Query parse data base for image/comments
    ```swift
    let query = PFQuery(className:"Post")
    query.whereKey("author", equalTo: currentUser)
    query.order(byDescending: "createdAt")
    query.findObjectsInBackground { (posts[PFObject]?, error: Error?) in
       if let error = error { 
          print(error.localizedDescription)
       } else if let posts = posts {
          print("Successfully retrieved \(posts.count) posts.")
        }
    }```

## Build Progress
### Sprint 1
<img src=https://github.com/CodePath-IOS-2022-Project/SurfsUp/blob/main/sprintOne.gif>

### Sprint 2
After evaluating our first sprint, we decided to change our project from a social media app targeted towards surfers, to be a social media app targeted towards movie lovers. 

<img src=https://github.com/CodePath-IOS-2022-Project/Flixtagram/blob/main/sprint2.gif>

### Sprint 3
Due to time constraints, we were unable to fully finish the "Optional Nice-to-have Stories." 

<img src=https://github.com/CodePath-IOS-2022-Project/Flixtagram/blob/main/sprint2.gif>

