2025-10-20
Tags: [[HTB]]

----
# Conceito Geral:

### **Ferramentas de Filtragem e Manipulação de Texto no Linux**

#### **1. Visualizadores de Arquivos (Pagers)**

- **`more`**: Permite visualizar o conteúdo de arquivos grandes, uma página por vez. Ao sair (com `Q`), o texto permanece no terminal.
    
- **`less`**: Uma versão mais poderosa do `more`. Permite rolar para cima e para baixo. Ao sair, a tela do terminal é limpa.
    

#### **2. Visualizadores Parciais**

- **`head`**: Mostra as **10 primeiras linhas** de um arquivo por padrão.
    
- **`tail`**: Mostra as **10 últimas linhas** de um arquivo por padrão.
    

#### **3. Ferramentas de Filtragem e Busca**

- **`sort`**: Organiza as linhas de um arquivo em ordem alfabética ou numérica.
    
- **`grep`**: A ferramenta mais importante para **buscar padrões** de texto.
    
    - `grep "palavra"`: Mostra apenas as linhas que contêm a "palavra".
        
    - `grep -v "palavra"`: Inverte a busca, mostrando as linhas que **NÃO** contêm a "palavra".
        

#### **4. Ferramentas de Manipulação e Formatação**

- **`cut`**: **Corta** e exibe seções específicas de cada linha, com base em um delimitador.
    
    - Exemplo: `cut -d":" -f1` usa `:` como delimitador e exibe apenas o primeiro campo.
        
- **`tr`**: **Traduz** ou substitui um conjunto de caracteres por outro.
    
    - Exemplo: `tr ":" " "` substitui todos os `:` por espaços.
        
- **`column -t`**: Formata a saída em colunas alinhadas, criando uma tabela legível.
    
- **`awk`**: Uma linguagem de programação poderosa para processar texto. Permite manipular colunas e realizar ações complexas.
    
    - Exemplo: `awk '{print $1, $NF}'` exibe o primeiro (`$1`) e o último (`$NF`) campo de cada linha.
        
- **`sed`**: Um editor de fluxo para **substituir** texto com base em padrões (regex).
    
    - Exemplo: `sed 's/bin/HTB/g'` substitui todas (`g`) as ocorrências de "bin" por "HTB".
        

#### **5. Ferramenta de Contagem**

- **`wc` (Word Count)**: Conta linhas, palavras e caracteres em um texto.
    
    - `wc -l`: A opção mais útil, conta apenas o número de **l**inhas.

-----
# Referências:


