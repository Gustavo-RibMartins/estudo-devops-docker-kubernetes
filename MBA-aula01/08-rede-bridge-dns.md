# Redes bridge DNS Docker

Vamos trabalhar com a rede bridge novamente, mas vamos criar nossa própria rede bridge

````sh
docker network create minha-rede
````

Agora vamos executar um contêiner dentro da rede

````sh
docker run -d --name=webserver-nginx --network=minha-rede nginx
````

Vamos subir outro contêiner na mesma rede

````sh
docker run -d --name=webserver-apache --network=minha-rede httpd
````

Acesse o primeiro contêiner

````sh
docker exec -it webserver-nginx sh
````

Agora de dentro do primeiro contêiner chame o segundo através do nome dele

````sh
curl webserver-apache
````

Olha que interessante, quando criamos nossa própria rede bridge e damos nomes ao nosso contêiner o Docker possui um serviço de DNS que consegue resolver o IP do contêiner por seu nome.