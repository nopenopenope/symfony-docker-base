## Symfony + Docker + PHP 8.1 + Nginx + MariaDb Boilerplate

This easy and simple boilerplate should kickstart local development for any Symfony application.

Just fetch this repository and run `docker compose up` inside the project root.

Since vendor is not commited, you must run `composer install` on the first run manually:

```shell
$ docker compose up -d
$ docker compose exec php bash
$ composer install
```

The URL will be available at `localhost:1234` but the port can be changed in `docker-compose.yml`.

### This boilerplate is meant to be for educational purposes mainly

If you're new to the Docker environment, things can be a bit overwhelming. Feel free to play around with this repository
content as much as you like locally.

### Things to consider

In this repository we have commited `.env` file. It cannot be commited again unless you specify it via Git.
This is inteded. Please do never commit your `.env` file as it often contains passwords and credentials (which is not
suggested in the first place).

Instead, manipulate the `.env` file locally to match your environment, or better, create a `.env.local` file to override
the settings in there for local development.


### Technologies packed within

| Software | Version |
|----------|---------|
| PHP FPM  | 8.1     |
| Nginx    | 1.23.3  |
| Symfony  | ^6.2    |
| XDebug   | 3.2.0   |
| MariaDb  | 10.10.2 |


### Author

This package has been assembled by Maximilian Graf Schimmelmann (https://www.schimmelmann.org). 
