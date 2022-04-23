# Comandos Básicos

Para iniciarmos o uso do Git, primeiramente precisamos aprender os comandos mais básicos. <br />
Segue a lista abaixo:

- **Iniciando um repositório Git para controle de versão**
    - ```git init``` 
    
    <br />

- **Removendo o controle Git**
    - ```Basta remover o diretório oculto ".git" que foi criado com comando "git init"```
    
    <br />

- **Configurando dados do usuário que aparecerão na autoria dos commits**
    - ```git config user.name schdofer```
        - Configura o ***username*** com o valor informado para o repositório do diretório atual
    - ```git config --global user.name schdofer```
        - Configura o ***username*** com o valor informado globalmente no seu Git
    - ```git config user.email meu_email@gmail.com```
        - Configura o ***email*** com o valor informado para o repositório do diretório atual
    - ```git config --global user.email meu_email@gmail.com```
        - Configura o ***email*** com o valor informado globalmente no seu Git
    
    <br />    

- **Verificando status de alterações no repositório e branch atual**
    - Inspeciona todo conteúdo verificando se existe algum arquivo pendente para commit.
    - ```git status```

<br />

- **Adicionando arquivos na Staging Area**
    - Adicionando arquivos individualmente:
        - ```git add <filename_1> <filename_2> <filename_n>```
    - Adicionando todos os arquivos de uma vez:
        - ```git add .```
        - ```git add -a```
        - ```git add --all```

<br />

- **Removendo arquivos da Staging Área**
    - Remove arquivo da Staging Area, trazendo-o novamente para Working Directory
        - ```git rm --cached <filename>```

<br />

- **Gravando no repositório Git local as alterações presentes na Staging Area**
    - ```git commit -m "mensagem de salvamento"```

<br />

- **Verificando logs dos commits realizados**
    - ```git log```
        - Exibe log dos commits realizados trazendo 4 importantes informações:
            1. O Hash SHA1 que identifica unicamente o commit
            2. O autor do commit
            3. A data do commit
            4. A mensagem informada no commit
    - ```git log --oneline```
        - Exibe uma versão mais curta (de uma linha) do log dos commits realizados.
        - Traz consigo apenas as seguintes informações:
            1. O Hash SHA1 que identifica unicamente o commit
            2. A mensagem informada no commit
    - ```git log --oneline --decorate```
        - Exibe uma versão mais curta (de uma linha) do log dos commits realizados.
        - Mostra onde está o HEAD (cabeça = para qual commit o Git está apontando)
        - Decora com cores mais amigáveis a saída textual em tela
    - ```git log --oneline --decorate --all```
        - Exibe uma versão mais curta (de uma linha) do log dos commits realizados.
        - Mostra onde está o HEAD (cabeça = para qual commit o Git está apontando)
        - Decora com cores mais amigáveis a saída textual em tela
        - Mostra também os commits que estão à frente do commit para o qual o HEAD está apontando (desde que estejam no repositório local)
    - ```git log --oneline --decorate --all --graph```
        - Exibe uma versão mais curta (de uma linha) do log dos commits realizados.
        - Mostra onde está o HEAD (cabeça = para qual commit o Git está apontando)
        - Decora com cores mais amigáveis a saída textual em tela
        - Mostra também os commits que estão à frente do commit para o qual o HEAD está apontando (desde que estejam no 
        repositório local)
        - Acrescenta uma exibição gráfica que facilita a identificação de ramificações e merges

<br />

- **Comparando alterações realizadas com a versão anterior de um arquivo**
    - ```git diff <filename>```

<br />
