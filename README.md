#Trabajo Práctico Wordpress

#1-Clonar repositorio
  git clone https://github.com/apenasco/wordpress.git
  cd wordpress

#2-Crear volumen (10GB)
	openstack volume create --size 10 prod-db-vol

#3-Deploy
	make deploy ENV=prod

#4- Volumen para stag
	cinder snapshot-create --force --name snap-stag-db-vol prod-db-vol
	cinder create --snapshot-id UUID --name stag-db-vol 10

#5- Deploy stag:
	make deploy ENV=stag

