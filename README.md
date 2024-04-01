# Block35-TheAcmeStore
## Overview
In this workshop you will be building an RESTFUL API which uses a data layer. This API will enable users to set their favorite products.
## Directions
You will have a similar setup to the guided practice.
You will need to create a new repository named the_acme_store
You will have a folder named server in that repository with 2 files within that folder:
  - index.js (will be your express application and setup functions, we called this init in guided practice)
  - db.js (this will be your data layer)

Your Data Layer (server/db.js) will need to export the following:
Each of these method can be tested in a setup function (we named our init in guided practice) in server/index.js. Make sure each one function works before moving on to the next. Use the guided practice as a reference.

client - a node pg client
createTables method - drops and creates the tables for your application
createProduct - creates a product in the database and returns the created record
createUser - creates a user in the database and returns the created record. The password of the user should be hashed using bcrypt.
fetchUsers - returns an array of users in the database
fetchProducts - returns an array of products in the database
fetchFavorites - returns an array favorites for a user
createFavorite - creates a favorite in the database and returns the created record
destroyFavorite - deletes a favorite in the database
Your Express Application (server/index.js) Should Have the Following RESTFUL Routes
You can test your routes by using curl or POSTMAN

GET /api/users - returns array of users
GET /api/products - returns an array of products
GET /api/users/:id/favorites - returns an array of favorites for a user
POST /api/users/:id/favorites - payload: a product_id
returns the created favorite with a status code of 201
DELETE /api/users/:userId/favorites/:id - deletes a favorite for a user, returns nothing with a status code of 204

The Database schema is shown below
User
  id (UUID)

  username (STRING)

  username (STRING) UNIQUE

  password (STRING) UNIQUE

Product
  id (UUID)

  name (STRING)

Favorite
  id (UUID)

  product_id (UUID REFERENCES products table NOT NULL)

  user_id (UUID REFERENCES users table NOT NULL) 

  CONSTRAINT combination of user_id and product_id should be unique 
