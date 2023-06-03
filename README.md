docker-compose run --rm  custom-certbot certonly --webroot --webroot-path /var/www/certbot/ --agree-tos --renew-by-default -d tarlao.fr -d www.tarlao.fr -d anthony.tarlao.fr -d aurelie.tarlao.fr -m anthony.tarlao@gmail.com

docker-compose run --rm  custom-certbot certonly --webroot --webroot-path /var/www/certbot/ --agree-tos --renew-by-default -d calibreo.it -d www.calibreo.it -d api.calibreo.it -d ws.calibreo.it -d staging.calibreo.it -d stagingapi.calibreo.it -d stagingws.calibreo.it -m anthony.tarlao@gmail.com

docker-compose run --rm custom-certbot renew

from scratch
- partir des conf (calibreo.conf, siteperso.conf) avec le port 80 seulement (effacer les conf 443)
- relancer nginx (docker-compose up -d)
- jouer les 2 commandes "docker-compose" ci-dessus pour générer les certif ssl
- les sauvegarder dans le dossier certbot (parent de current)
- remettre les confs 443 et relancer nginx

empty logs:
- docker exec -it custom-nginx bash -c 'truncate --size 0 /etc/nginx/logs/access.log && truncate --size 0 /etc/nginx/logs/error.log'