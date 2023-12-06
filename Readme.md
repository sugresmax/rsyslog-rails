# Simple ruby on rails app to view rsyslog records from postgresql database 

The application is based on Rsyslog (https://www.rsyslog.com/).
It's receives logs from various network devices, such as commutators, routers or servers and
save it in Postgresql db.

Logs are viewed through the Ruby on Rails application and Nginx.

## Installation

Copy project to your server

`git clone https://github.com/sugresmax/rsyslog-rails.git && cd rsyslog-rails`

Create `.env` file from `.env.example` and change environment if you need

Run docker compose application

`docker compose up -d`

When application initialized, its creates admin user. You can pass env `ADMIN_USER` & `ADMIN_PASSWORD` to create user.
Otherwise user will be created with name admin and random password.

After all you can connect to app by typing the `server.address:8080` in the browser.

## Configuration of network devices

Just add configuration of your devices to store logs at remote server.

For example, rsyslog can send logs to remote server if we specify in `/etc/rsyslog.conf` this configuration:

```
*.* @@remote-server.address.example
```

More about this: https://www.rsyslog.com/doc/master/index.html
