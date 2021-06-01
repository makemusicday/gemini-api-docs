.. code-block:: json

  {
      "token": {
          "access_token": "ZyrIfSZqraXTmPaMlaRt2fxEsheoUZV6aWb5OlOT8o",
          "expires_in": 86400,
          "scope": [
              "profile",
              "performer",
              "venue"
          ],
          "token_type": "Bearer"
      },
      "user": {
          "_links": {
              "delete": {
                  "href": "/api/users/e5f34047-1f96-4881-8a46-3b1353bfafd9/delete",
                  "method": "POST",
                  "title": "Delete this user account."
              },
              "edit": {
                  "href": "/api/users/e5f34047-1f96-4881-8a46-3b1353bfafd9",
                  "method": "PATCH",
                  "title": "Edit this user account."
              },
              "get-conversations": {
                  "href": "/api/convos/user/e5f34047-1f96-4881-8a46-3b1353bfafd9",
                  "method": "GET",
                  "title": "Get all conversations for this user account."
              },
              "new-artist": {
                  "href": "/api/artist/e5f34047-1f96-4881-8a46-3b1353bfafd9/new",
                  "method": "POST",
                  "title": "Create a new performer profile for this user."
              },
              "new-artist-avatar": {
                  "content-type": "multipart/form-data",
                  "href": "/api/artists/avatar",
                  "method": "POST",
                  "title": "Upload a profile image in preparation for creating a performer profile for this user."
              },
              "new-selfmatch": {
                  "href": "/api/selfmatch/e5f34047-1f96-4881-8a46-3b1353bfafd9/new",
                  "method": "POST",
                  "title": "Create a new selfmatch event for this user."
              },
              "new-venue": {
                  "href": "/api/venue/e5f34047-1f96-4881-8a46-3b1353bfafd9/new",
                  "method": "POST",
                  "title": "Create a new venue profile for this user."
              },
              "self": {
                  "href": "/api/users/e5f34047-1f96-4881-8a46-3b1353bfafd9",
                  "method": "GET",
                  "title": "User data and profile information."
              }
          },
          "address": null,
          "allow_email_notifications": true,
          "artists": [],
          "cities": [],
          "email": "jazzified@example.com",
          "first_name": null,
          "has_confirmed_email": false,
          "id": "e5f34047-1f96-4881-8a46-3b1353bfafd9",
          "last_name": null,
          "locale": "en_US",
          "phone": null,
          "selfmatches": [],
          "venues": [],
          "zip_code": null
      }
  }
