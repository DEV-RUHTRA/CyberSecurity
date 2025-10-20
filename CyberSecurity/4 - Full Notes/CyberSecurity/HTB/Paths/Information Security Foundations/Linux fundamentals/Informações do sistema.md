2025-10-07
Tags: [[HTB]]

----
# Conceito Geral:

Aqui estão diversos comandos utilizados no Shell para obter informações do sistema.

Arquivo pdf.


![[Linux_Fundamentals_Module_Cheat_Sheet.pdf]]

#### **Comandos importantes:**

- **hostname** (fornece o nome do host);
- **id** (fornece informações do usuário);
- **whoami** (fornece o nome do usuário);
- **uname** (fornece informações sobre a máquina).
#### **Comando ``uname``:**

**Uname** é um comando utilizado para obter informações da máquina que vamos explorar. Intuitivamente, podemos utilizar o ``man uname`` , para que dessa forma, o manual do comando seja exibido no terminal. Com o manual em mãos qualquer informação da máquina é fácil de se obter, ou seja, podemos explorar vulnerabilidades e exploits apenas com essas informações.

#### **Diretório ``/etc/passwd``:**

O `/etc/passwd`arquivo é um **arquivo de texto em sistemas operacionais** do tipo Unix que contém informações essenciais da conta do usuário, como nome de usuário, ID do usuário (UID), diretório inicial e shell padrão. Utilizando o comando ``cat /etc/passwd`` é **possível ler** todo o arquivo de texto.

#### **Comando ``ip`` ou ``ip a``:**

O comando ip é utilizado para determinar todas as informações de rede, incluindo nome da rede, ip, ipv4, endereço MAC e muito mais.

#### **Comando ``ls -la``:**

**Desvendando o Comando: `ls -l -a`**

Na verdade, `ls -la` é uma combinação do comando `ls` com duas opções (flags): `-l` e `-a`.

- **`ls`**: É o comando base para **l**i**s**tar (do inglês **l**i**s**t) o conteúdo de um diretório. Se você digitar apenas `ls`, ele te mostrará uma lista simples dos nomes dos arquivos e pastas.
    
- **`-a`**: É a opção para "**a**ll" (todos). Ela força o `ls` a mostrar **todos** os arquivos, incluindo os **arquivos ocultos**. No Linux, qualquer arquivo ou diretório que começa com um ponto (`.`) é considerado oculto (por exemplo, o `.bash_history` que você investigou).
    
- **`-l`**: É a opção para "**l**ong format" (formato longo). Em vez de mostrar apenas os nomes, ele exibe uma lista muito mais detalhada, com várias colunas de informação. É aqui que está a maior parte da riqueza do comando.
    

**Analisando a Saída Detalhada (O que o `-l` mostra)**

Quando você roda o `ls -l`, cada linha representa um arquivo ou diretório e é dividida em colunas. Vamos usar uma linha da saída que você me mandou como exemplo:

`drwxr-xr-x 4 htb-student htb-student 4096 Aug 3 2021 .cache`

Aqui está o significado de cada coluna:

1. **Permissões (`drwxr-xr-x`):** A informação mais importante para cibersegurança!
    
    - **`d`**: O primeiro caractere indica o tipo. `d` significa **d**iretório. Se fosse um arquivo normal, seria um `-`.
        
    - **`rwx`**: As próximas 3 letras são as permissões do **Dono** do arquivo. `r` (read/leitura), `w` (write/escrita), `x` (execute/execução).
        
    - **`r-x`**: As 3 seguintes são as permissões do **Grupo** dono. Neste caso, o grupo pode ler e executar, mas não pode escrever (`-`).
        
    - **`r-x`**: As 3 últimas são as permissões para **Todos os Outros** usuários.
        
2. **Número de Links (`4`):** Número de links físicos para o arquivo. (Não é tão crucial para a sua análise inicial).
    
3. **Dono (`htb-student`):** O nome do usuário que é o proprietário do arquivo.
    
4. **Grupo (`htb-student`):** O nome do grupo que é o proprietário do arquivo.
    
5. **Tamanho (`4096`):** O tamanho do arquivo em bytes.
    
6. **Data da Última Modificação (`Aug 3 2021`):** Quando o arquivo foi alterado pela última vez.
    
7. **Nome (`.cache`):** O nome do arquivo ou diretório.
    

**Por que ele é Tão Útil em Cibersegurança?**

- **Encontrar Arquivos Escondidos:** A flag `-a` é essencial para encontrar arquivos de configuração, scripts ou notas que os desenvolvedores ou usuários "esconderam" de propósito ou por padrão.
    
- **Analisar Permissões (O Mais Importante!):** A flag `-l` é a sua principal ferramenta para encontrar vetores de **escalação de privilégios**. Se você (como um usuário de baixa permissão) encontrar um arquivo ou script que pertence ao `root`, mas que você tem permissão de **escrita (`w`)**, isso é uma mina de ouro! Você poderia alterar o script, esperar o `root` executá-lo, e assim ganhar controle total da máquina. Você estará sempre procurando por configurações de permissões anormais.
#### **Comando ``ls -li nome_do_arquivo``:**

Esse comando fornece todas as informações necessárias de um arquivo, como por exemplo o **inode**, nome, dono, data, tamanho etc... Exemplo de saída: 

``147627 -r--r----- 1 root root 755 Jan 18  2018 sudoer.``
inode | permissões|  |dono |grupo |tamanho |data |nome



-----
# Referências:

