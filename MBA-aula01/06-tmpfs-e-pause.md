# Experimentando tmpfs e pause em Docker

Vamos criar um contêiner Docker que monte uma pasta em memória, abra o terminal e execute o comando abaixo

````sh
docker run -it --mount type=tmpfs,target=/app --name exemplo-tmpfs ubuntu bash
````

Agora vamos navegar até a pasta e criar um arquivo txt

````sh
cd /app
echo "exemplo tmpfs" > tmpfs.txt
````

Pronto o arquivo foi gerado. Abra outra janela de terminal, mantendo o anterior aberto e execute o comando abaixo

````sh
docker pause exemplo-tmpfs
````

Agora o contêiner foi pausado, faça a listagem e perceba o estado dele

````sh
docker ps
````

Agora retire a pausa do contêiner

````sh
docker unpause exemplo-tmpfs
````

Acesse o contêiner novamente

````sh
docker exec -it exemplo-tmpfs bash
````

Acesse a pasta e veja se o arquivo ainda está lá e com o contéudo gravado

````sh
cd /app
cat tmpfs.txt
````

Ótimo, tudo funcionando. Vamos fazer outro teste, pare o contêiner com o comando abaixo, no segundo terminal

````sh
docker stop exemplo-tmpfs
````

Perceba que contêiner está parado

````sh
docker ps -a
````

Vamos iniciar ele novamente 

````sh
docker start exemplo-tmpfs
````

Vamos acessar ele novamente

````sh
docker exec -it exemplo-tmpfs bash
````

Vá até a pasta e veja se o arquivo ainda está lá

````sh
cd /app
cat tmpfs.txt
````

Não está certo? Quando paramos o container ele perde todos os dados em memória.<br>
Com este experimento acabamos de testar dois conceitos, pause e volumes tmpfs. Bacana né?