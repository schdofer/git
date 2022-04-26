# Desfazendo as coisas no Git
O git possui comandos relacionados a "desfazer" as coisas. <br />
São eles: ***git checkout***,  ***git clean***,  ***git revert***, ***git reset***,  ***git rm*** e ***git reflog***

<br />

### git checkout
----
Git checkout é uma maneira fácil de “carregar” as capturas instantâneas salvas na máquina de desenvolvimento. Durante o curso normal de desenvolvimento, HEAD em geral aponta para a ramificação main ou para outra ramificação local, mas, quando você consulta um commit anterior, HEAD não aponta mais para uma ramificação — ele aponta direto para um commit. Esse estado é chamado de "HEAD desconectado".<br />
Usado para descartar alterações de um dado arquivo, retornando a versão que é apontada pelo HEAD (último commit válido normalmente) ou algum commit específico.

```git checkout HEAD```
- Usado para retornar para o “Working Directory” e “Staging Area” a última versão commitada de todos arquivos.
- Usado quando você fez alguma alteração que não deveria no arquivo e deseja retornar a última versão salva.

<br />

```git checkout <SHA_COMMIT>```
- Usado para retornar para o “Working Directory” e “Staging Area” a versão do commit especificado de todos arquivos
- Usado quando você deseja ver com a versão estava em determinado commit.
- Você pode usar um ```git checkout -b <NEW_BRANCH>``` a partir do checkout de um commit anterior para criar um novo branch sem os commits indesejados (outra forma de desfazer as coisas)

<br />

```git checkout HEAD <filename>```
- Usado para retornar para o “Working Directory” e “Staging Area” a última versão commitada do arquivo.
- Usado quando você fez alguma alteração que não deveria no arquivo e deseja retornar a última versão salva.

<br />

```git checkout <SHA_COMMIT> <filename>```
- Usado para retornar para o “Working Directory” e “Staging Area” a do arquivo correspondente ao commit informado.
- Usado quando você fez alguma alteração que não deveria no arquivo e deseja ver como estava em determinado commit.

<br />

### git reset
----
O git reset modifica para qual commit o "ponteiro" da branch está apontado. Você pode utilizar isso para desfazer alguma alteração, mas tem que tomar cuidado porque você vai modificar todo o histórico de commits. <br />
Usado para remover arquivos da árvore de commits ou mesmo da Staging Area. <br />
ELE DESFAZ TODOS COMMITS ATÉ O COMMIT ESPECÍFICO. <br />
É o comando de "desfazer" que tem o resultado mais "limpo", como se os commits nunca tivessem existido. <br />
É recomendado quando ainda fez "push" (enviou as alterações para o servidor), porque senão teria que usar o parâmetro ***--force*** o que poderia "chatear" alguns colegas de projeto. <br />
Existem 3 formas de fazer um Reset (soft, mixed e hard), onde a forma padrão é a “mixed”. <br />
Quando não informada a forma de realizar o reset, é utilizada a forma padrão, que como dito acima é a ***mixed***. 

<br />

#### **SOFT**
Utiliza-se o parâmetro ***--soft***. <br />
É a versão mais "leve" de se fazer um reset. <br />
Desta forma, os arquivos dos commits posteriores ao commit para o qual o reset apontou o HEAD, seguem no ***“Working Directory”*** e na ***“Staging Area”*** mas são removidos da árvore de commits. <br />
Muito usado para refazer algum commit quando deseja-se trocar a mensagem informada. <br />
Exemplo: ```git reset --soft 04bi00e``` 

<br />

#### **MIXED**
Forma padrão de se efetuar um reset. <br />
Utiliza-se o parâmetro ***--mixed*** (ou simplesmente sem informar nada por ser o padrão). <br />
Os arquivos dos commits posteriores ao commit para o qual o reset apontou o HEAD, seguem no ***“Working Directory”*** mas são removidos da ***“Staging Area”***. <br />
Muito usado para refazer algum commit quando deseja-se trocar a mensagem informada ou quando adicionou algum arquivo indevido ou ainda esqueceu-se de adicionar algum arquivo.
Exemplo: ```git reset --mixed 04bi00e ou git reset 04bi00e``` 

<br />

#### **HARD**
Utiliza-se o parâmetro ***--hard***. <br />
É a versão mais "pesada" de se fazer um reset. <br />
Os arquivos dos commits posteriores ao commit para o qual o reset apontou o HEAD, são REMOVIDOS DE TODAS AS ÁREAS, ou seja, removidos da ***“Árvore de Commits”***, ***“Staging Area”*** e ***“Working Directory”***. <br />
Usado quando você deseja tocar o trabalho fora. <br />
Exemplo: ```git hard --hard 04bi00e```

<br />

#### **Diferentes sintaxes para Git Reset**
```git reset HEAD <filename>```
- Remove um arquivo da staging area, mantendo no Working Directory.
- Usado quando um arquivo foi adicionado por engano na Staging Area.
<br />

```git reset HEAD || git reset HEAD~2 (2 commits abaixo) || git reset HEAD^^^^ (4 commits abaixo)```
- Remove os arquivos da Staging Area e da árvore de commits até o número de commits abaixo desejado.
- Usado quando deseja-se limpar os commits à frente de um desejado commit.
<br />

