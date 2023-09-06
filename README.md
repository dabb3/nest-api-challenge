## BACKEND ENGINEERING TASK

This project is a challange proposed by Payever for the position of Back-end Engineer. It`s a task to create a simple REST application from scratch, using Nest.js, Typescript, MongoDB, RabbitMQ and communicating with an external API (https://reqres.in/) .

## Technologies  

I used in this project, those technologies:

- [Node.js](https://nodejs.org/en/)
- [Nest.js](https://nestjs.com/)
- [MongoDB](https://www.mongodb.com/)
- [Typescript](https://www.typescriptlang.org/)
- [RabbitMQ](https://www.rabbitmq.com/)

## API/ENDPOINTS

In this project I used *Postman* to test API's request as it's a framework that I already know how to use it.

1. POST /api/users  
This request will keep the information from user entry in *MongoDB*. Once data is created, the application will send an email to 'user.email' with a welcome message and RabbitMQ event.
2. GET /api/user/{userId}  
This request will bring data from an external API and returns a user based on userId in JSON with dummy information.
3. GET /api/user/{userId}/avatar  
This resquest will bring an image from the 'user.data', store the image in the File System and generate a hash that will be used to name the .jpg file and also the 'user.avatar' value.
4. DELETE /api/user/{userId}/avatar  
This request will remove the image file from the File System storage and 'user.avatar' *MongoDB* entry. 

## AUTOMATION:
To run the automated tests, in any environment you are, run:

``` bash
npm run test
```
``` bash
npm run test:cov
``` 
*npm run test:cov* will give you the coverage of unit tests. For this project, the only missing one is the *users.service.ts* file. Which will be done sooner as possible.

## IMPORTANT TO REMEMBER:
To start *MongoDB* database, open a prompt and type: 
``` bash
mongosh databaseName
```
On my case:
``` bash
mongosh nest
```

After installing RabbitMQ, search for *RabbitMQService - start* on windows search bar to start RabbitMQ.
The same process can be done by *RabbitMQService - stop* to stop RabbitMQ.
I used *MongoDB* and *RabbitMQ* locally. No cloud framework was used in this project.