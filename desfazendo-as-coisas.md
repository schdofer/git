# Desfazendo as coisas no Git

### git restore
----

<br />

### git checkout
----
Usado para descartar alterações de um dado arquivo, retornando a versão que é apontada pelo HEAD (último commit válido normalmente) ou algum commit específico.

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
Usado para remover arquivos da árvore de commits ou mesmo da Staging Area. <br />
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

### git reset X git revert
----

### git reflog
----
