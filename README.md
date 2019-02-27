# docker-container-as-service

Script to start docker container on boot on linux

## Getting Started

These instructions will get you run docker container as linux daemon

### Prerequisites

Needs docker as service on host machine

```
systemctl enable docker
```

### Installing

Enterprise linux(Tested on Oracle Enterprise Linux 7)

1. Download script 

2. Re-name file docker-[service-name]@[container-name].service

    **[service-name]**: i suggest use container name but you can use anything.

    **[container-name]**: represent container name assigned at created time.

```
  mv docker-[service-name]@[container-name].service docker-mariadb-test@mariadb-test.service
```
3. Copy file to /etc/systemd/system directory

```
cp docker-mariadb-test@mariadb-test.service /etc/systemd/system/ 
```

4. Enable new service by using
```
systemctl enable docker-mariadb-test@mariadb-test.service
```


## Using service

To check if service works use this steps

Start service
```
systemctl start docker-mariadb-test@mariadb-test.service
```
Now you can see if docker container is running
```
docker ps 
or
docker ps | grep mariadb-test
```

Stop service
```
systemctl stop docker-mariadb-test@mariadb-test.service
```

Service status
```
systemctl status docker-mariadb-test@mariadb-test.service
```


### Finally


Now your containers starts on boot and stops on shutdown.

## Authors

* **Ricardo Barrera** - *Initial work* - [brik18](https://github.com/brik18)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
