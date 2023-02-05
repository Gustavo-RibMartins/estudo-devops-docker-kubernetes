# MySQL + bridge + volumes no Docker

Agora vamos unir alguns conceitos bem legais e perceber o poder do Docker, execute o comando abaixo

````sh
docker volume create meu-espaco
````

Criamos um volume, agora vamos subir o MySQL usando este volume

````sh
docker run -d -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=laboratorio -v meu-espaco:/var/lib/mysql --name=meu-banco2 -p 3306:3306 mysql:8.0
````

Aguarde o MySQL estar pronto para conexão e execute para ter certeza

````sh
docker logs meu-banco2
````

Procure no log o seguinte resultado "ready for connections", caso não tenha aparecido, repita o comando acima até que o banco de dados esteja pronto.
Agora abra o Visual Studio Code e instale uma extensão com o seguinte id "cweijan.vscode-mysql-client2", é um cliente de MySQL.
Crie uma nova conexão com os dados abaixo:

````sh
servidor: localhost
porta: 3306
usuário: root
senha: root
````

Acesse o banco "laboratorio", crie tabela e insira dados.<br>
Agora pare e exclua o contêiner com os comandos abaixo

````sh
docker stop meu-banco2
docker rm meu-banco2
````

Crie outro contêiner com o comando abaixo, montando o mesmo espaço

````sh
docker run -d -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=laboratorio -v meu-espaco:/var/lib/mysql --name=meu-banco3 -p 3306:3306 mysql
````

Aguarde o MySQL estar pronto para conexão e execute para ter certeza

````sh
docker logs meu-banco3
````

Vá até o Visual Studio Code, conecte no banco e perceba que todos os dados foram preservados.<br>
O que achou do que podemos fazer com contêineres?