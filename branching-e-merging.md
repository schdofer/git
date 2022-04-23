# Branching e Merging

### Branch
----
Um Branch é uma ramificação. <br />
É muito usado quando deseja-se dividir o desenvolvimento em duas ou mais frentes para que um código não represe outro. <br />
Pode ser utilizado para criar branches de features que depois serão mesclados com o principal. <br />
Também é comumente usado para dividir os ambientes DEV, HOM e PROD. <br />

#### **Comandos para manipulação de branches**

- ```git branch```
    - Lista os branches de um repositório e indica em qual você está atualmente.
- ```git branch <novo_branch>```
    - Cria um novo branch com o nome informado a partir do branch atual.
- ```git branch -d <nome_branch>```
    - Remove o branch do nome informado.
- ```git checkout <nome_branch>```
    - Alterna o apontamento para o branch informado.
- ```git checkout -b <nome_branch>```
    - Cria um branch como nome informado e já aponta para ele no exato momento.
    - Faz a mesma coisa que executar o comando ```git branch <novo_branch>``` e depois ```git checkout <novo_branch>```

<br />

### Merge
----
Um Merge é uma mesclagem entre 2 branches. <br />
É usando quando queremos importar alterações feitas em um branch para outro. <br />
Basicamente mescla o conteúdo de um branch **"doador”** (passado como parâmetro) para um **“recebedor”** (atualmente selecionado). <br />

#### **Comandos para manipulação de merges**

- ```git merge <>outro_branch>```
    - Realiza merge do outro branch informado com o branch que você está no momento.
    - Traz as alterações o outro branch para o branch atual.
    - Quando um merge é realizado, 3 possíveis resultados podem ocorrer (destacados abaixo)

#### **Possibilidades de retorno na realização de um merge**

- ```Fast-Foreward```
    - Significa que o merge foi realizado com sucesso sem qualquer imprevisto.
    - Isto ocorre quando vieram alterações do outro branch que não existiam no branch atual e no branch atual não existe nenhuma alteração nova.

- ```Recursive```
    - Significa que o merge foi realizado com sucesso mas que o Git teve que organizar a árvore de commits recursivamente.
    - Isto ocorre quando vieram alterações do outro branch que não existiam no branch atual mas também existem alterações no branch atual que não existiam no outro branch (desde que não no mesmo arquivo).

- ```Conflict```
    - Significa que o merge identificou algum conflito que o Git não conseguiu resolver sozinho, necessitando de ajuste manual.
    - Conflitos ocorrem quando:
        1. Um mesmo arquivo foi alterado em branches diferentes e foi realizado um merge entre estes branches
        2. Um mesmo arquivo foi alterado em um mesmo branch por usuários diferentes 
            - Neste caso um aviso de erro surge ao tentar efetuar um "push"
            - Será necessário realizar um "pull" para resolver o conflito localmente

#### **Resolvendo conflitos**

Um conflito sempre deve ser resolvido localmente, para que após tudo ajustado seja enviado ao servidor. <br />
Quando as alterações conflitam, o Git marca o arquivo que teve conflito, indicando onde está o HEAD e onde está o outro branch. <br />
Assim, você deve manualmente editar o arquivo, apagando as marcações e o conteúdo que não quer e salvando o arquivo. <br />
Existem plugins nos ediitores e IDEs modernos que facilitam esta operação. <br />
Após resolver o conflito no repositório local, deverá novamente adicionar o arquivo e realizar o commit. <br />
Somente após você poderá enviar para o servidor com comando "git pull". <br />


