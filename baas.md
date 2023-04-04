# Baas
The API server that provide service to store the videos and create users 

### Hosted URl - [baas](https://blackbaas.vercel.app/)

## Routes

`/users`
* [/users/ - getAllUsers](#getAllUsers)
* [/users/add - addUser](#addUser)
* [/users/uploads - uploads](#uploads)
* [/users/userId/:userId - getUser](#getUser)
* [/users/private-video/:email - getPrivateVideo](#getPrivateVideo)
* [/users/videos - getVideos](#getVideos)
* [/users/login - login](#login)
* [/users/azure/uploads - getAzureBlobStorage](#getAzureBlobStorage)
* [/users/azure/uploads - getAWSS3BucketsList](#getAWSS3BucketsList)
* [/users/aws/buckets/:bucketName - getCreateAWSS3Bucket](#getCreateAWSS3Bucket)
* [users/aws/buckets - getAWSS3BucketsList](#getAWSS3BucketsList)
* [/aws/buckets/:bucketName - getCreateAWSS3Bucket](#getCreateAWSS3Bucket)
* [/aws/buckets/:bucketName - deleteAWSS3Bucket](#deleteAWSS3Bucket)
* [/aws/buckets/:bucketName/objects](#getAWSS3BucketObjects)
* [/aws/buckets/:bucketName/upload](#uploadAWSS3BucketObject)

# getAllUsers
Fetch all the Users 
#### `GET` - /users/

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/"
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
    url: "https://blackbaas.vercel.app/users/login",
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
    url: "https://blackbaas.vercel.app/users/uploads",
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
    url: "https://blackbaas.vercel.app/users/userId/:userId",
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
    url: "https://blackbaas.vercel.app/users/private-video/:email",
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
    url: "https://blackbaas.vercel.app/users/login",
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
Get all the list of blob in the Azure blob storage Container

#### `GET` - /users/azure/uploads

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/azure/uploads"
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

## postAzureBlobStorage
Uploading the file to the AZURE blob storage service
#### `POST` - /users/azure/uploads

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/azure/uploads"
   method: "POST"
})
```

Response
```javascript
let response.data = {
    mesage: "File Uploaded Successfully"
}
```

# AWS (AMAZON Web Services)

## getAWSS3BucketsList
List all the buckets in AWS S3
#### `GET` - /users/aws/buckets/

##### Parameters

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/aws/buckets"
   method: "GET"
})
```

Response
```javascript
let response.data = [
        {
            "Name": "elasticbeanstalk-us-east-1-823978677915",
            "CreationDate": "2020-11-30T13:47:53.000Z"
        },
        {
            "Name": "infna-ready",
            "CreationDate": "2022-05-25T07:49:48.000Z"
        },
        {
            "Name": "infna-teset",
            "CreationDate": "2022-05-25T08:58:57.000Z"
        },
        {
            "Name": "r-ere",
            "CreationDate": "2022-05-25T18:20:24.000Z"
        },
        {
            "Name": "rando-red",
            "CreationDate": "2022-05-25T18:19:55.000Z"
        },
        {
            "Name": "random-re",
            "CreationDate": "2022-05-25T18:19:26.000Z"
        }
    ]
```

## getCreateAWSS3Bucket
Create a bucket in the AWS S3

#### `GET` - /users/aws/buckets/:bucketName

##### Parameters
* bucketName (required) 

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/aws/buckets/:bucketName"
   method: "GET"
})
```

Response
```javascript
// infna-okay is the bucketName
let response.data = {
    Location: "http://infna-okay.s3.amazonaws.com/"
}
```

## deleteAWSS3Bucket
Delete a bucket in the AWS S3

#### `GET` - /users/aws/buckets/:bucketName

##### Parameters
- bucketName (required) 

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/aws/buckets/:bucketName"
   method: "DELETE"
})
```

Response
```javascript
let response.data = {
    message: "Bucket deleted Successfully"
}
```

## getAWSS3BucketObjects
List alle the objects of a bucket in the AWS S3

#### `GET` - /users/aws/buckets/:bucketName/objects

##### Parameters
- bucketName (required) 

Request
```javascript
let res = await axios({
   url: "https://blackbaas.vercel.app/users/aws/buckets/:bucketName/objects"
   method: "GET"
})
```

Response
```javascript
let response.data = [
    {
        "Key": "package.json",
        "LastModified": "2022-05-25T08:14:10.000Z",
        "ETag": "\"78a6cef94bfdbe82726da49f951a3b56\"",
        "ChecksumAlgorithm": [],
        "Size": 294,
        "StorageClass": "STANDARD",
        "Owner": {
            "ID": "13a4c53bacd679aab39f85376ff4b014db7c06a2b1c8f3d7fb78faceb87b2eec"
        }
    },
    {
        "Key": "page4.png",
        "LastModified": "2022-05-26T16:43:36.000Z",
        "ETag": "\"33b6d0bf988f414d0d4dea46f41b0e3a\"",
        "ChecksumAlgorithm": [],
        "Size": 26929,
        "StorageClass": "STANDARD",
        "Owner": {
            "ID": "13a4c53bacd679aab39f85376ff4b014db7c06a2b1c8f3d7fb78faceb87b2eec"
        }
    },
    {
        "Key": "rd.png",
        "LastModified": "2022-05-26T16:42:25.000Z",
        "ETag": "\"4d09a1241892e4194c16f6acedecd856\"",
        "ChecksumAlgorithm": [],
        "Size": 168067,
        "StorageClass": "STANDARD",
        "Owner": {
            "ID": "13a4c53bacd679aab39f85376ff4b014db7c06a2b1c8f3d7fb78faceb87b2eec"
        }
    },
    {
        "Key": "xWR6mvVAsMYg2356HUUAuN.jpg",
        "LastModified": "2022-05-25T16:01:23.000Z",
        "ETag": "\"8f43dbeaeca61cc0289bae553b9927b8\"",
        "ChecksumAlgorithm": [],
        "Size": 285200,
        "StorageClass": "STANDARD",
        "Owner": {
            "ID": "13a4c53bacd679aab39f85376ff4b014db7c06a2b1c8f3d7fb78faceb87b2eec"
        }
    }
]
```

## uploadAWSS3BucketObject
List alle the objects of a bucket in the AWS S3

#### `POST` - /users/aws/buckets/:bucketName/upload

##### Parameters
- bucketName (required) 

Request
```javascript
let res = await axios({
   url: "https://baas0.com/users/aws/buckets/:bucketName/objects"
   method: "GET"
})
```

Response
```javascript
let response.data = []
```
