# Trabalhando com variáveis de ambiente no Docker

Vamos entender como funcionam as variáveis de ambiente no Docker, portanto vamos subir agora o banco de dados MySQL usando docker

````sh
docker run -d -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 --name=meu-banco mysql:8.0
````

Desta vez estamos passando uma variável de ambiente para o contêiner, definindo a senha do usuário root de banco como "root", para saber se o MySQL subiu execute o comando abaixo

````sh
docker logs meu-banco
````

Procure no log o seguinte resultado "ready for connections", caso não tenha aparecido, repita o comando acima até que o banco de dados esteja pronto.<br>
Agora abra o Visual Studio Code e instale uma extensão com o seguinte id "cweijan.vscode-mysql-client2", é um cliente de MySQL.<br>
Crie uma nova conexão com os dados abaixo:

````sh
servidor: localhost
porta: 3306
usuário: root
senha: root
````

Com este cliente é possível criar bancos, tabelas e inserir dados na sua instância de MySQL.