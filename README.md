# EvolutionApi + Chatwoot on Docker

Repository to help install Evolution API + Chatwoot on Docker.  
Used as the docker-compose base of the wppconnect project, and adapted to work with EvolutionApi

This installation includes the following packages:

* **EvolutionAPI:** The EvolutionAPI package.
* **Chatwoot:** The Chatwoot package.
* **Nginx:** The Nginx web server.
* **Postgres:** The PostgreSQL database.
* **Redis:** The Redis in-memory data structure store.
* **PgAdmin:** The PgAdmin web-based administration tool for PostgreSQL.

# Installation

First, clone the repository using the following command:

    git clone https://github.com/willph/evolutionApi_chatwoot_docker evolution_chatwoot

After that, run the following command:

    cd evolution_chatwoot

To copy and paste the file .env.example as .env in these two locations, run the following commands:

    cp .env.example .env
    cp evolution-api/Docker/.env.example evolution-api/Docker/.env

Inside the "evolution_chatwoot" folder, execute:

    docker-compose up --build --no-start

Wait while it compiles all the data. After completion, enter the following command:

    docker-compose run --rm rails bundle exec rails db:chatwoot_prepare

The above command will create the entire Chatwoot database. Finally, to finish, execute this command to bring up all the containers:

    docker-compose up



Create an Instance in EvolutionApi
Send a JSON of type POST to the URL localhost:8080/instance/create

"instanceName": -> the desired name for the instance
"token": -> Create an apiKey for this instance

    {
       "instanceName": "Name_Instance",
       "token": "Create_apiKey",
       "qrcode": true
    }

![create_instance](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/4d84ba91-5f7c-4be8-96c6-731378ada804)


To set a created instance in EvolutionApi to Chatwoot, you only need to provide the following data:

* **"account_id":** *the id of the created Chatwoot user*
* **"token":** *token of this created user*
* **"url": "http://rails:3000"** *This remains unchanged as it is the container where Chatwoot is located.*

Send the JSON as a POST request to the URL localhost:8080/chatwoot/set/chosen_instance_name

**chosen_instance_name** -> *This refers to the name chosen when creating the instance.*

    {
	   "enabled": true,
	   "account_id": "id_user_chatwoot",
       "token": "Token_of_user_chatwoot",
       "url": "http://rails:3000",
       "sign_msg": true
    }

![set_chatwoot](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/6be316c2-a8ce-4d23-9034-43285c3b2fad)



## Postman EvolutionApi v1.3.1
    https://www.postman.com/agenciadgcode/workspace/evolution-api/collection/26869335-21d9320d-803f-4adb-80b3-a5bcbda2dfe6

#### Note: All tests were performed using Windows 10 and Docker Desktop 4.21.1 (114176). Even though the tutorial is not complete and lacks images, those with some knowledge should be able to test it.


_If you need any further assistance, don't hesitate to ask._

_Good luck!_
