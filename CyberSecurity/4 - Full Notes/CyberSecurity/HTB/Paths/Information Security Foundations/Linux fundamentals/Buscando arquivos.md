2025-10-18
Tags: [[HTB]]

----
# Conceito Geral:

##### **Comando find:**

O comando ``find`` é o **principal** comando utilizado para buscar por pastas, diretórios, arquivos entre outros. O especial e diferencial dele é a forma como podemos buscar utilizando parâmetros, como loca, tipo, dono, data tamanho entrou outros.

![[Pasted image 20251018125037.png]]

**Exemplo:**

![[Pasted image 20251018125152.png]]

**Parâmetros:**

| **Opção**             | **Descrição**                                                                                                                                                                                                                                                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-type f`             | Aqui, definimos o tipo do objeto pesquisado. Neste caso, ' `f`' significa ' `file`'.                                                                                                                                                                                                      |
| `-name *.conf`        | Com ' `-name`', indicamos o nome do arquivo que estamos procurando. O asterisco ( `*`) representa 'todos' os arquivos com a `.conf`extensão ' '.                                                                                                                                          |
| `-user root`          | Esta opção filtra todos os arquivos cujo proprietário é o usuário root.                                                                                                                                                                                                                   |
| `-size +20k`          | Podemos então filtrar todos os arquivos localizados e especificar que queremos ver apenas os arquivos maiores que 20 KiB.                                                                                                                                                                 |
| `-newermt 2020-03-03` | Com esta opção, definimos a data. Somente arquivos mais recentes que a data especificada serão apresentados.                                                                                                                                                                              |
| `-exec ls -al {} \;`  | Esta opção executa o comando especificado, usando as chaves como espaços reservados para cada resultado. A barra invertida impede que o próximo caractere seja interpretado pelo shell, pois, caso contrário, o ponto e vírgula encerraria o comando e não alcançaria o redirecionamento. |
| `2>/dev/null`         | Este é um `STDERR`redirecionamento para o ' `null device`', ao qual retornaremos na próxima seção. Este redirecionamento garante que nenhum erro seja exibido no terminal. Este redirecionamento deve `not`ser uma opção do comando 'find'.                                               |

#### **Descritores de arquivo e redirecionamentos:**

#### **1. O que é um Descritor de Arquivo (File Descriptor - FD)?**

- É um **número único** (como um "CPF") que o Linux usa para identificar qualquer recurso de entrada ou saída aberto (arquivos, conexões de rede, etc.).
    
- **Analogia:** Pense no ticket de um guarda-volumes. O ticket é o **Descritor de Arquivo**, e o seu casaco é o **arquivo/recurso**. Você usa o ticket para interagir com seu casaco.
    

#### **2. Os 3 Descritores de Arquivo Padrão (Essenciais)**

Todo programa no Linux, por padrão, já começa com três canais de comunicação abertos:

- **`STDIN` (Standard Input) - FD 0:** Entrada Padrão. Geralmente, é o **teclado**.
    
- **`STDOUT` (Standard Output) - FD 1:** Saída Padrão. Geralmente, é a **tela/terminal**. É a saída normal e bem-sucedida de um comando.
    
- **`STDERR` (Standard Error) - FD 2:** Saída de Erro Padrão. Também é a **tela/terminal**. É para onde as mensagens de erro são enviadas.
    

#### **3. Redirecionamento: Controlando os Fluxos de Dados**

Redirecionar é a técnica de desviar esses fluxos padrão (entrada, saída e erro) de seus destinos normais.

- **`>` (Redirecionar STDOUT):** Envia a saída padrão para um arquivo.
    
    - **Atenção:** Se o arquivo não existe, ele é criado. Se já existe, ele é **sobrescrito** (apagado e recriado).
        
    - **Exemplo:** `find /etc/ -name shadow > resultados.txt` (salva a saída no arquivo).
        
- **`>>` (Anexar STDOUT):** Envia a saída padrão para um arquivo, mas em vez de sobrescrever, **adiciona o resultado ao final do arquivo**.
    
    - **Exemplo:** `echo "Nova linha" >> resultados.txt` (adiciona texto ao arquivo existente).
        
- **`<` (Redirecionar STDIN):** Usa o conteúdo de um arquivo como entrada padrão para um comando.
    
    - **Exemplo:** `cat < resultados.txt` (o `cat` lê do arquivo em vez do teclado).
        
- **`2>` (Redirecionar STDERR):** Permite controlar especificamente o fluxo de erro.
    
    - **Exemplo Prático (O Mais Importante!):** `find /etc/ -name shadow 2> /dev/null`
        
        - Este comando envia todas as mensagens de erro ("Permissão negada", etc.) para o `/dev/null`, que é o "buraco negro" do Linux, efetivamente silenciando os erros.
            
- **Combinando Redirecionamentos:** Você pode controlar todos os fluxos ao mesmo tempo.
    
    - **Exemplo:** `find /etc/ -name shadow 1> saida.txt 2> erros.txt` (salva a saída bem-sucedida em um arquivo e os erros em outro).
        

#### **4. Pipes (`|`): Conectando Comandos**

O "pipe" é usado para pegar a **Saída Padrão (STDOUT)** de um comando e usá-la como **Entrada Padrão (STDIN)** para o comando seguinte. Ele cria uma "pipeline" de processamento.

- **Como funciona:** `comando1 | comando2`
    
    - A resposta do `comando1` não aparece na tela, ela é "encanada" diretamente para o `comando2`.
        
- **Exemplo 1 (Filtragem):** Procurar por arquivos `.conf` e filtrar apenas os que contêm a palavra "systemd".
    
    Bash
    
    ```
    find /etc/ -name *.conf 2>/dev/null | grep systemd
    ```
    
- **Exemplo 2 (Encadeamento Múltiplo):** Filtrar e depois contar os resultados.
    
    Bash
    
    ```
    find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l
    ```
    

**Conclusão:** Dominar redirecionamentos (`>`) e pipes (`|`) é uma habilidade essencial. Permite que você filtre ruído, salve resultados importantes, automatize tarefas e construa comandos complexos para encontrar exatamente a informação que precisa.




-----
# Referências:

