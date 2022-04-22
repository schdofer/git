# Arquitetura

O Git possui algumas importantes áreas em sua arquitetura para sua correta execução. 

<br />

### **Working Directory**
Representa o diretório de trabalho no sistema de arquivos. <br />
Quando o arquivo está apenas nesta área, ele ainda não é controlado pelo GIT. <br />
Arquivos vem para cá após um PULL.

<br />

### **Staging Area**
É uma área de transferência utilizada pelo GIT. <br />
Os arquivos precisam ser adicionados nesta área para posteriormente serem persistidos ou salvos no repositório GIT. <br />
Arquivos vem para cá após um ADD.

<br />

### **GIT Local Repository**
O repositório local do GIT é onde ficam os arquivos que já estão salvos e controlados pelo GIT. <br />
Arquivos vem para cá após um COMMIT.

<br />

### **GIT Remote Repository**
O repositório remoto do GIT é exatamente como o repositório local, porém fica em outro computador ou servidor. <br />
Arquivos vem para cá após um PUSH.

<br />
