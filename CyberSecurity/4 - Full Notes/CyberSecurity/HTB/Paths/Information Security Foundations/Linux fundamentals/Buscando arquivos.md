2025-10-18
Tags: [[HTB]]

----
# Conceito Geral:

##### Comando find:

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

#### Descritores de arquivo e redirecionamentos:




-----
# Referências:

