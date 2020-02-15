# Server

## Setup

1. Add the following line to your hosts file: `192.168.10.10 homestead.server`
2. Copy the `Homestead.example.yaml` to `Homestead.yaml`, and configure the folders to your computer
3. Run `php vendor/bin/homestead make`

## Connecting to the Database

* Using PostgreSQL
* Default Configuration:
    Username: `homestead`
    Password: `secret`
    Port: `54320`
* Follow this [link](https://laravel.com/docs/4.2/homestead#daily-usage) for more information
