# Simple ruby on rails app to view rsyslog records from postgresql database 

The application is based on Rsyslog (https://www.rsyslog.com/).
It's receives logs from various network devices, such as commutators, routers or servers and
save it in Postgresql db.

Logs are viewed through the Ruby on Rails application and Nginx.

## Installation

Copy project to your server

`git pull rsyslog-rails && cd rsyslog-rails`

Create `.env` file from `.env.example` and change environment if you need

Run docker compose application

`docker compose up -d`

When application initialized, its creates admin user with random password. You can see it in console output.

After all you can connect to app by typing the `server.address:8080` in the browser.

## Configuration of network devices

Just add configuration of your devices to store logs at remote server.

For example, rsyslog can send logs to remote server if we specify in `/et/rsyslog.conf` this configuration:

```
*.* @@remote-server.address.example
```

More about this: https://www.rsyslog.com/doc/master/index.html


docker run -d \
    -v public:/rails/public \
    -e DB_HOST=rsyslog.db.host \
    -e DB_USER=rsyslog.db.host \
    -e DB_PASSWORD=db-password \
    -e RSYSLOG_DB=rsyslog-db-name \
    -e RAILS_DB=rails-db-name \
    -e RAILS_MASTER_KEY=191e2cae935a1bb0e4f518c6fc0c7f0a
    -e SECRET_KEY_BASE=secret_key_base
    -p 3000:3000 rails_rsyslog
