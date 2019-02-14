---
layout: post
title:  "npm-oauth2-server scope"
comments: true
categories: auth
date:   2019-02-15 00:08:24 +0900
---

> # npm-oauth2-server scope


Although call back function of 'validateScope' is optional, If you don't provide this function, oauth accept all of the request regardless scope.

All of the generated access token have no scope as you can see,


```json
{
    "_id" : ObjectId("5c530e969bd2ae127829b2ab"),
    "accessToken" : "6c4f475b41f76d1a28511e86226c5d2bb7937030",
    "accessTokenExpiresAt" : ISODate("2019-01-31T19:04:54.467Z"),
    "refreshToken" : "e699dbdff0aee6bd2b5065444eebc70fb17390e0",
    "refreshTokenExpiresAt" : Date(316908947094468),
    "client" : {
        "id" : "eW91cnRoZW9ubHlvbmU="
    },
    "user" : {
        "id" : "jdj9354@naver.com"
    },
    "__v" : 0
}
```

If you just simply that method, you can find that token is generated with scope.

```JSON
{
    "_id" : ObjectId("5c65f8000857ae3e70fcadcf"),
    "accessToken" : "c0bc2e6bc91984f203438aa11b9f11aa2b710f27",
    "accessTokenExpiresAt" : ISODate("2019-02-15T03:21:36.276Z"),
    "refreshToken" : "fe68f45bcde66ce4eb0117fc534f14e4581d676b",
    "refreshTokenExpiresAt" : Date(316910186496276),
    "scope" : "ADMIN",
    "client" : {
        "id" : "eW91cnRoZW9ubHlvbmU="
    },
    "user" : {
        "id" : "jdj9354"
    },
    "__v" : 0
}
```

This is a sample code for giving ADMIN scope to user who is made client account.

```javascript
module.exports.validateScope = function(user,client,scope){
    if(user.id == client.user.id)
        return "ADMIN";
    else
        return "USER";
}
```
