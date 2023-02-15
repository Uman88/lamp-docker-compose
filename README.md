# A simple LAMP stack was created using Docker-Compose

### A basic LAMP stack environment, contains for following:
* PHP
* APACHE
* MySQL
* phpMyAdmin

Structure LAMP Docker-Compose

```
├── app
│   └── index.php
├── docker
│   ├── images
│   │   ├── mysql
│   │   │   ├── Dockerfile
│   │   │   └── my.cnf
│   │   └── php
│   │       ├── Dockerfile
│   │       └── php.ini
│   ├── logs
│   │   └── apache2
│   └── volume
│       └── mysql
├── docker-compose.yml
└── README.md

```

How to use LAMP, just build:

```
docker-compose build
```

Then:

```
docker-compose up -d
```

Then go to http://localhost and you will see the index page
with information about the currently installed PHP.

You throw your projects in the app folder, for example:
* /app/store
* /app/store.loc

