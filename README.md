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
## User APIs
### /auth/register
- Create a user by taking data from a request body .
- Password Should be in Encrypted Format.
- __Response format__
  - _**On success**_ - Return HTTP status 201 with user document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### /auth/login
- Allow an user to login with their email and password.
- __Response format__
    - _**On success**_ - Return HTTP status 200 and JWT token in response body.
    - _**On error**_ - Return a suitable error message with a valid HTTP status code.

## Post APIs
### /posts
- Create Post by taking the data from request body.
- __Response format__
    - _**On success**_ - Return HTTP status 201 and Post Into in response body.
    - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### /posts/
- Get all the posts.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the post document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.

### /posts/:userId/posts
- Get all the posts.
- __Response format__
  - _**On success**_ - Return HTTP status 200 and returns the post document.
  - _**On error**_ - Return a suitable error message with a valid HTTP status code.