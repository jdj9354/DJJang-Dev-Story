---
layout: post
title:  "oauth2-server npm study"
comments: true
categories: auth
date:   2018-11-06 00:04:00 +0900
---

> ## oauth2-server study
![oauth2-server-npm](/assets/oauth2-server-npm.PNG)

> ## Installation & Document
![oauth2-install](/assets/oauth2-install.PNG)
Document
https://oauth2-server.readthedocs.io/en/latest/

> ## Example
const OAuth2Server = require('')



> ## Model
Each oauth2 server should contain Model.
Model is something like interface to estalbish oauth2 server.

npm oauth2-server contains following functions.
It contains mandatory / optional functions.
If you don't implement optional method, oauth2-server provide its default fucntion.

|Function|isMandatory|Description|
|---|---|---|
|generateAccessToken(client, user, scope, [callback])|X|Generate a new token|
|generateRefreshToken(client, user, scope, [callback])|X|Refresh a new token|
|generateAuthorizationCode(client, user, scope, [callback])|X|Generate a new AuthorizationCode|
|getAccessToken(accessToken, [callback])|O<br>(if OAuth2Server#authenticate() is used)|Retrieve saved token|
|getRefreshToken(refreshToken, [callback])|O<br>(if the refresh_token grant is used)|Retrieve saved refresh token|
|getAuthorizationCode(authorizationCode, [callback])|O<br>(if the authorization_code grant is used)|Retrieve saved authorizationCode|
|getClient(clientId, clientSecret, [callback])|O<br>(for all grant types)|Retrieve a client|
|getUser(username, password, [callback])|O<br>(if the password grant is used)|Retrieve a user|
|getUserFromClient(client, [callback])|O<br>(if the client_credentials grant is used)|Retrieve user that associated with client|
|saveToken(token, client, user, [callback])|O<br>(for all grant types)|Save access token|
|saveAuthorizationCode(code, client, user, [callback])|O<br>(if the authorization_code grant is used)|Save authorizationCode|
|revokeToken(token, [callback])|O<br>(if the refresh_token grant is used)|Revoke refresh token|
|revokeAuthorizationCode(code, [callback])|O<br>(if the authorization_code grant is used)|Revoke authorizationCode|
|validateScope(user, client, scope, [callback])|X|Check scope for a given client/user|
|verifyScope(accessToken, scope, [callback])|O|Check scope for a given token|

<br>

> ## OAuth 2.0 base knoledge
---


---
## Grant type
Grant type means how to grant request for auth.
There are several grant types, and these are basic grant types.


### 1. Authorization Code
### 2. Implicit
### 3. Password
### 4. Client Credentials
### 5. Device Code
### 6. Refresh Token

---

I used mongodb as storing various information
(User, Client, Token, AUthCode)
