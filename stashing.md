# Stashing

A tradução literal de Stash é esconderijo e é justamente isso que esta área é. <br />
É um local para guardarmos o código sem precisar realizar commit. <br />
Usado quando queremos alternar de branch ou mudar de atividade mas ainda não queremos salvar ou persistir o que já fizemos mas também não queremos tocar nosso trabalho fora. 

<br />

#### **Comandos para manipulação de stash**

- ```git stash list```
    - Lista stashes realizados.

- ```git stash save “Mensagem”```
    - Salva na área de Stash os arquivos (presentes na “Staging Area”), incluindo a mensagem informada como um identificador ou lembrete para este stash realizado.
    - Remove os arquivos da “Staging Area” e do “Working Directory”, ou seja, não aparecem (como novos ou modificados) no comando “git status”.

- ```git stash apply stash@{0}```
    - Retorna o Stash informado para “Staging Area” mas mantém cópia na área de Stash.
	- Onde o **stash@{0}** corresponde ao código stash de um identificador salvo.
	- Este código pode ser obtido com o comando “git stash list”.

- ```git stash drop stash@{0}```
	- Remove o stash informado da área de Stash.

- ```git stash pop```
	- Desempilha o último Stash da área de Stash para “Staging Area”.
    - Neste caso ele remove o conteúdo da área de Stash e aplica na Workiing Directory e Staging Area.

- ```git stash branch <<nome_branch>>```
	- Cria um novo branch a partir do conteúdo de um Stash.

<br />
