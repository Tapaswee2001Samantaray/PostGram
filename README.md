# Post-Gram

```yaml
Post Gram is fully Responsive MERN App with Authentication, Likes, Dark Mode, A user can add/remove a friend 
into his/her friend list and He/She can upload a post .
```
To Start Backend Server
- Go inside Server folder .
```yaml
    Step1: Clone repo to your local
    Step2: npm i 
    Step3: create a .env file and add "MONGO_URL" , "PORT" and "JWT_SECRET"
    Step4: npm start
```
To Start Frontend Server
- Go inside client folder .
```yaml
    Step1: npm i 
    Step2: npm start
```
## Backend Includes
- Post and User Model
- auth , posts , users controller
- auth middleware
- auth , posts and users routes
- index file

### Models
- Post Model
```yaml
    {
    userId: {
        type: String,
        required: true
    },
    firstName: {
        type: String,
        required: true
    },
    lastName: {
        type: String,
        required: true
    },
    location: String,
    description: String,
    picturePath: String,
    userPicturePath: String,
    likes: {
        type: Map,
        of: Boolean
    },
    comments: {
        type: Array,
        default: []
    }
},
    { timestamps: true }
```
- User Model
```yaml
    {
    firstName: {
        type: String,
        required: true,
        min: 2,
        max: 50
    },
    lastName: {
        type: String,
        required: true,
        min: 2,
        max: 50
    },
    email: {
        type: String,
        required: true,
        max: 50,
        unique: true
    },
    password: {
        type: String,
        required: true,
        min: 5
    },
    picturePath: {
        type: String,
        default: ""
    },
    friends: {
        type: Array,
        default: []
    },
    location: String,
    occupation: String,
    viewedProfile: Number,
    impressions: Number
},
    { timestamps: true }
```
## Auth APIs
### POST /auth/register
- Create a user by taking data from a request body .
- Password Should be in Encrypted Format.
- __Response format__
  - _**On success**_ - Return HTTP status 201 with user document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### POST /auth/login
- Allow an user to login with their email and password.
- __Response format__
    - _**On success**_ - Return HTTP status 200 and JWT token in response body.
    - _**On error**_ - Return a suitable error message with a valid HTTP status code.

## Posts APIs
### POST /posts
- Create Post by taking the data from request body.
- __Response format__
    - _**On success**_ - Return HTTP status 201 and Post Into in response body.
    - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### GET /posts/
- Get all the posts.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the post document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### GET /posts/:userId/posts
- Get a user post.
- Read userId from Request Params.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the post document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### PATCH /posts/:id/like
- Update the like whether it is Liked or Disliked.
- Read id of the post from params . 
- Get UserId from request body.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the updatedPost document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

## Users APIs
### GET /users/:id
- Get the User .
- read id of the user from Params.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the user document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### GET /users/:id/friends
- Get the User's Friends.
- read id of the user from Params.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the Friends document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### PATCH /users/:id/:friendId
- Update user's friend list whenever a user add or remove a friend from his/her friend list.
- read id of the user and friendId from Params.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the updated Friends document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

## Middleware
### Authentication
- Make sure all the restricted routes are protected.

## Front-End
### Register
![App Screenshot](https://github.com/Tapaswee2001Samantaray/PostGram/blob/main/ScreenShots/Register.png?raw=true)