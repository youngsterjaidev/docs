# server967

## Routes

`/users`
* [/users/ - getAllUsers](#getAllUsers)
* [/users/add - addUser](#addUser)
* [/users/uploads - uploads](#uploads)
* [/users/userId/:userId - getUser](#getUser)
* [/users/private-video/:email - getPrivateVideo](#getPrivateVideo)
* [/users/videos - getVideos](#getVideos)
* [/users/login - login](#login)

# getAllUsers
#### /users/

##### Parameters

`Request`
```javascript
let res = await axios({
   url: "http://localhost:8000/users/"
   method: "GET"
})
```

`Response`
```javascript
let res = {
    "_id": {
        "$oid": "614c335418eef4acd8447274"
    },
    "username": "test333@gmail.com",
    "email": "test333@gmail.com",
    "password": "$2a$10$3iDa5tDfC2J47G5hn5U0SehYWPqkDLevIb6Ifn9u1A0EC0kVrYoTG",
    "profilePicUrl": null,
    "bio": null,
    "videos": [{
        "videoId": {
            "$oid": "614c33bd18eef4acd8447275"
        },
        "filePath": "satisfy.mp4"
    }, 
    {
        "videoId": {
            "$oid": "614c33e518eef4acd8447277"
        },
        "filePath": "satisfy.mp4"
    }, 
    {
        "videoId": {
            "$oid": "61507e0346c02e6e54ebf754"
        },
        "filePath": "0001-0200.mp4"
    }],
    "time": 1632383828981
    }
```

# addUser
#### /users/add

##### Parameters

* email (required)
* password (required)
* username (required)

`Request`
```javascript
let res  await axios({
    url: "http://localhost:8000/users/login",
    method: "POST",
    data: {
        email: "test333@gmail.com",
        password: "test0000",
        username: "test333@gmail.com"
    }
})

```
`Response`
```javascript
let response = {
    message: "User created successfully !"
}
```




# Login
#### /users/login

##### Parameters

* email (required)
* password (required)

`Request`
```javascript
let res  await axios({
    url: "http://localhost:8000/users/login",
    method: "POST",
    data: {
        email: "test333@gmail.com",
        password: "test0000"
    }
})

```
`Response`
```javascript
let response = {
    auth_token: {
        
    },
    info: {
    "_id": {
        "$oid": "614c335418eef4acd8447274"
    },
    "username": "test333@gmail.com",
    "email": "test333@gmail.com",
    "password": "$2a$10$3iDa5tDfC2J47G5hn5U0SehYWPqkDLevIb6Ifn9u1A0EC0kVrYoTG",
    "profilePicUrl": null,
    "bio": null,
    "videos": [{
        "videoId": {
            "$oid": "614c33bd18eef4acd8447275"
        },
        "filePath": "satisfy.mp4"
    }, 
    {
        "videoId": {
            "$oid": "614c33e518eef4acd8447277"
        },
        "filePath": "satisfy.mp4"
    }, 
    {
        "videoId": {
            "$oid": "61507e0346c02e6e54ebf754"
        },
        "filePath": "0001-0200.mp4"
    }],
    "time": 1632383828981
    }
}
```