# Autenticação

No Github as formas de autenticação são:
- SSH
- Token de acesso pessoal

<br />

### **SSH**
Forma de estabelecer uma conexão segura e encriptada entre duas máquinas. <br />
Ao utilizar esta forma, não precisará ficar fornecendo usuário e senha a cada interação com servidor pois a chave criptografada se encarregará disto. <br />
Para criar, siga os passos:
1. Criação da chave com ssh-keygen:
    - ```ssh-keygen -t ed25519 -C fernando.cunha1986@gmail.com```
2. Adicione a chave publica no GitHub
3. Inicie o ssh--agent e passar a chave privada para ele
    - ```eval $(ssh-agent -s)```
    - ```ssh-add /home/fernando/sshh/id_ed25519```

<br />

### **Token de acesso pessoal**
Para poder acessar usando protocolo HTTPS é recomendado geração de token de acesso pessoal. <br />
É uma outra maneira de acessar o Github. <br />
Desta forma, ele sempre pedirá seu usuário e senha ao interagir com servidor. <br />
Para gerar o token no Github siga os passos:
1. Acesse Developer settings
2. Personal access tokens
3. New Token
4. Generate token (pode ter uma data de expiração)

