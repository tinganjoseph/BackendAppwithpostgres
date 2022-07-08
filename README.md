installation packages
npm install express sequelize pg pg-hstore body-parser cors jsonwebtoken bcryptjs --save

Let me explain what we’ve just done:
– import express, body-parser and cors modules:

Express is for building the Rest apis
body-parser helps to parse the request and create the req.body object
cors provides Express middleware to enable CORS
– create an Express app, then add body-parser and cors middlewares using app.use() method. Notice that we set origin: http://localhost:8081.
– define a GET route which is simple for test.
– listen on port 8080 for incoming requests.

Now let’s run the app with command: node server.js.
Open your browser with url http://localhost:8080/, you will see:


//config
First five parameters are for PostgreSQL connection.
pool is optional, it will be used for Sequelize connection pool configuration:

max: maximum number of connection in pool
min: minimum number of connection in pool
idle: maximum time, in milliseconds, that a connection can be idle before being released
acquire: maximum time, in milliseconds, that pool will try to get connection before throwing error


Define the Sequelize Model
These Sequelize Models represents users & roles table in PostgreSQL database.

After initializing Sequelize, we don’t need to write CRUD functions, Sequelize supports all of them:

create a new User: create(object)
find a User by id: findByPk(id)
find a User by email: findOne({ where: { email: ... } })
get all Users: findAll()
find all Users by username: findAll({ where: { username: ... } })
These functions will be used in our Controllers and Middlewares.