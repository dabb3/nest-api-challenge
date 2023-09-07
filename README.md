## BACKEND ENGINEERING TASK

This project is a challenge proposed by Payever for the position of Back-end Engineer. It`s a task to create a simple REST application from scratch, using Nest.js, Typescript, MongoDB, RabbitMQ and communicating with an external API (<https://reqres.in/>) .

## TECHNOLOGIES  

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

## TESTING

To run the tests, in any environment, use:

``` bash
npm run test
```

``` bash
npm run test:cov
```

*npm run test:cov* will give you the coverage of unit tests. For this project, the only missing one is the *users.service.ts* file. Which will be done sooner as possible.

## HOW TO SEE RABBITMQ EVENT SENDING EMAIL?

1. Create an account on [Send Grid](<https://app.sendgrid.com>) .
2. Configure your account and configure the *apikeys* username and password.
3. Configure a *.env* file using those params configured:

    For MongoDB configuration use:

    ``` bash
    MONGO_URI=mongodb://127.0.0.1:27017/yourDatabaseName?directConnection=true
    ```

    For Mailer configuration use:

    ``` bash
    MAILER_HOST=smtp.sendgrid.net
    ```

    Default value for MAILER_USER:

    ``` bash
    MAILER_USER=apikey
    ```

    Your apikey password that Send Grid will provide you:

    ``` bash
    MAILER_PASS=put here apikey password
    ```

    Default value for MAILER_PORT:

    ``` bash
    MAILER_PORT=465
    ```

    For Rabbit configuration use:

    ``` bash
    RABBITMQ_URL=amqp://localhost:5672
    ```

4. After configuring all those params with your information, run the application and send and *post* request on *POSTMAN*.
5. Verify if your sent data was created on local *MongoDB* database first.
6. Once the data is created, go to Send Grid and log in.
7. You will see *Suppressions* dropdown option on left down.
8. After clicking it, the dropdown will show you and *Invalid* option to click.
9. After clicking it, a new *Invalid Emails* screen will be opened.
10. You can check your dummy email on that screen.

## IMPORTANT TO REMEMBER

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

## FINAL CONSIDERATIONS

It took me almost two days to fix all the problems and understand how an event via RabbitMQ works, the most annoying part to solve was sending the email after the post request was sent because my data was being created in my local MongoDB database but the event was not being sent, after many attempts, a lot of reading and spending a lot of time on stackoverflow, I managed to get the events to work.
