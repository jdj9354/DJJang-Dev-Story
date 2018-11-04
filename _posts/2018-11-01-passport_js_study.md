---
layout: post
title:  "Passport.js study"
date:   2018-11-01 01:53:00 +0900
---

> ## Passport.js installation

```alias
$ npm install passport --save
```

![install_cmd](https://jdj9354.github.io/DJJang-Dev-Study/assets/install_cmd.PNG)

![package_capture](https://jdj9354.github.io/DJJang-Dev-Study/assets/package_capture.PNG)


> ## Strategy

As I undestand, strategy means specific authentication policy and implementation.
There are many strategy on http://www.passportjs.org/packages/
(502 startegies 2018-11-04)

When establish passport based auth system, you should specify strategy which you will use.
(As a parameter on <span style="color:blue"> authentifcate </span> function)

You can npm install strategy.

> ## OAuth 2.0 strategy

Passport include OAuth2.0 also.
First, npm install oauth strategy

```alias
$ npm install passport-oauth --save
```

passport-oauth strategy includes both auth1.0 and auth2.0

>## Google OAuth Strategy

There is strategy for google oauth also.

```alias
$ npm install passport-google-oauth
 ```

 Once you install the npm packages, setup it.

```alias
var passport = require('passport');
var GoogleOauth2Strategy = require('passport-google-oauth').OAuth2Strategy;

app.use(passport.initialize());
app.use(passport.session());

passport.serializeUser(function(user, done) {
    done(null, user);
});

passport.deserializeUser(function(obj, done) {
    done(null, obj);
});


passport.use(new GoogleStrategy({
    clientID: GOOGLE_CLIENT_ID,
    clientSecret: GOOGLE_CLIENT_SECRET,
    callbackURL: "http://www.example.com/auth/google/callback"
  },
  function(accessToken, refreshToken, profile, done) {
       done(null,profile);
  }
));
```

In case of clientID, clientSecret, you can get it from Google Console.
(https://console.cloud.google.com/apis/credentials/oauthclient/)
The callbackURL is a URL which is called after authentication processed.
You should use same url for callbackURL as you used on google console.


```alias
app.get('/auth/google',
    passport.authenticate('google', { scope: ['https://www.googleapis.com/auth/plus.login'] }));

// GET /auth/google/callback
//   Use passport.authenticate() as route middleware to authenticate the
//   request.  If authentication fails, the user will be redirected back to the
//   login page.  Otherwise, the primary route function function will be called,
//   which, in this example, will redirect the user to the home page.
app.get('/oauth/google/callback',
    passport.authenticate('google', { failureRedirect: '/login' }),
    function(req, res) {
        res.redirect('/');
    });

```

Register your endpoint for google auth and callback for Google auth.
Then, you can confirm your simple Google OAuth processed on your end point.


![login](https://jdj9354.github.io/DJJang-Dev-Study/assets/login.PNG)


![googlelogin](https://jdj9354.github.io/DJJang-Dev-Study/assets/googlelogin.png)

![indexpage](https://jdj9354.github.io/DJJang-Dev-Study/assets/indexpage.PNG)
