docker stop nginx 

docker-compose build

docker-compose up -d

Dans apps/my-symfony-app:

docker-compose exec php composer install
docker-compose exec php php bin/console doctrine:schema:create
docker-compose exec php composer require doctrine/doctrine-fixtures-bundle --dev
docker-compose exec php php bin/console doctrine:fixtures:load

docker-compose stop