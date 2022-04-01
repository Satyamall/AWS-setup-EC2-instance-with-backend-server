
Problem
 - setup an ec2 instance
 - install apache server
 - run a node express application
 - ensure tcp is forwarded to correct port

View the Html Page: <a href="http://3.6.89.119:3000/">Click here</a>

Setup EC2 instance:
 - click on services
 - click on compute
 - click on instances
 - click on launch instances
 - Choose an Amazon Machine Image (AMI)
 - select the ubuntu server
 - choose Free tier eligible
 - click Next: Configure Instance Details
 - left default and click on Next: Add Storage
 - left default and click on Next: Add Tags
 - click on Add tag
 - fill the tags credential
   - Name  My application 2
   - dev   developers
   - data  01-04-2022
 - click on Next: Configure Security Group
 - click on Add Rule
   - choose SSH  custom IP address  satya
   - choose HTTP custom IP address  satya
 - click on Review and Launch
 - click on launch
 - choose a new key pair
 - choose pair name
 - Download Key Pair
 - click on Launch Instances

Use local Machine for handle
 - make a folder on Desktop => mkdir aws-setup-ec2-with-backend-server
 - mv backend_server.pem aws-setup-ec2-with-backend-server
 - cd aws-setup-ec2-with-backend-server
 - ssh -i "key pair file name" ubuntu@"paste the Public IPv4 DNS here"
 - Press Enter
 - sudo apt-get update
 - sudo apt-get install apache2
 - sudo apt-get install -y nodejs
 - check node => node
 - check node version => node -v
 - make src folder => mkdir src
 - cd src/
 - sudo apt install npm
 - npm init -y
 - npm i express --save
 - touch index.js
 - pico index.js
```js
    const express=require("express")
const app=express();

const PORT = process.env.PORT || 3000;

app.get("/",(req,res)=>{
    return res.send("Hello I am Satya, This is for AWS - setup EC2 instance with backend server")  
})

app.listen(PORT,()=>{
   console.log(`Listen on port ${PORT}`)
})
```
  - ctrl + S
  - ctrl + O
  - ctrl + L
  - ctrl + X
  - pico package.json
    // set up start in script
  - npm start
   // Public IPv4 address:3000 run in browser
 - cd 
 - killall -9 node
 - cd src/
 - sudo npm install pm2 -g
 - pm2 start index.js
 - pm2 monit

# Pictorial View:
![Screenshot (394)](https://user-images.githubusercontent.com/80479635/161309778-7b1881e6-f773-4f1d-a46e-30ccf52f4154.png)
