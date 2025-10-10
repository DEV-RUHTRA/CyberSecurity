2025-10-07
Tags: [[HTB]]

----
# Conceito Geral:

Aqui estão diversos comandos utilizados no Shell para obter informações do sistema.

Arquivo pdf.


![[Linux_Fundamentals_Module_Cheat_Sheet.pdf]]

#### Comandos importantes:

- **hostname** (fornece o nome do host);
- **id** (fornece informações do usuário);
- **whoami** (fornece o nome do usuário);
- **uname** (fornece informações sobre a máquina).
#### Comando ``uname``:

**Uname** é um comando utilizado para obter informações da máquina que vamos explorar. Intuitivamente, podemos utilizar o ``man uname`` , para que dessa forma, o manual do comando seja exibido no terminal. Com o manual em mãos qualquer informação da máquina é fácil de obter, ou seja, podemos explorar vulnerabilidades e exploits apenas com essas informações.

#### Diretório ``/etc/passwd``:

O `/etc/passwd`arquivo é um **arquivo de texto em sistemas operacionais** do tipo Unix que contém informações essenciais da conta do usuário, como nome de usuário, ID do usuário (UID), diretório inicial e shell padrão. Utilizando o comando ``cat /etc/passwd`` é **possível ler** todo o arquivo de texto.

#### Comando ``ip`` ou ``ip a``:

O comando ip é utilizado para determinar as 


-----
# Referências:

