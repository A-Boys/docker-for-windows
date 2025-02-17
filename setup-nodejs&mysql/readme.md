<center>
<h1>STEPS FOR SETTING UP NODEJS & MYSQL</h2>
</center>

<br>

### STEP 1: BUILD AN IMAGE FOR NODEJS & MYSQL

`docker build -t <name for your image mysql>  `

- Run this command in the directory containing the `Dockerfile`

<p>
    <pre>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker build -t mysql-db .
<br>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker build -t nodejs-app .
    </pre>
</p>

<br>

### STEP 2: RUN THE CONTAINER

- Use the following to run the container from your image:
  <br>
  _Note_: <br><pre><center>`THIS HELP YOU TO KNOW THE ALIAS OR THE VARIABLE TO PROPERLY RUN A CONTAINER`</center></pre><br>
  <br>`-d` = is for detach
  <br>`--name` = is container name
  <br>`-e` = is to set variables to pass into container
  <br>`-p` = is to publish port where in the `left-side` is the **_host machine port_** while the `right-side` is the **_port inside the container_**
  <br>`-v` or `--volume` = This mounts `/host/path` from the local system to `/container/path` **_inside the container_**.
  <br>`-w` or `--workdir`= the **_working directory_** where commands will run inside the container.
  <br>`--env-file` = Allows **_passing multiple environment variables_** stored in a file.

<p>
    <pre>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=thread_db -e MYSQL_USER=master -e MYSQL_PASSWORD=root -p 3306:3306 mysql:latest
<br>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker run -d --name my-app --link mysql-db:mysql -p 3000:3000 -v $(pwd):/app -w /app --env-file .env nodejs-app
    </pre>
</p>
<br>

### STEP 3: CHECK THE LOGS OF BOTH CONTAINER

- Run this command to check logs of running containers.
  <br>
  `docker logs <your-container-name>`

<p>
    <pre>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker logs mysql-db
<br>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ docker logs my-app
    </pre>
</p>

For `mysql-db`

- It must return like this:
<p>
    <pre>
2025-02-17T05:01:27.790662Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
2025-02-17T05:01:27.815987Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/run/mysqld/mysqlx.sock
2025-02-17T05:01:27.816010Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '9.2.0'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server - GPL.
    </pre>
</p>
<br>

For `my-app`

- It must return like this:

<p>
    <pre>
> appsdev-api-template@1.0.0 dev
> nodemon --watch src src/index.js

<span style="color:yellow">[nodemon] 3.1.9
[nodemon] to restart at any time, enter "rs"
[nodemon] watching path(s): src/\*_/_
[nodemon] watching extensions: js,mjs,cjs,json
</span><span style="color:green"><b>[nodemon] starting "node src/index/js"</b></span>
</pre>

</p>

<br>

### STEP 4: CHECK IF YOUR API ALREADY RUNNING ON `PORT 3000`.

<br>

- Run this command to check logs of running containers.

  `curl http://localhost:3000/v1`

<p>
    <pre>
<span style="color:green"><b>Ubuntu:</b></span><span style="color: blue">~</span>$ curl http://localhost:3000/v1
    </pre>
</p>

- It must return like this:
<p>
    <pre>
{
    "message": "Running on port 3000 🚀",
    "controller": "Home"
}
    </pre>
</p>
<br>
