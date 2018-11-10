---
layout: post
title:  "oauth2-server npm study"
date:   2018-11-06 00:04:00 +0900
---

> ## oauth2-server study
![oauth2-server-npm](/assets/oauth2-server-npm.PNG)

> ## Installation
![oauth2-install](/assets/oauth2-install.PNG)

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
|getAccessToken(accessToken, [callback])|O|Retrieve saved token|
---
## Client vs User

### Client
3rd Party apps/servies which utilize oauth system.

### User
Actual users who use the 3rd party app/service.

---
