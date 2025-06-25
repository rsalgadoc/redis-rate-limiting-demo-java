# Basic Redis Rate-limiting Demo Spring (Java) 

This application demonstrates rate limiting using Redis and Spring.

---

# How it works?

## 1. How the data is stored:
<ol>
    <li>New responses are added key-ip:<pre> SETNX your_ip:PING limit_amount
 Example: SETNX 127.0.0.1:PING 10 </pre><a href="https://redis.io/commands/setnx">
 more information</a> 
 <br> <br>
 </li>
 <li> Set a timeout on key:<pre>EXPIRE your_ip:PING timeout
Example: EXPIRE 127.0.0.1:PING 1000 </pre><a href="https://redis.io/commands/expire">
 more information</a>
 </li>
</ol>
<br/>

## 2. How the data is accessed:
<ol>
    <li>Next responses are get bucket: <pre>GET your_ip:PING
Example: GET 127.0.0.1:PING   
</pre><a href="https://redis.io/commands/get">
more information</a>
<br> <br>
</li>
    <li> Next responses are changed bucket: <pre>DECRBY your_ip:PING amount
Example: DECRBY 127.0.0.1:PING 1</pre>
<a href="https://redis.io/commands/decrby">
more information</a>  </li>
</ol>
 

---

## How to run it locally?

#### Open the file server/.env.example and create a copy with the name .env, 
####  File to see the available environment variables. You may set these variables when you start the application.
    - REDIS_HOST: Redis server host
	- REDIS_PORT: Redis server port
	- REDIS_PASSWORD: Redis server password
	- REDIS_DB: Database Name

#### Run backend

1. Create a .env file, take example file .env.example as template.

2. From the root directory of the project, run the following commands:
``` sh
cd server
./gradlew bootRun
```

3. Point your browser to `localhost:5000`.
