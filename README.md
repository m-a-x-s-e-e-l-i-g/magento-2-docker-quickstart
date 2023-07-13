# Magento 2 Docker Quickstart
Easily spin up a Magento 2 shop for Development purposes

## Requirements
- [Docker](https://docs.docker.com/engine/install/)

## Get started
1. Clone this repository and go into the directory
```
git clone https://github.com/m-a-x-s-e-e-l-i-g/magento-2-docker-quickstart
```
2. Go into the directory
```
cd magento-2-docker-quickstart
```
3. Spin up:
```
docker-compose up -d
```
4. Access the container's CLI as root:
```
docker exec -it magento2 bash
```
5. Change directory to the Magento root:
```
cd /bitnami/magento
```
6. Get your authentication keys: \
You could use the following guide: \
https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html \
But it's as simple as this when you have a [Magento Marketplace](https://repo.magento.com/) account: \
![animated-steps](https://user-images.githubusercontent.com/7907436/175305577-a92020f9-33ac-41f6-8f0f-55f89dfbe969.png)

7. Deploy sample data:
```
php bin/magento sampledata:deploy
php bin/magento setup:upgrade
php bin/magento cache:flush
```
8. (Optional) Install modules:
```
composer require vendor/module
php bin/magento module:enable Vendor_Module
php bin/magento setup:upgrade
php bin/magento setup:di:compile
php bin/magento setup:static-content:deploy -f -s standard
chmod -R 777 ./pub/ ./var/cache ./generated
php bin/magento cache:flush
```
9. MAGENTO TIME! \
![party](https://media4.giphy.com/media/UfJhMWe12OaIxJxzDw/giphy.gif)

10. (Optional) Cry😭  
In this final step, you come to the realization that Magento lacks any enjoyable aspects..

## Credentials

Name | URL | Username | Password
----------------------|------------------------|------|---------
Magento Frontend      | http://localhost       |      |
Magento Admin Backend | http://localhost/admin | user | bitnami1
PHPMyAdmin            | http://localhost:8080  | root | 

## Enabling developer mode
```
bin/magento deploy:mode:set developer
```
