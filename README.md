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


Edit the root **.env** file. 
To do this type **nano .env**

To generate a SECRET_KEY_BASE for Chatwoot use https://www.browserling.com/tools/random-hex or another of your preference

Paste the generated code in SECRET_KEY_BASE=**replace_with_lengthy_secure_hex**

Now Edit the evolution-api/**.env** file. 
To do this type **nano evolution-api/.env**

To generate a AUTHENTICATION_API_KEY for evolution use https://api-keygen.com/ and select UUID or another of your preference

Paste the generated code in AUTHENTICATION_API_KEY=**GENERATE_YOUR_API_KEY**



Inside the "evolution_chatwoot" folder, execute:

    docker-compose up --build --no-start

Delete the __data__ folder located inside __chatwoot__ and recreate it. Inside the __data__ folder, create two new folders: __redis__ and __postgres__.

Wait while it compiles all the data. After completion, enter the following command:

    docker-compose run --rm rails bundle exec rails db:chatwoot_prepare

**Note: If you get the error in the image below, run the command again.**

    docker-compose run --rm --trace rails bundle exec rails db:chatwoot_prepare

![erro-postgres](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/880269df-d7ce-498b-b6dd-6a4f3f5fdcda)


The above command will create the entire Chatwoot database. Finally, to finish, execute this command to bring up all the containers:

    docker-compose up

or no prompt output

    docker-compose up -d



Create an Instance in EvolutionApi

Use manager in web. Type https://URL_of_Evolution/manager

![image](https://github.com/user-attachments/assets/125e4eb6-130b-4e1e-9f16-9729181eae6a)


To set a created instance in EvolutionApi to Chatwoot, you only need to provide the following data:

* **"account_id":** *the id of the created Chatwoot user*
* **"token":** *token of this created user*
* **"url"**: *This url where Chatwoot is located.*

![image](https://github.com/user-attachments/assets/99ece767-940d-455e-a2c0-ebd7559da545)


### If the *Automatically Creates* option is enabled, it will create an inbox in Chatwoot automatically. There is no need to create it manually.

![image](https://github.com/user-attachments/assets/2c14f2e2-1439-4b5d-babd-ffaf29c60942)



# If you want to create the inbox manually.
These variables will be used to create an inbox in Chatwoot.

With Chatwoot open and properly logged in, click on **Settings**, then on **Inbox**, and **Add an Inbox**. Choose **API** as the type.

In the **Channel Name** field, enter what came in **"name_inbox"**, and in the **Webhook URL** field, enter what came in **"webhook_url":**.

Proceed with the remaining steps until you finish and create your inbox.


* **Inbox Name** = Instances Name in Evolution-Api

* **URL of webhook** = https://url-Evolution-Api/chatwoot/webhook/instance

![canal-api](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/eafff7a5-084d-40ec-b4bf-20491c3967c9)



To generate the QRCode in the inbox, go to __contacts__, then __new contacts__, and __add a contact__ containing the following data as shown in the image below:


![criar-contato](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/80e8eadc-e5a4-4b99-bfde-57d76af3732b)


After creating the contact, click on it, then on new message, and in the dialog box that appears, choose the created inbox and write the message __iniciar__, then click on send message.


![gera-qr-code](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/438d77d1-4877-4e63-8683-147a69965a3d)


Now, just go to the inbox and scan the generated QRCode.

![qr-code-gerado](https://github.com/willph/evolutionApi_chatwoot_docker/assets/17226802/1915a150-bc5c-4369-b2f9-ef5f945f368d)



## Postman EvolutionApi v2.0.10
    [https://www.postman.com/agenciadgcode/workspace/evolution-api/collection/26869335-21d9320d-803f-4adb-80b3-a5bcbda2dfe6](https://www.postman.com/agenciadgcode/evolution-api/collection/gqr041s/evolution-api-v2-0)

#### Note: All tests were performed using Ubuntu 22.04 and Docker version 24.0.7. Even though the tutorial is not complete and lacks images, those with some knowledge should be able to test it.
#### Don't forget that if you are going to put it into production, please change the passwords for greater security.


# DONATE

If you want to help us with any amount, send it to will.phelipe@gmail.com PIX or PayPal

_If you need any further assistance, don't hesitate to ask._

_Good luck!_
