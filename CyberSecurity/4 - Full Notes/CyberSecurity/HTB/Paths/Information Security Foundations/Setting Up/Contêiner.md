2025-09-29
Tags: [[HTB]] [[Docker]]

----
# Conceito Geral:

### O que são containers? 

Containers são uma forma de **"virtualizar"** o sistema pegando apenas o que é necessário.
![[containers-vs-virtual-machines.jpg]]

**Diferença entre Máquina Virtual e Container:**
![[Pasted image 20250930160323.png]]

Uma imagem do sistema de arquivos forma a base de cada contêiner. Podemos escolher entre usar uma imagem já criada ou criar uma nós mesmos. Os contêineres também se caracterizam por uma excelente escalabilidade. A escalabilidade aprimorada é ideal para atender aos requisitos da infraestrutura de TI, agora altamente dinâmica, nas empresas. De fato, a alta escalabilidade dos contêineres permite adaptar perfeitamente as capacidades para o fornecimento de aplicativos pelos usuários. Enquanto isso, mesmo grandes configurações de contêineres podem ser gerenciadas sem problemas graças a sistemas de orquestração como `Apache Mesos`ou `Google Kubernetes`. Esses sistemas distribuem os contêineres pelo hardware existente com base em regras predefinidas e os monitoram.

##### Além disso é crucial entender sobre Docker e Kubernetes:

- O **Docker** é a ferramenta mais popular para criar e gerencia Containers. O **Kubernetes (K8s)** é a ferramenta mais popular para orquestrar (gerenciar, escalar e automatizar) milhares de containers em produção. 

-----
# Referências:

