# Como o Git funciona por baixo dos panos ?

O Git utiliza o algorítmo de encriptação SHA1 para controle e versionamento de código o que garante agilidade e segurança.

<br />

### SHA1
----
A sigla SHA significa "Secure Hash Algorithm" e o 1 indica a versão deste algorítmo usado. <br />
É um conjunto de funções criptográficas projetadas pela NSA (agência de segurança dos EUA). <br />
A encriptação gera conjunto de caracteres de 40 dígitos, sendo possível identificar quaisquer alterações facilmente pois qualquer vírgula alterada nno arquivo geraria uma alteração na criptografia resultannte. <br />
Podemos ver o SHA1 em ação usando a ferramenta OPENSSL, veja os exemplos: <br />
1. Gerando SHA1 em tela a partir de uma String com OPENSSL
    - ```echo "Olá mundo!" | openssl sha1```
2. Gerando SHA1 em tela a partir de arquivo com OPENSSL
    - ```openssl sha1 arquivo.txt```
3. Como os objetos do Git utilizam metadados (além dos conteúdos dos arquivos) ele gerará um Hash SHA1 diferente do gerado pelo OPENSSL. <br />
Para reproduzirmos o Hash de um arquivo exatamente igual ao Hash gerado pelo Git temos que informar estes mesmos metadados (string fixa blob, espaço, tamanho da string, \0 e por fim o conteudo):
    - ```echo "blob 8\0conteudo" | openssl sha1```

<br />

Também podemos usar o próprio Git para gerar o Hash SHA1, veja os exemplos (assim não precisamos informar os metadados): <br />
1. Gerando SHA1 a partir de string informada
    - ```echo "Olá mundo!" | git hash-object --stdin```
2. Gerando SHA1 a partir de arquivo
    - ```git hash-object ./meu-arquivo.txt```

<br /><br />

### Objetos fundamentais no Git
----
O Git possui alguns objetos fundamentais para seu funcionamento. <br />
Estes objetos server para garantir o controle do versionamento facilitando a identificação de alterações. <br />
Eles possuem além dos conteúdos dos arquivos propriamente ditos, metadasdos que são utilizados apra controle pelo Git. <br />

<br />

#### **BLOB**
Objeto especial onde o git armazena o conteúdo de um arquivo que será encriptado com SHA1. <br />
Contém metadados e o conteúdo de um arquivo. <br />
Os metadados que possui são:
- Tipo de objeto (neste caso a string "blob")
- Espaço em branco
- Tamanho do conteúdo (inteiro que representa o tamanho do conteúdo do arquivo)
- Caracteres especiais (\0)
- Conteúdo (conteúdo textual do arquivo propriamente dito)

<br />

#### **TREE**
Objeto especial que armazena vários BLOBs. <br />
Também será gerado um Hash SHA1 para uma TREE, sendo assim, qualquer alteração no SHA1 de um BLOB contido dentro de uma específica TREE também gerará alteração no Hash SHA1 desta mesma TREE. <br />
Com isto, perceba que existe uma hierárquia que facilita a identificação de alterações e que otimiza o controle do versionamento. <br />
Uma TREE também possui seus metadados que são:
- Tipo de objeto (neste caso a string "tree")
- Espaço em branco
- Tamanho do conteúdo (inteiro que representa o tamanho do conteúdo de toda tree)
- Caracteres especiais (\0)
- BLOB(s)
- Hash do(s) BLOB(s)
- Nome do arquivo(s) do(s) BLOB(s)