# Docker Mysql Master Slave for Development
This is simple Replication Mysql (1 master - 1 slave) with Docker Compose also for Docker Swarm.

## Information:

- Mysql 8.0 (Original image from Oracle)
- GTIDs on ([What is GTIDs?](https://www.redhat.com/sysadmin/gtid-replication-mysql-servers "What is GTIDs?"))
- PhpMyAdmin built in. (default port: **8081**)
- Auth:
  - master:
    - username: `root`
    - password: `master`
  - slave:
    - username: `root`
    - password: `slave`
  - replica:
    - username: `repl`
    - password: `replpassword`

- Both master and slave service port were not exposed.

## Deploy:

- Docker Compose mode:
`docker-compose up -d`

- Docker Swarm mode:
Remove `depends_on` in service `slave` then run
`docker stack deploy master-slave -c docker-compose.yml`

![image](https://user-images.githubusercontent.com/96720166/207311571-0323d746-8c99-46bf-8d18-a9b320d322f2.png)

## Testing:

You can use Mysql Cli or using PhpMyAdmin for modify data.

### With PhpMyAdmin
Access: `localhost:8081` or `127.0.0.1:8081`
![image](https://user-images.githubusercontent.com/96720166/207311767-9be14dc4-5777-401f-a472-17636bb16e12.png)

Login with username and password (Provided in `Auth` section)
Create a database in master server:
![image](https://user-images.githubusercontent.com/96720166/207312536-d146197e-5d91-4d4c-aa1e-528d671d765b.png)

Access the `slave` server and check if database exists.
![image](https://user-images.githubusercontent.com/96720166/207312801-b4cd7347-5fbd-4539-8964-b0a2fcf3089e.png)

## Licence
[GPLv3][gpl] © [Pham Dai][author]

[magento-badge]:https://img.shields.io/badge/magento-2.3.x%20%7C%202.4.x-orange.svg?logo=magento&style=for-the-badge
[release-badge]:https://img.shields.io/github/v/release/robaimes/module-checkout-designs?sort=semver&style=for-the-badge&color=blue
[packagist]:https://repo.codefarm.codes/#cdfrm/magento2-splitdb
[gpl]:https://www.gnu.org/licenses/gpl-3.0.en.html
[author]:https://www.linkedin.com/in/daipham3101/


