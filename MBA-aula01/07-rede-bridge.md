# Redes Bridge Docker

Vamos iniciar utilizando a rede Bridge do Docker, para isso vamos usar outra imagem, um servidor web leve, chamado nginx, portanto execute o comando abaixo, mas certifique-se de que a porta 8080 da sua máquina está livre, abra o navegador e tente acessar http://localhost:8080 <br>
Caso a porta esteja ocupada troque por outra porta e execute

````sh
docker run -d -p 8080:80 --name=web-server nginx 
````

Agora abra seu navegador e acesse http://localhost:8080 (porta definida no comando) <br>
Você vai ver a página inicial do nginx. Parabéns, você acabou de subir um servidor web com Docker! <br>
Vamos analisar em qual rede o contêiner está, execute o comando abaixo

````sh
docker inspect web-server
````

Muita informação será retornada, mas procure por "Networks" e verá a informação "bridge". Além do contêiner estar na rede bridge, fizemos um mapeamento de portas para que a porta 80 do contêiner fosse redirecionada para a 8080 de nossa máquina. <br>