```git reset <SHA_COMMIT> (7 primeiros caracteres)```
- Remove da árvore de commits tudo que estiver depois do SHA informado.

<br />

### git revert
----
O comando git revert pode ser considerado um comando do tipo "desfazer"; no entanto, ele não é uma operação tradicional de desfazer. Em vez de remover o commit do histórico do projeto, ele descobre como inverter as alterações introduzidas pelo commit e anexa um commit novo com o conteúdo resultante. Assim, ele evita que o Git perca o histórico, o que é importante para a integridade do histórico de revisão e para uma colaboração confiável. <br />
ELE REVERTE APENAS O COMMIT ESPECÍFICO. <br />
Resumindo: o git revert reverte as alterações de um commit antigo, e assim que ele reverter, ele cria um commit novo com os dados revertidos, ou seja, ele não modifica e nem remove nenhum dos commits anteriores, apenas cria um novo removendo as alterações do commit informado. <br />
Sendo assim, o uso dele é mais recomendado quando você já realizou o "push" para o servidor. Assim será realizado um novo commit na árvore, não "estragando" a árvore de commits dos demais colaboradores do projeto. <br />

#### **Diferentes sintaxes para Git Revert**

```git revert <SHA_COMMIT> (7 primeiros caracteres)```
- Revert o commit do SHA informado, gerando um novo commit de reversão.
- Em seguida o Git abrirá o editor que foi selecionado como padrão para editar o commit de reversão, onde você pode editar a mensagem.
- Caso seja necessário realizar ajustes e correções nos arquivos durante o processo de reversão, será necessário utilizar o comando git add após a edição desses arquivos e em seguida o comando e depois para finalizar o comando ```git revert --continue```.
<br />

```git revert HEAD || git revert HEAD~2 (2 commits abaixo) || git revert HEAD^^^^ (4 commits abaixo)```
- Reverte os arquivos até o commit desejado sendo que o número 1 é o último commit.

<br />

### git checkout x git reset X git revert
----
- git checkout
    - Utilize git checkout para mudar de lugar e revisar o histórico de commit
    - Utilize também quando desejar criar um novo branchh a partir de um commit antigo
- git revert 
    - É a melhor ferramenta para desfazer alterações públicas compartilhadas
    - Reverte APENAS o commit informado
    - Não altera o histórico de commits
    - Evita necessidade de usar o ***--force*** e constrangimentos com colegas    
- git reset 
    - É usado melhor para desfazer alterações privadas locais
    - Desfaz TODOS os commits até o commit selecionado
    - Altera o histórico de commits
    - Uso indicado para quando ainda não foi realizado o "push"

<br />

### git restore
----
O git restore é uma nova opção quando estamos trabalhando e precisamos restaurar algum arquivo ou o projeto por completo, e isso o git checkout também faz, porém o git restore é especificamente para trabalhar com essa parte de restauração de arquivos ou projeto ao um ponto anterior que chamamos de fonte de restauração (source). <br />
O checkout tinhha muitas responsabilidades, então o restore veio como uma opção com responsabilidade mais enxuta. <br />
Sintaxe: ```git restore --source <SHA_COMMIT> .```

<br />

### git reflog
----
Usando para quando desejamos "desfazer" um "reset". <br />
Usado para obter os hashs SHA1 dos commits que foram removidos com RESET de forma equivocada. <br />
Depois de obter o hash basta refazer o "reset" para ele. <br />
Sintaxe do reflog: ```git reflog``` <br />
Em seguida execure: ```git reset --hard <SHA_COMMIT>```

<br />

### git commit --amend
----
Usado para desfazer uma mensagem de commit. <br />
Basicamente, ele permite que você ajuste a mensagem do último commit para mensagem mais adequada.

<br />

### git rm
----
O comando git rm pode ser usado para remover arquivos individuais ou uma coleção de arquivos. A principal função do git rm é remover arquivos rastreados do índice de Git. O git rm também pode ser usado para remover arquivos do índice de staging e do diretório de trabalho. <br />
É melhor usar o comando ```git rm``` em vez de simplesmente o "rm" por que ai o Git já reconhece e remove do seu índice de controle. <br />
Usando apenas o "rm" será necessário fazer um ```git add``` e ```git commit``` para remover também o arquivo do controle de versão.

<br />

### git clean
----
É considerado até certo ponto um comando do tipo "desfazer". <br />
Ele porém atua sobre os arquivos não rastreados pelo Git, os arquivos "UNTRACKED". <br />
Arquivos não rastreados são arquivos que foram criados dentro do diretório de trabalho do repositório, mas ainda não foram adicionados ao índice de rastreamento do repositório usando o comando git add. <br />
O Git é configurado globalmente para exigir que o ```git clean``` seja executado com parâmetro ```--force``` devido sua ação ser irreversível. <br />
Quando executado por completo, o git clean vai fazer uma exclusão irreversível do sistema de arquivos, semelhante à execução do utilitário rm da linha de comando (excluindo todos arquivos não rastreados pelo Git).

<br />

### Fonte de estudo
[https://www.atlassian.com/br/git/tutorials/undoing-changes](https://www.atlassian.com/br/git/tutorials/undoing-changes)
