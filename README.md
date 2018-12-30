# DorsaLeague

To register or login do steps bellow :

Base url is :
http://79.175.155.143/Dorsabazar/api/


------------


- **Post user phone number by** 
POST `/register/RegisterRequest`

sample :
http://.../api/register/RegisterRequest?mobileNumber=0912***1234

response:
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": {
    "mobileNumber": "string"
  }
}
```

------------


- **Send verify code** and** get jwt** if phone number and sms key was currect
POST json params to `/register/VerifyCode`

**Params :**
```json
{
  "phoneNumber": "string",
  "code": "string",
  "deviceModel": "string",
  "deviceId": "string",
  "osType": "Android",
  "osVersion": "string",
  "fcmToken": "string",
  "appVersion": "string"
}
```

**and reponse is :**
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": "string"
}
```
which extra is jwt , used to add  Authorization in header to get or set user profile and othe api that contains user's information

**NOTE : add DeviceId in header too.**

sample :
`Authorization: Bearer [jwt]`
`DeviceId: [deviceId]`


------------


- **Get user profile information by call get method :**
GET  `/register/GetProfile?mobile=""`

NOTE : Moble is user's phone number
NOTE : Do not forget add Authorization in header


------------


- **If user profile was null you have to complete user information by below api **
POST `/register/SetProfile`

**Params :**
```json
{
  "firstName": "string",
  "lastName": "string",
  "imageUrl": "string",
  "phoneNumber": "string",
  "email": "string"
}
```
NOTE: do not forget add Authorization and DeviceId in header

**Response is :**
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": {
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "imageUrl": "string",
    "phoneNumber": "string"
  }
}
```

------------


- **To edit user information :**
PUT `/register/UpdateProfile`

Params :
```json
{
  "firstName": "string",
  "lastName": "string",
  "imageUrl": "string",
  "phoneNumber": "string",
  "email": "string"
}
```
NOTE: do not forget add Authorization and DeviceId in header

**Response:**
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": {
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "imageUrl": "string",
    "phoneNumber": "string"
  }
}
```

------------


- **To start user season call start menu call it when user come to app (on app resumed) :**
POST `/api/League/Start`

Params:
```json
{
  "mobileNumber": "string",
  "packageName": "string",
  "deviceId": "string"
}
```
NOTE: do not forget add Authorization and DeviceId in header


Response:
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": {
    "user": {
      "firstName": "string",
      "lastName": "string",
      "email": "string",
      "imageUrl": "string",
      "phoneNumber": "string"
    },
    "allowedTime": 0
  }
}
```
NOTE: allowedTime is long thas show how log user can be in app (in minutes)

------------


- **End user season by calling bellow api when user leave app (on pause app).**
POST `/League/End`

Params:
```json
{
  "mobileNumber": "string",
  "packageName": "string",
  "deviceId": "string"
}
```
NOTE: do not forget add Authorization and DeviceId in header


Response:
```json
{
  "ok": true,
  "messages": [
    {
      "code": 0,
      "description": "string"
    }
  ],
  "extra": true
}
```
