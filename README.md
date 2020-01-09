###Notes for Installations for backend.###

- npm init -y


- npm install knex,
            sqlite3,
            dotenv,
            cors,
            helmet,
            morgan,
            express


- npm install nodeman --save -dev 
    
    *(configure under scripts in package.json)
     "server": "nodemon index.js",
     "start": "nodemon index.js"


- knex init (for knexfile.js)

        *delete staging and production

        *add (under development)     
        client: "sqlite3",
        useNullAsDefault: true, // needed for sqlite

        *copy/past (under seeds)
         pool: {
      afterCreate: (conn, done) => {
        // runs after a connection is made to the sqlite engine
        conn.run("PRAGMA foreign_keys = ON", done); // turn on FK enforcement
      },

- setup: server.js, index.js, db.config.js files and .env file.

    *index.js
        const server = require('./server.js');

const PORT = process.env.PORT || 4000;

server.listen(PORT, () => {
    console.log(`Listening on port ${PORT}...`);
});

    *server.js
        const express = require('express');

const recipeRouter = require('./recipes/recipe-router');

require('dotenv').config()

const server = express();

server.use(express.json());
server.use('/api/recipes', recipeRouter);

server.get("/", (req, res, next) => {
    res.send("<h4>I am your sanity check. Hello!</h4>")
})

module.exports = server;

    *.env   
        PORT = 4000

- knex migrate:make <filename>

- knex migrate:latest

- knex seed:make 00-<table_name>

- knex seed:run

- npm run server

- (Then make router and model files)

Have fun!