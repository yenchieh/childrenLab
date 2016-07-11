# childrenLab


# www.childrenLab.com/api/login
* Params - email, password
* Return example: 
```
{
"username": "test@test.com",
"roles": [
"ROLE_USER"
],
"access_token": "4ncvvg81j5smer66avrgdasgvcncngd3",
"token_type": "Bearer"
}
```

* Exception: if email or password not match, the response status will be 403 Unauthorized
* Use the access_token to access other API. Put the token on the request header.
Ex:
```
 x-auth-token: 4ncvvg81j5smer66avrgdasgvcncngd3
```


# www.childrenLab.com/user/register
* Params(required) - email, password, phoneNumber, firstName, lastName
* other Params - birthday, nickName, sex, address, city, zipCode, role(2 type: ROLE_USER, ROLE_NANNY)
* The default role is ROLE_USER

* Exception example: 
```
{
"success": false,
"message": "The email already registered."
}
```

# www.childrenLab.com/user/isEmailRegistered
* Params - email
* Return example:
```
{
  "registered": true
}
```

# www.childrenLab.com/kids/add
* Params(required) - firstName, lastName, birthday(Format must be: "yyyy-MM-dd"
* Params(not required) - nickName, note

* Return example:
```
{
"success": true
}
```

# www.childrenLab.com/kids/edit
* Params(required) - kidId
* Params(not required) - firstName, lastName, birthday, nickName, note

* Return example:
```
{
"success": true
}
```

# www.childrenLab.com/kids/remove
* Params(required) - kidId

* Return example:
```
{
"success": true
}
```

# www.childrenLab.com/kids/list
* Return example:
```
{
    "success": true,
    "kids": [
        {
            "id": 2,
            "firstName": "test2",
            "lastName": "testLast2",
            "nickName": "testNick2",
            "birthday": "1985-09-30 12:00:00",
            "note": "hahaha"
        },
        {
            "id": 1,
            "firstName": "test",
            "lastName": "testLast",
            "nickName": "testNick",
            "birthday": "1985-08-29 12:00:00",
            "note": "hahaha, it's test"
        }
    ]
}
```

# www.childrenLab.com/avatar/temp
* Temp cloud place to store image
* Params(required) - img
* It return image byte format: data:image/png;base64

# www.childrenLab.com/avatar/uploadProfileImage
* Profile Image for user
* The image stored in http://avatar.childrenlab.com/'
* Params(required) - encodedImage (we should change it)
* Return example:
```
{
    "success": true,
    "profileImage": "1234521.png"
}
```

# www.childrenLab.com/avatar/uploadKidsProfileImage
* Profile Image for user
* The image stored in http://avatar.childrenlab.com/'
* Params(required) - encodedImage (we should change it), kidId
* Return example:
```
{
    "success": true,
    "profileImage": "1234521.png"
}
```

# www.childrenLab.com/calendarEvent/addEvent
* Event creation
* Params(required) - eventName, startDate, endDate, color, status, description, alert
* startDate and endDate format: yyyy/MM/dd HH:mm:ss
* Return example:
```
{
    "success": true
}
```


# www.childrenLab.com/calendarEvent/getEventsByUser
* Event creation
* Params - query, month, year, day
* query - month or day.
* If query == month, only month and year are required from parameters.
* If query == day, month, year, and day are required from parameters.
* month - integer
* year - integer
* day - integer
* Return example:
```
{
  "success": true,
  "events": [
    {
      "id": 17,
      "eventName": "Jehcd",
      "startDate": "2016-07-06 09:39:00",
      "endDate": "2016-07-06 09:40:00",
      "color": "pink",
      "status": "Open",
      "description": "",
      "alert": 43
    },
    {
      "id": 18,
      "eventName": "Tfvg",
      "startDate": "2016-07-06 09:42:00",
      "endDate": "2016-07-06 09:43:00",
      "color": "green",
      "status": "Open",
      "description": "",
      "alert": 48
    }
  ],
  "totalCount": 2
}
```

# www.childrenLab.com/calendarEvent/editEvent
* Params(required) - id, eventName, startDate, endDate, color, description, alert
* startDate and endDate format: yyyy/MM/dd HH:mm:ss
* Return example:
```
{
    "success": true
}
```


# www.childrenLab.com/calendarEvent/deleteEvent
* Params(required) - id
* Return example:
```
{
    "success": true
}
```

# www.childrenLab.com/device/uploadRawData
* Params(required) - rawData
* Raw Data Example: |MacID,X,Y,Z,U,V,TIME|
* Return example:
```
{
    "success": true
}
```

# www.childrenLab.com/device/uploadResultData
* Params(required) - macId, activity, calories, distance, receivedTime
* receivedTime is long - timestamp
* Return example:
```
{
    "success": true
}
```