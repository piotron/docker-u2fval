# Docker u2fval

## Getting started
These instruction will get you a working u2fval server from @yubico in docker env.

### Prerequisities
Docker 1.10

## Building
```
docker build -r u2fval:{TAG}
```
Required mounts:
* /u2fval-data
Optional mounts:
* /etc/yubico/u2fval/u2fval.conf - Here you change database from default sqlite
* /etc/yubico/u2fval/logging.conf - Here you can set logging options
* /uwsgi.yaml - this one is for uwsgi configuration


## How to run?
#### Default run command
````
# docker run -d --name u2fval-server  -p 8080:8080 -v $HOSTDIR:/u2fval-data u2fval
```
#### Initiate database schema
 If you didn't modified config file, it will create SQLITE database file.
```
docker run {args} u2fval db init
```
### Upgrade database schema basing on connection string in u2fval.conf file
```
 docker run {args} u2fval db upgrade
```
### run standalone webserver
```
 docker run {args} u2fval run -i0.0.0.0
```
## Authors

* **Piotr Radosz** - *Initial work* - [piotron](https://github.com/piotron)

