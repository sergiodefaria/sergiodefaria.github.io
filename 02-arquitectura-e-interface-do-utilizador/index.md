# Arquitectura e interface do utilizador

# Arquitetura Geral do Sage X3
O Sage X3 é um software de planeamento de recursos empresariais (ERP) que ajuda as empresas a gerir vários aspetos das suas operações, incluindo finanças, distribuição, fabrico e muito mais. A arquitetura geral do Sage X3 consiste em várias camadas que trabalham em conjunto para fornecer uma solução de software robusta e escalável.

Este artigo fornece uma visão da arquitetura geral do Sage X3 e discute as várias camadas que criam a base do software. Isso inclui a camada de código de aplicação utilizada para desenvolver e gerir o software, uma visão geral dos elementos da interface de utilizador comum e do processo geral de desenvolvimento.
Os tópicos deste artigo são:

- Arquitetura geral
- Arquitetura da aplicação
- Processo geral de desenvolvimento

## Arquitetura geral
O Sage X3 pode gerir o processamento de dados em vários servidores. O diagrama a seguir representa o modelo básico de arquitetura para o Sage X3. Esse modelo pode ser alterado de acordo com as necessidades de cada empresa.
{{< img src="images/x3architecture.png" >}}

O Sage X3 consiste em vários elementos de servidor, que podem ser instalados num só servidor, podem ser servidores separados ou uma combinação de servidores. Por exemplo, além dos servidores de aplicação e de base de dados, é possível ter um servidor web, um servidor de impressão, etc.

O Sage X3 foi projetado para utilizar clientes e servidor web. O acesso ao Sage X3 não requer a instalação de um cliente específico, uma vez que é feito por um navegador de Internet.

### Cliente baseado na web

- Conecção ao Sage X3 através da generalidade dos navegadores web mais utilizados ex. Chrome, Firefox, Edge, Opera, Safari,... 
  - Não há necessidade de um cliente pesado dedicado
- Permite uma conectividade mais fácil com o Sage X3 através de smartphones e tablets
- Utilização das funcionalidades da web
  - Favoritos / Histórico / Separadores / Navegação
  - Uso de links para navegar pelo sistema.

### Servidor web
Existe também um novo servidor web para substituir a versão anterior do servidor web:

- O servidor web é um servidor http

  - Assíncrono, muito rápido, baseado em node.js (em vez do anterior Apache)
  - Funciona com URL e envia de volta para o cliente feeds JSON que são SData normalizados
  - O supervisor e o motor do X3 enviam os mesmos feeds SData
  - Cada página tem sua própria URL

- O protocolo X3 funciona no modo "Web completo" em 2 modos diferentes:

  - Sem estado (consulta, exibição detalhada de qualquer página): sem bloqueio, nenhum contexto salvo
  - Com estado (quando uma modificação está em andamento): um rascunho existe no lado web, uma cópia de trabalho existe no servidor, ambas trocam assincronamente as modificações feitas

- Quando uma página (um serviço) é solicitada:

  - O supervisor envia primeiro um protótipo (definição de metadados) para construir a interface do utilizador
  - Os dados são enviados numa segunda etapa

### Navegadores web suportados

- A interface web permite que a utilização de qualquer um dos seguintes navegadores web:
  - Internet Explorer 
  - Firefox 
  - Chrome 
  - Safari 
  - Opera

- Permite o acesso às funções web:

  - Histórico, Favoritos, Separadores, que são gerenciados automaticamente pelo navegador.
  - Capacidade offline.
  - Links interativos e contextuais em vez de botões.

### Dispositivos móveis suportados

- Permite o uso de smartphones e tablets:
  - IPhone, Ipad
  - Android

## Arquitetura da aplicação

