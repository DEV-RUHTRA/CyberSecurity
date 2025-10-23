
2025-10-23
Tags: [[HTB]]

----
# Conceito Geral:

#### **1. Conceitos Fundamentais**

- **Propriedade:** Cada arquivo/diretório pertence a um **Dono (owner)** e a um **Grupo (group)**.
    
- **Níveis de Acesso:** As permissões são definidas para três níveis:
    
    1. **Owner (Dono):** O usuário proprietário.
        
    2. **Group (Grupo):** Membros do grupo associado.
        
    3. **Others (Outros):** Todos os demais usuários no sistema.
        

#### **2. As Três Permissões Básicas (`r`, `w`, `x`)**

As permissões têm significados diferentes para arquivos e diretórios:

|**Permissão**|**Para ARQUIVOS**|**Para DIRETÓRIOS**|
|---|---|---|
|**`r` (Read)**|Permite ler o conteúdo do arquivo.|Permite listar os arquivos dentro do diretório (`ls`).|
|**`w` (Write)**|Permite modificar ou apagar o arquivo.|Permite criar, apagar ou renomear arquivos dentro do diretório.|
|**`x` (Execute)**|Permite executar o arquivo (como um script ou programa).|Permite "entrar" no diretório (`cd`). **(Crucial!)**|

**Ponto Chave:** Você não pode acessar o conteúdo de um diretório (mesmo para ler um arquivo dentro dele) se você não tiver a permissão de **execução (`x`)** naquele diretório.

#### **3. Comandos de Gerenciamento**

- **`ls -l` (Listar):** Mostra as permissões detalhadas.
    
    - Ex: `-rwxr-xr--`
        
    - `1º caractere`: Tipo (`-` = arquivo, `d` = diretório, `l` = link).
        
    - `Caracteres 2-4`: Permissões do Dono (`rwx`).
        
    - `Caracteres 5-7`: Permissões do Grupo (`r-x`).
        
    - `Caracteres 8-10`: Permissões dos Outros (`r--`).
        
- **`chmod` (Change Mode):** Altera as permissões de um arquivo/diretório.
    
    - **Método Simbólico:** Usa referências (`u`=dono, `g`=grupo, `o`=outros, `a`=todos) e operadores (`+`=adicionar, `-`=remover).
        
        - Ex: `chmod a+r shell` (adiciona permissão de leitura para todos).
            
    - **Método Octal (Numérico):** Usa números baseados na soma dos valores: `r=4`, `w=2`, `x=1`.
        
        - Ex: `chmod 754 shell`
            
            - Dono: `7` (4+2+1 = `rwx`)
                
            - Grupo: `5` (4+0+1 = `r-x`)
                
            - Outros: `4` (4+0+0 = `r--`)
                
- **`chown` (Change Owner):** Altera o proprietário (dono e/ou grupo).
    
    - Ex: `chown root:root shell` (define o dono como "root" e o grupo como "root").
        

#### **4. Permissões Especiais (Críticas para Cibersegurança)**

- **SUID (Set User ID):**
    
    - **O que é:** Quando aplicado a um arquivo executável, permite que qualquer usuário execute esse arquivo com as permissões do **Dono** do arquivo (não do usuário que o executou).
        
    - **Como identificar:** Aparece como um `s` no lugar do `x` do dono (ex: `-r**s**r-xr-x`).
        
    - **Risco (GTFObins):** Se um SUID é definido em um programa que pode gerar um shell (como `find`, `vim`, `journalctl`), um usuário comum pode usá-lo para "escalar privilégios" e se tornar `root`.
        
- **SGID (Set Group ID):**
    
    - **O que é:** Similar ao SUID, mas faz o programa ser executado com as permissões do **Grupo** do arquivo.
        
    - **Como identificar:** Aparece como um `s` no lugar do `x` do grupo (ex: `-rwx**s**-xr-x`).
        
- **Sticky Bit:**
    
    - **O que é:** Uma permissão aplicada apenas a **diretórios**. Quando ativa, impede que usuários apaguem ou renomeiem arquivos que não lhes pertencem, mesmo que tenham permissão de escrita (`w`) no diretório (ex: o diretório `/tmp`).
        
    - **Como identificar:** Aparece como um `t` (ou `T`) no lugar do `x` dos "Outros".
        
        - `t` (minúsculo): Sticky bit + `x` (execução) para outros.
            
        - `T` (maiúsculo): Sticky bit, mas sem `x` (execução) para outros.

-----
# Referências:

