# Modos de desenvolvimento

# Desenvolvimento Sage X3

## Modos de Desenvolvimento

Atualmente, existem 4 modos de desenvolvimento no Sage X3:
### Modo Clássico

Modo das versões anteriores do Sage X3 baseado na linguagem de programação procedural

No modo Clássico, o Sage X3 é baseado em funções.

- As funções podem ser chamadas a partir de um item de menu e de outras funções.
- As funções servem como base para atribuição de direitos de acesso.
- As funções são identificadas por um código (variável GFONCTION, dica de texto nos menus do Sage X3).

No **Modo Clássico**, as páginas são baseadas no design do cliente para Windows versão 6. Este modo é uma emulação da versão 6, que não requer nenhuma modificação no repositório da versão 6 para funcionar. Os elementos armazenados no dicionário de ecrãs, dicionário de ações, dicionário de janelas, assim como os scripts projetados para a versão 6 são usados neste modo.
Os princípios básicos da ergonomia da versão 6 ainda estão presentes:
- A interface é controlada pelo servidor.
- Um controle de bloqueio de campo não pode ser ignorado e deve ser preenchido antes que outro campo possa ser preenchido.
- O controle é síncrono.

Em baixo é apresentado um exemplo de uma página Clássica na **versão 6**, mostrando os elementos de navegação.
{{< img src="images/ScreenV6.png" >}}

Em baixo é apresentado um exemplo de uma página Clássica na **versão 12**, mostrando os elementos de navegação.
{{< img src="images/ScreenV12.png" >}}

#### Organização da página Clássica

- Uma lista à esquerda (se aplicável) com várias caixas.
- Uma página central onde a informação é mostrada.
- Um painel à direita com links adicionais.

A lista à esquerda é usada para seleção e operações de escolha. É possível filtrar na primeira linha da lista, inserindo valores que podem ser prefixados por um operador. O operador padrão utilizado é "contendo".
Os botões "Anterior" e "Seguinte" são utilizados para aceder à página anterior ou seguinte de registos numa lista.
Podem existir vários painéis à esquerda, especialmente um painel de últimos registos lidos que lista os registos acedidos recentemente.
A página central contém diferentes campos que são definidos pela aplicação.

A transição de uma função existente para o modo Nativo pode levar um tempo significativo. Para garantir a disponibilidade de todas as funções Clássicas com o novo cliente via browser, mesmo que os desenvolvedores ou parceiros de negócios não tenham tido tempo para fazer a transição do código, o modo Clássico ainda está incorporado no ambiente mais recente, podendo ser utilizadas as funções existentes.

Como a reorganização do código pode levar tempo e para simplificar a transição entre o desenvolvimento Clássico e o desenvolvimento Nativo, uma camada adicional de interface do utilizador chamada Transição foi desenvolvida para ambientes desde a versão 7.

- Hospedada pelo servidor Web, essa camada suporta uma interface do utilizador envolta na estrutura do modo Nativo, mas com um estilo muito próximo ao do modo Nativo.

- Nesse modo, é estabelecida uma conexão entre o servidor Web e o motor X3 em condições equivalentes às existentes na versão 6. Além disso, o servidor do modo Nativo age como um simples proxy nesse caso.

- A transição de uma página do modo Nativo para um ecrã de fusão é relativamente transparente (o ecrã de Transição sobrepõe-se à página do modo Nativo), mas as funções avançadas não estão disponíveis.

- O cliente de transição, ainda em desenvolvimento, estará disponível em vários navegadores e será capaz de executar as ecrãs Clássicos sem qualquer reorganização de código.
  - A autoria é limitada nesse modo.
  - A interface móvel não está disponível nesse modo.

- Funciona com os seguintes princípios:

  - Num painel de controle, um item de menu pode referir-se a uma função Clássica pelo seu nome. Quando isso acontece, durante a execução, uma página é aberta mostrando o ecrã Clássico e usando o protocolo da versão 6 para se conectar ao servidor X3.

  - A função Clássica chamada dessa maneira funciona com as mesmas características presentes na versão 6.

    - Uma lista à esquerda está disponível.
    - Os controles são bloqueantes e síncronos.
    - O movimento do cursor é completamente controlado pelo servidor e não é possível fazer alterações nessas páginas.

