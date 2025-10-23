2025-10-22
Tags: [[HTB]]

----
# Conceito Geral:

#### **O que é RegEx?**

- **Definição:** Expressões Regulares (RegEx) são padrões de busca usados para encontrar, substituir ou manipular textos com alta precisão.
    
- **Como Funciona:** Elas usam uma sequência de caracteres normais e símbolos especiais (chamados **metacaracteres**) para definir um padrão de busca. Por exemplo, metacaracteres podem definir "qualquer dígito" ou "qualquer letra".
    
- **Onde Usar:** São ferramentas essenciais em linguagens de programação e em comandos de terminal como `grep` e `sed`.
    

#### **2. Operadores de Agrupamento**

Para usar os operadores de agrupamento (`()`, `|`) no `grep`, é necessário usar a opção `-E` (Expressão Regular Estendida).

| **Operador** | **Exemplo** | **Descrição**                                                                                                                            |
| ------------ | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **`()`**     | `(padrão)`  | **Agrupador:** Trata o que está dentro como uma única unidade.                                                                           |
| **`[]`**     | `[a-z]`     | **Classe de Caracteres:** Encontra qualquer caractere dentro dos colchetes (ex: `[abc]` encontra 'a', 'b' ou 'c').                       |
| **`{}`**     | `{1,10}`    | **Quantificador:** Define quantas vezes o padrão anterior deve se repetir (ex: `{1,10}` = de 1 a 10 vezes).                              |
| **`\|`**     | `(a\|b)`    | **Operador OU (OR):** Encontra linhas que contenham _ou_ o padrão `a` _ou_ o padrão `b`.                                                 |
| **`.*`**     | `(a.*b)`    | **Operador E (AND):** Encontra linhas que contenham o padrão `a` _e_ o padrão `b`, **naquela ordem**, com qualquer coisa (`.*`) no meio. |

#### **3. Exemplos Práticos com `grep -E`**

- **Operador OU (`|`):**
    
    - **Objetivo:** Encontrar linhas que contenham "my" **OU** "false".
        
    - **Comando:** `grep -E "(my|false)" /etc/passwd`
        
    - **Resultado:** Mostra todas as linhas que contêm pelo menos uma das duas palavras.
        
- **Operador E (`.*`):**
    
    - **Objetivo:** Encontrar linhas que contenham "my" **E** "false" (com "my" aparecendo antes de "false").
        
    - **Comando:** `grep -E "(my.*false)" /etc/passwd`
        
    - **Resultado:** Mostra apenas as linhas onde ambas as palavras estão presentes na ordem especificada.
        
- **Alternativa para "E" (Usando Pipes):**
    
    - Uma forma mais simples de conseguir um resultado "E" (sem se importar com a ordem) é usar o `pipe` (`|`) para encadear dois `grep`:
        
    - **Comando:** `grep -E "my" /etc/passwd | grep -E "false"`
        
    - **Resultado:** O primeiro `grep` encontra todas as linhas com "my"; o segundo `grep` filtra essa lista, mostrando apenas as que _também_ contêm "false".

-----
# Referências:

