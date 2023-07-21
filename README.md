# EvolutionApi + Chatwoot on Docker

Repository to help install Evolution API + Chatwoot on Docker.  Used as the docker-compose base of the wppconnect project, and adapted to work with EvolutionApi

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

Inside the "evolution_chatwoot" folder, execute:

    docker-compose up --build --no-start

Wait while it compiles all the data. After completion, enter the following command:

    docker-compose run --rm rails bundle exec rails db:chatwoot_prepare

The above command will create the entire Chatwoot database. Finally, to finish, execute this command to bring up all the containers:

    docker-compose up