A arquitetura do Sage X3 está organizada em camadas para que a gestão de dados, a execução de processos e a apresentação de informações sejam tratadas de forma independente. Essa arquitetura de vários níveis garante operações do sistema altamente confiáveis em todas as circunstâncias. A arquitetura da aplicação do Sage X3 é composta pelas seguintes camadas: Código da aplicação, Supervisor, Motor X3, Base de dados e Sistema operativo.

{{< img src="images/x3ApplicationArchitecture.png" >}}

### Camada de código da aplicação

Esta série de artigos vão-se focar principalmente na camada de código da aplicação, que lida com a lógica de negócio, processos standard, processos verticais e processos específicos. A separação desses processos permite personalizar o sistema e desenvolver rotinas específicas da empresa, ao mesmo tempo em que mantém o código específico ou personalizado seguro em relação a futuras atualizações de versões.

> **Código da aplicação**
>> - Lógica de negócio
>> - Processos Standard (SUB*, TRT*, CNS*)
>> - Processos Verticais (SPV*, X*)
>> - Processos Específicos (SPE*, Y*, Z*)

- O código da aplicação é atualizado a partir do próprio Sage X3. Essas atualizações referem-se à lógica de negócio contida no Sage X3, como encomendas de venda, encomendas de compra e faturação. (Isso difere da atualização da plataforma, que envolve a Consola Sage X3 e afeta a arquitetura geral da solução Sage X3 a nível de componente.)

- O nível de atualização do código da aplicação geralmente é independente dos níveis de atualização da plataforma.
A camada de código da aplicação é onde escrevemos o nosso código. É também onde o sistema básico e a interface do utilizador são escritos.

- Toda a lógica de negócio, como encomendas de venda, encomendas de compra, faturação e produção, ocorre na camada de código da aplicação.

- Quando se instala o Sage X3, existem processos padrão que vêm com o software.

- Os processos verticais (SPVs) modificam o Sage X3 para atender às necessidades de uma indústria ou legislação para vários clientes.

- Os processos específicos permitem que os parceiros Sage ou os clientes escrevam melhorias específicas que são exclusivas (ou "específicas") para essa implementação.

### Camada do Supervisor:
A camada do supervisor é composta pelos seguintes elementos.

> **Supervisor**
>> - Base de Dados e Configuração
>> - Utilizadores e Direitos de Acesso
>> - Gestão de consultas de dados (Estatistícas, Listas, Acesso a Dados...)
>> - Parâmetros da aplicação
>> - Gestão de tarefas batch
>> - Gestão de versões e atualizações
>> - Plataforma de desenvolvimento para personalizações específicas

- Esta é a camada que funciona abaixo da camada de código da aplicação e é onde ocorre a configuração da bade de dados a partir do Sage X3 (não do Microsoft SQL Server ou Oracle).
- Os direitos de utilizador e acesso também são definidos nesta camada, assim como a gestão de pesquisa de dados, parâmetros da aplicação, gestão de tarefas batch, gestão de versões e atualizações, e plataforma de desenvolvimento para personalizações específicas.

- Várias questões de desenvolvimento são tratadas automaticamente pelo supervisor.
  - Cabeçalhos e Linhas: O supervisor agora lida com isso internamente. Como desenvolvedores, não é necessário escrever código específico para lidar com cabeçalhos e linhas. Ele também permite ter vários conjuntos de linhas em relação a um cabeçalho (em vez de apenas um) e também a capacidade de ter sublinhas para as linhas.

- Fácil integração com sistemas externos
  - Integração do Office: O novo cliente web gere a integração do Office por meio de um suplemento. O Office é visto como um cliente. Isso é uma grande mudança em relação à versão 6, porque agora o suplemento do Office conecta-se ao servidor web para obter os dados e usa o mesmo protocolo que o cliente web. Além disso, nenhum desenvolvimento precisa ser feito no servidor ou nos documentos do Office.
  - Web Services: Fornece uma interface consistente para os dados, ou seja, não estará mais limitado aos objetos com os quais se deseja interagir.