- O visual do ecrã foi projetado para ser o mais próximo possível do visual das novas páginas do modo Nativo.

- O modo Clássico pode exigir apenas modificações mínimas no código existente da versão 6 para funcionar.

#### Comportamento principal de uma página no modo Clássico

Os diferentes atalhos que existiam na versão 6 (como as teclas de função F2, F5, F6, F9, F11, F12...) foram substituídos por uma combinação da tecla ESC e a mesma tecla de função, pois as teclas de função são geridas pelos navegadores e podem ter usos diferentes dependendo do navegador.

#### Gestão de páginas

Quando uma página no modo Clássico é aberta, é utilizada uma conexão do tipo v6 com um processo X3. Na primeira vez que isso ocorre, o tempo de conexão pode levar vários segundos (como acontecia com uma conexão v6).

- Fechar uma página no modo Clássico irá sair da função atual e perder quaisquer dados modificados. Será o mesmo se o botão de voltar for usado ou se outro URL for digitado. Se houver um trabalho pendente, aparecerá uma caixa de diálogo para solicitar uma confirmação.

#### Navegação local

Uma página no modo Clássico pode chamar outra página no modo Clássico (usando uma seleção, usando o atalho Esc+F7, chamando outra entidade - operação conhecida como "tunel" na terminologia da versão 6 - ou seguindo outro link). Quando isso acontece, uma nova página no Modo Clássico é empilhada sobre a anterior, e isso pode ser repetido. Um rastro de navegação aparece no topo da página.

- Clicar no "x" presente apenas na última parte do rastro de navegação fechará a página e retornará à anterior (a operação de fechar terá o mesmo efeito).

- Também é possível abrir uma função que empilha uma página adicional com o link "Ir para função" (conforme mencionado acima). A página que é aberta é exatamente a mesma que a página exibida na versão 6 ao digitar a tecla F7.

#### Tempo limite:

A sessão no Modo Clássico é gerida com o protocolo v6; portanto, é possível desconectar uma sessão após ocorrer um tempo limite. Quando isso acontece, é exibida uma janela de confirmação.

- Se o utilizador não responder "Não", a página é fechada e é apresentado o portal do Modo Nativo. Uma barra azul localizada abaixo da barra principal fornece ao utilizador informações sobre a desconexão por tempo limite.

#### Organização global da página no modo Clássico:

- A organização de uma página no modo Clássico é a mesma que uma página na versão 6, exceto pelo fato de que os menus e botões estão localizados numa barra vertical do lado direito. Isso significa que encontraremos em tal página:

  - Uma lista à esquerda (se aplicável) com várias caixas.
  - Uma página central onde os dados estão localizados.
  - Uma barra lateral direita com links adicionais.
  - Os painéis esquerdo e direito podem ser ocultados para fornecer mais espaço aos dados da aplicação. Os ícones fecham o painel direito e esquerdo, mas o atalho direto ESC+F11 fecha ambos os painéis em uma única operação. Quando os painéis estão fechados, ESC+F11 reabre-os.

#### Gestão de ecrãs tipo quadro nas páginas do modo Clássico

A gestão dos ecrãs tipo quadro funciona de forma diferente em relação à versão 6: deixou de haver foco intermédio numa linha antes de ter o foco numa célula. Portanto, um único clique leva diretamente ao modo de edição numa célula, não sendo mais necessário um clique duplo como na versão 6.

- Pressionar Esc em uma linha continua a sair da modificação da linha, e pressionar Enter em um campo na grade leva ao primeiro campo localizado após a grade.

### Modo apenas-leitura

Para apresenção de dados de representações e classes, não permite modificação de dados

### Modo nativo

Este modo é baseado na linguagem de programação orientada a objetos e foi introduzida na versão 7

### Modo intermédio

É um modo hibrído, que mistura o modo clássico com o modo nativo

