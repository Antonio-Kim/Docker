# Counting number of visits
This is a simple app using docker compose with multiple local containers. The docker
compose will build two separate containers, node and redis, and create a simple
app that counts number of visits the website had. To run the app,
```bash
docker-compose up
```
is all you need. You can run it silently by add __-d__ flag after "up". Now go on
to your browser and type in "__localhost:4001__" and refresh the page to increase
the numer of the counts. To stop all the containers
```bash
docker-compose down
```

## Configuration issues
There might be a case where your redis-server not configure properly when running
docker-compose. First, ensure that index.js has the following code after express:
```javascript
const app = express();
const client = redis.createClient({
    host: 'redis-server',
    port: 6379
});
```
Second, try using docker-compose down and then rebuilding the docker-compose once
again.
```bash
docker-compose down
docker-compse up --build
```

## Restart policies
These are useful commands to be used in docker-compose. See the file to find out
how to set this up.
| Restart Policies | Descriptions                                                           |
|------------------|------------------------------------------------------------------------|
| "no"             | Never attempt to restart this . container  if it stops or crashes      |
| always           | If the container stops "for any reasons", always attempt to restart it |
| on-failure       | Only restart if the container stops with an error code                 |
| unless-stopped   | Always restart unless the user forcibly stops it                       |