
# Build Docker Image and run docker container for NodeJS app.
Create a simple project using NodeJS. build docker image and using docker container run the docker image. Push NodeJs Project into docker hub  repositories.

  Prerequisite

1.	Install docker desktop on your local system.

https://docs.docker.com/desktop/install/windows-install/

2.	Install NodeJS and npm. 
3.	Install express and initialize simple Project.

    Step 1: Using NodeJS initialize simple express app.
    ```
    npm init -y
    ```
    Package.Json    
```json
{
  "name": "hey-nodejs",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "Start": "node index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

Step 2: 	Install express JS.
```
npm i express
```

Step 3:	Create index.js file to start node and execute the JS code.
Index.js
```json
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.json({
    "hey": "NodeJs"
  })
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})

```
Step 4: Start the application.
```
node index.js 
Example app listening on port 3000
```
Output:

Step 5: Create a docker file and containerized application.
1.	First log into docker hub.
2.	Using terminal command log into to docker.
```
docker login
```
Step 6: Create dockerfile to build docker image and deploy application in docker container.

Dockerfile
```
FROM node:slim
WORKDIR /app
COPY . /app
RUN npm install
EXPOSE 3000
CMD node index.js

```
Step 6:	Build docker image.
 ```
 docker build -t dharmaraj257/hey-nodejs:0.0.1.RELEASE .
 ```
 step 7:  Run docker image using docker container.     
 ```
 docker container run -d -p 3000:3000 dharmaraj257/hey-nodejs:0.0.1.RELEASE 
 ```

Step 8: 	Pushing docker image into docker hub Repositories.
```
docker push dharmaraj257/hey-nodejs:0.0.1.RELEASE 
```
Output:
![Alt text](<docker 4.png>)