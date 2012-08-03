DBHouse
=

Union database driver framework, it aims to provide standard APIs to access any kinds of database. For further goals, making the union of all databases.

Installation
-
Using NPM to install DBHouse module directly:

    npm install dbhouse

Example
-

Querying MongoDB with specific condition:

    var DBHouse = require('dbhouse');
    
    /* Create connection with MongoDB */
    var dbHouse = new DBHouse;
    dbHouse.connect('mongodb', { host: 'localhost', port: 27017 }, function() {
    
      /* Create a database operator */
      var db = new DBHouse.Database(dbHouse);
      db.open('dbhouse')
    	  .collection('users')
    	  .where({
          '$or': [ { name: 'Fred Chien'}, { name: 'Stacy Li' } ]
        })
        .limit(1)
        .query(function(err, data) {
          if (err)
            throw err;
    
          console.log(data);
        });
    });

License
-
Licensed under the MIT License.

Authors
-
Copyright&copy; 2012 Fred Chien <<fred@mandice.com>>