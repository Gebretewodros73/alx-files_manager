# alx-files_manager

This repository contains a file management system with various functionalities, including handling Redis connections, MongoDB operations, creating an Express server, user authentication, file uploads, and more.

## Project Structure

The project is organized into the following directories:

1. `utils`

1.1 `redis.js`

This directory contains the implementation of a Redis utility class named `RedisClient`. It includes methods to connect to Redis, check the connection status, get, set, and delete values.

Example usage in `main.js`:
```javascript
import redisClient from './utils/redis';

(async () => {
    console.log(redisClient.isAlive());
    console.log(await redisClient.get('myKey'));
    await redisClient.set('myKey', 12, 5);
    console.log(await redisClient.get('myKey'));

    setTimeout(async () => {
        console.log(await redisClient.get('myKey'));
    }, 1000*10);
})();
```

1.2 `db.js`

This directory contains the implementation of a MongoDB utility class named `DBClient`. It includes methods to connect to MongoDB, check the connection status, and retrieve the number of users and files in the database.

Example usage in main.js:

```javascript
import dbClient from './utils/db';

const waitConnection = () => {
    // ...
};

(async () => {
    console.log(dbClient.isAlive());
    await waitConnection();
    console.log(dbClient.isAlive());
    console.log(await dbClient.nbUsers());
    console.log(await dbClient.nbFiles());
})();
```

2. `routes`

2.1 `index.js`

This directory contains the implementation of an Express server with two endpoints:

* `GET /status` returns the status of Redis and MongoDB.
* `GET /stats` returns the number of users and files in the database.

Example usage:

```bash
# Check status
curl 0.0.0.0:5000/status

# Get statistics
curl 0.0.0.0:5000/stats
```

2.2.2 `UsersController.js`

This file contains the definition of an endpoint:

* `POST /users` creates a new user in the database based on the provided email and password.


