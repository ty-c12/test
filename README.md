# Image Share System

Description: Server-side app for sharing image with the implementation of MongoDB.<br>

Group: 25<br>
Names:<br>
Chan Tsz Yi (13434884)<br>
Ting Kenneth Charles (13338614)<br>
Raja Arbab Mahmood (13275291)<br>
Rejul Rai (13347518)<br><br>

The server is configured to list on port 8080.<br>
To run the server locally: https://localhost:8080

===========================================================================
## Login/logout
Default users (username/password):
- Developer: (developer/developer)
- Guest: (guest/guest)

===========================================================================
## Register
Register is available with the following constraints:
- No space for username
- Certain format requirement for password (at least 8 characters)
- Password and re-entered password should be identical

===========================================================================
## Post
A full page for viewing a post by a user.<br>
User can view their latest post in index, while a link to create posts will be rendered to users without any posts.<br>
In default, the user developer has a post.<br>
Function within a post:
- Like
- Posting a comment

===========================================================================
## Create/upload
User can upload an image to the database.<br>
There are multiple error handlings:
- No files being upload
- File failed to be uploaded to the database

After successful upload, a preview of the uploaded image will be rendered in the create page<br>
User can be redirected to the relevant image post upon clicking the preview image.

===========================================================================
## Profile
User can view own and others' profiles<br>
User can edit one's username, description, and password.

===========================================================================
## Delete
After login
- They can delete their profile or delete specific photo

Upon deleting an account, all data relevant to the specific account will be removed from the database.

===========================================================================
# Restful
In this project, there are four HTTP request types: post, get , put, and delete.

- Post
  - Post request is used for creating/adding.
    - Path URL for creating post: /create
    - Path URL for creating account/register: /register
    - Test (creating post): curl -X POST -H "accept: application/json" --data '{"photo": "<photo>", "username": "<username>", "filename": "<filename>", "size": "<size>", "date": "<date>", "data": "<data>", "like": [], "comment": []}' http://localhost:8080/create
    - Test (register): curl -X POST -H "accept: application/json" --data '{"username":"<username>", "password":"<password>", "desc":"<password>"}' http://localhost:8080/register

- Get
  - Get request is used for find.
    - Path URL for images list from certain poster: /search/<username>
    - Path URL for a certain image: /post/<postID>
    -Path URL for a certain poster's profile: /profile/<usermame>
    - Test (images list from poster): curl -X GET "accept: application/json" http://localhost:8080/search/<username>
    - Test (image): curl -X GET -H "accept: application/json" http://localhost:8080/post/<postID>
    - Test (profile): curl -X GET -H "accept: application/json" http://localhost:8080/profile/<username>

- Put
  - Put request is used for update.
    - Path URL for update user: /profile/<username>
    - Path URL for like post: /post/<postID>/like
    - Path URL for comment post: /post/<postID>/comment
    - Test (update user): curl -X PUT -H "accept: application/json" --data '{"username": "<username>", "password": "<password>", "desc", "<desc>"}' http://localhost:8080/profile/<username>
    - Test (like): curl -X PUT -H "accept: application/json" --data '{"like": "<username>"}' http://localhost:8080/post/<postID>/like
    - Test (comment): curl -X PUT -H "accept: application/json" --data '{"comment": ["<username>", "<commentText>"]}' http://localhost:8080/post/<postID>/comment

- Delete
  - Delete request is used for deletion.
    - Path URL for delete user: /profile/<username>
    - Path URL for delete photo: /post/<postID>
    - Test (user): curl -X DELETE -H "accept: application/json" http://localhost:8080/profile/<username>
    - Test (photo): curl -X DELETE -H "accept: application/json" http://localhost:8080/post/<postID>