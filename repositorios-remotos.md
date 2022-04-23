# Contribuindo com repositórios remotos

Como já fora dito, o Git trabalha de forma descentralizada. <br />
Logo, tudo que foi feito no repositório Git local pode ser compartilhado com repositórios remotos. <br />
Primeiramente é necessário ter um repositório Git remoto criado (como por exemplo no GITLAB, GITHUB ou BITBICKET). <br />

<br />

### Criando um link entre repositório local e remoto
----
Para criar um link entre um repositório local e remoto temos basicamente 2 formas:
1. Quando já temos os dados salvos no repositório remoto e queremos criar e iniciar nosso repositório local a partir dele.
    - ```git clone <url_repositório_remoto>```
2. Quando já temos os dados salvos no repositório local e queremos iniciar o repositório remoto a partir dos dados locais.
    - Para isso, precisaremos adicionar nossa origem remota (referência local do repositório remoto).
    - ```git remote add origin <<url_repositório_remoto>>```
	    - Onde ***“origin”*** é o nome como o repositório remoto será referenciado localmente.
		- Pode ser qualquer nome, mas ***“origin”*** é uma convenção do Git muito adotada.

<br />

### Visualizando repositórios remotos configurados no projeto GIT:
----
Para visualizar os repositórios remotos referenciados localmente, utilize os comandos:
- ```git remote```
    - Lista os repositórios remotos ativos para o projeto.
- ```git remote -v``` ou ```git remote --verbose```
    - Lista os repositórios remotos ativos para o projeto com maiores informações.

<br />

### Enviando dados do repositório local para o remoto
----
Utilizar o comando ***“git push”*** do inglês empurrar. <br />
Basicamente 2 formas de uso:
- ```git push```
    - Envia os dados commitados no repositório local corrente para o correspondente no repositório remoto.
- ```git push origin dev```
    - Envia os dados commitados no repositório local e branch de nome ***“dev”*** para o repositório remoto e branch de mesmo nome.
    - Na primeira vez que utilizar o comando é necessário usar o parâmetro ***-u*** para vincular o branch local com o branch remoto de mesmo nome.

<br />

### Obtendo dados do repositório remoto para o local
----
Utilizar o comando ***“git pull”*** do inglês puxar. <br />
Este comando obtém os arquivos no branch remoto de mesmo nome que o local e já faz um merge automaticamente no branch local, informando o resultado da operação de Merge. <br />
Basicamente 2 formas:
- ```git pull```
    - Obtém todas alterações do repositório remoto e atualiza os branchs locais correspondentes
- ```git pull origin dev```
    - Obtém os dados commitados no repositório remoto de nome ***“dev”*** e atualiza no repositório local de mesmo nome.


Podemos ainda obter dados mas não realizar o Merge automaticamente no nosso branch local, para isto usa-se o comando ***“git fetch”***.

O comando ***“git fetch”*** traz para o branch local todas alterações do repositório remoto porém não realiza o Merge. <br /> 
É muito útil quando queremos trazer os dados para comparar com ***“git log”*** ou ***“git diff”*** antes de fazer o Merge. <br /> 
Como o os comandos do Git são locais, após usar o fetch aí sim é possível usar o log e o diff. <br />

Exemplo de uso: <br />
	```git diff master origin/master```