# server967
The API server that provide service to store the videos and create users 

### Hosted URl - [Server967](https://server967.herokuapp.com/)

## Routes

`/users`
* [/users/ - getAllUsers](#getAllUsers)
* [/users/add - addUser](#addUser)
* [/users/uploads - uploads](#uploads)
* [/users/userId/:userId - getUser](#getUser)
* [/users/private-video/:email - getPrivateVideo](#getPrivateVideo)
* [/users/videos - getVideos](#getVideos)
* [/users/login - login](#login)
* [/azure/uploads - getAzureBlobStorage](#getAzureBlobStorage)
* [/azure/uploads - postAzureBlobStorage](#postAzureBlobStorage)

# getAllUsers
Fetch all the Users 
#### `GET` - /users/

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://server967.herokuapp.com/users/"
   method: "GET"
})
```

Response
```javascript
let response.data = [{
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
    }]
```

# addUser
Add some User
#### `POST` - /users/add

##### Parameters

* username (required)
* email (required)
* password (required)

Request
```javascript
let res.data = await axios({
    url: "https://server967.herokuapp.com/users/login",
    method: "POST",
    data: {
        email: "test333@gmail.com",
        password: "test0000",
        username: "test333@gmail.com"
    }
})

```
Response
```javascript
let response = {
    message: "User created successfully !"
}
```

# uploads
Upload a video to the Server
#### `POST` - /users/uploads

##### Parameters

* email (required)
* title (required)
* isPrivate (required)
* video - [video] (required)

Request
```javascript
let data = new FormData()
data.append("email", "test333@gmail.com")
data.append("title", "First Video")
data.append("isPrivate", false)
data.append("video", [video])

let res = await axios({
    url: "https://server967.herokuapp.com/users/uploads",
    method: "POST",
    data: data 
})

```
Response
```javascript
let response = {
    message: "Uploaded successfully!"
}
```

# getUser
Get a particular User Info
#### `GET` - /users/userId/:userId

##### Parameters

* userId (required)

Request
```javascript
let res = await axios({
    url: "https://server967.herokuapp.com/users/userId/:userId",
    method: "GET",
})

```
Response
```javascript
let response = {
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

# getPrivateVideo
Get the private video of some user
#### `GET` - /users/private-video/:email

##### Parameters

* email (required)

Request
```javascript
let res = await axios({
    url: "https://server967.herokuapp.com/users/private-video/:email",
    method: "GET",
})

```
Response
```javascript
let response = {
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


# Login
Login to the server
#### `POST` - /users/login

##### Parameters

* email (required)
* password (required)

Request
```javascript
let res  await axios({
    url: "https://server967.herokuapp.com/users/login",
    method: "POST",
    data: {
        email: "test333@gmail.com",
        password: "test0000"
    }
})

```
Response
```javascript
let response = {
    auth_token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2MzI3NDAzMTEsInVzZXJuYW1lIjoiaHB2MjYwMUBnbWFpbC5jb20iLCJlbWFpbCI6ImhwdjI2MDFAZ21haWwuY29tIiwiaWF0IjoxNjMyNzI1OTExfQ.Xyww9EM0IGyS3kK6MuRGcP0y2JfErzce5i51UINinP8",
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

# Azure

## getAzureBlobStorage
#### `GET` - /users/azure/uploads

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://server967.herokuapp.com/users/azure/uploads"
   method: "GET"
})
```

Response
```javascript
let response.data = {
    "title": "Home",
    "viewName": "Index",
    "accountName": "server967storage",
    "containerName": "azurelearnstorage",
    "thumbnails": [
        {
            "OrMetadata": "",
            "properties": {
                "Content-Encoding": "",
                "Content-Language": "",
                "Content-CRC64": "",
                "Content-MD5": "",
                "Cache-Control": "",
                "Content-Disposition": "",
                "createdOn": "2022-04-07T10:23:00.000Z",
                "lastModified": "2022-04-07T10:23:00.000Z",
                "etag": "0x8DA1880977EFDA9",
                "contentLength": 100243,
                "contentType": "image/jpeg",
                "blobType": "BlockBlob",
                "leaseStatus": "unlocked",
                "leaseState": "available",
                "serverEncrypted": true,
                "accessTier": "Hot",
                "accessTierInferred": true
            },
            "name": "042209310791208265-Screenshot from 2021-12-10 15-26-17.png"
        },
        {
            "OrMetadata": "",
            "properties": {
                "Content-Encoding": "",
                "Content-Language": "",
                "Content-CRC64": "",
                "Content-MD5": "",
                "Cache-Control": "",
                "Content-Disposition": "",
                "createdOn": "2022-04-07T10:39:52.000Z",
                "lastModified": "2022-04-07T10:39:52.000Z",
                "etag": "0x8DA1882F2D92D10",
                "contentLength": 7862921,
                "contentType": "video/mp4",
                "blobType": "BlockBlob",
                "leaseStatus": "unlocked",
                "leaseState": "available",
                "serverEncrypted": true,
                "accessTier": "Hot",
                "accessTierInferred": true
            },
            "name": "8127780786159935-2022-02-14 20-20-26.mkv"
        },
        {
            "OrMetadata": "",
            "properties": {
                "Content-Encoding": "",
                "Content-Language": "",
                "Content-CRC64": "",
                "Cache-Control": "",
                "Content-Disposition": "",
                "createdOn": "2022-04-07T07:32:34.000Z",
                "lastModified": "2022-04-07T07:32:34.000Z",
                "etag": "0x8DA1868C85B4380",
                "contentLength": 33129,
                "contentType": "image/png",
                "contentMD5": {
                    "type": "Buffer",
                    "data": [
                        216,
                        35,
                        146,
                        91,
                        44,
                        1,
                        240,
                        109,
                        98,
                        116,
                        110,
                        206,
                        3,
                        216,
                        182,
                        231
                    ]
                },
                "blobType": "BlockBlob",
                "leaseStatus": "unlocked",
                "leaseState": "available",
                "serverEncrypted": true,
                "accessTier": "Hot",
                "accessTierInferred": true
            },
            "name": "Notiy.png"
        }
    ]
}
```