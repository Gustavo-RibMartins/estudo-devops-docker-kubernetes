# Volumes em contêineres Docker

Vamos testar alguns conceitos usando volumes. Crie uma pasta docker no drive C: (C:/docker), caso seja windows, ou uma pasta no sistema operacional que esteja usando, abra o terminal e execute o comando abaixo

````sh
docker run -it -v /c/docker:/app ubuntu bash
````

Agora dentro do contêiner ainda, execute o seguinte comando

````sh
cd /app
echo "laboratorio de docker" > aula.txt
````

Agora vá no diretório da máquina local (C:/docker), note que o arquivo aula.txt está lá e abra no bloco de notas, que estará escrito "laboratorio de docker".<br>
Agora podemos perceber que, como os contêineres são efêmeros e que podem acabar a qualquer momento, devemos evitar guardar dados dentro dele, mas espelhar os dados em outro local.<br>
Outra forma de trabalhar com volumes, é criar um espaço sem especificar o caminho na máquina local.<br> 
Vamos tentar, digite "exit" e enter no contêiner atual e execute o comando abaixo

````sh
docker volume create exemplo-volume
````

Acabamos de criar um volume, agora basta executar um contêiner fazendo uso do volume

````sh
docker run -it -v exemplo-volume:/app ubuntu bash
````

Executar os comandos abaixo no contêiner

````sh
cd /app
echo "laboratorio de docker 2" > aula2.txt
````

Saia do contêiner digitando "exit" e suba outro contêiner mapeando o mesmo diretório

````sh
docker run -it -v exemplo-volume:/app ubuntu bash
````

Vá até a pasta app, pelo contêiner novo, e perceba que o mesmo arquivo está lá, execute os comandos abaixo

````sh
cd /app
cat aula2.txt
````

O comando "cat" executado acima, joga o conteúdo do arquivo txt na tela.<br>
Agora qual o caminho em que este arquivo aula2.txt está guardado? Execute o comando abaixo

````sh
docker volume inspect exemplo-volume
````

Veja o atributo "Mountpoint" e percebe que o arquivo está salvo na máquina virtual onde o Docker está rodando.