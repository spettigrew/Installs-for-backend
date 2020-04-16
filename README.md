### Notes for Installations for backend.

- npm init -y


- npm install

Notes for Installations for backend.

npm init -y

### Can find installs on https://www.npmjs.com/
#### npm install

            knex
            sqlite3
            dotenv
            cors
            helmet
            morgan
            express
            bcryptjs(hash)
            connect-session-knexfile
            jsonwebtoken (web tokens)
            jest (testing)
            * pkg.json "jest": "testEnvironment": "node"
            supertest (node.js testing)
            * test script in pkg.json "test": "jest --watch --verbose"


#### npm install nodeman --save -dev 
(configure under scripts in package.json)


     "server": "nodemon index.js",

     "start": "nodemon index.js"


#### knex init 
(for knexfile.js)

        * delete staging and production

        * add (under development)     
        client: "sqlite3",
        useNullAsDefault: true, // needed for sqlite

        * copy/past (under seeds)
         pool: {
      afterCreate: (conn, done) => {
        // runs after a connection is made to the sqlite engine
        conn.run("PRAGMA foreign_keys = ON", done); // turn on FK enforcement
      },

- setup: server.js, index.js, db.config.js files and .env file.

    - index.js
        const server = require('./server.js');

        const PORT = process.env.PORT || 4000;

        server.listen(PORT, () => {
        console.log(`Listening on port ${PORT}...`);
        });


    - server.js
        const express = require('express');

        const nameOfRouter = require('./file/file-router');

        require('dotenv').config()

        const server = express();

        server.use(express.json());
        server.use('/api/file', fileRouter);

    server.get("/", (req, res, next) => {
        res.send("<h3>I am your sanity check. Hello!</h3>")
        })

    module.exports = server;

    *For your .env file*
    
        .env   
        PORT = 4000

*Run in terminal*

- knex migrate:make (filename)

- knex migrate:latest

- knex seed:make 000_1 (table_name) *and so on. Make all seed #'s the same amount of digits.*

- knex seed:run

*(Then make your router and model files)*

npm run server -run app
npm test - run tests

## HEROKU 
in terminal: *

 - heroku addons: create heroku-postgresql:hobby -dev -a (project name)
 - heroku run bash -a (project name)

Have Fun! Go make something great!