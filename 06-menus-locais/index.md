# Menus Locais


# Menus locais (Mensagens aplicativo)

Os menus locais definem listas de texto que aparecem como menus drop-down, botões de opção e caixas de seleção nos ecrãs do Sage X3. Os menus locais são também usados para mensagens em caixas de informações, erros, avisos, etc. A seguir, tem um exemplo de um menu local em forma de menu suspenso (menu drop-downn) definido na função Mensagens de menus locais (TXT) (sob Tabelas no bloco Desenvolvimento > Dados e parâmetros) e o resultado disso no campo Classe ABC na função Sites dos Produtos (no bloco Dados comuns > Categorias de produtos).

{{< img src="images/localmenus.jpg" >}}

**Organização dos menus locais**
- Os menus locais são agrupados em capítulos identificados por números.
- Cada texto num capítulo é identificado por um número sequencial a partir de 1.
- Cada menu local pode conter até 123 itens.
- Os capítulos de 1 a 999 são para desenvolvimento standard.
- Os capítulos de 1000 a 1999 e de 5200 a 5999 são reservados para desenvolvimentos verticais.
- Os capítulos de 4000 a 4999 são para complementos (add-ons).
- Os capítulos de 6000 a 6999 são para desenvolvimentos específicos (6000 a 6499 para Sage e 6500 a 6999 para clientes).

Observação: Essas convenções de numeração também estão disponíveis no sistema de Ajuda e são as mesmas convenções de numeração usadas para as tabelas diversas.

## Na base de dados:

- Os menus locais são armazenados em duas tabelas: `APLSTD` para mensagens (mensagens de informação, aviso e erro) e `AMENLOC` para menus locais (listas suspensas, etc.).
- Quando um campo contém um item de menu local, o número do texto é armazenado na base de dados em vez do próprio texto. O menu local mais utilizado é o capítulo 1, o menu Não/Sim.
  - Contém duas opções, os textos: Não (item 1) e Sim (item 2).
  - Está associado a todas as caixas de seleção e a um número de campos normais.
  - Como resultado, o valor Não nos ecrãs e tabelas do Sage X3 é 1, e o valor Sim é 2.

## Tabelas e campos de ecrã
- Os campos de tabela e de ecrã na base de dados podem estar associados a um menu local (tipo de dados M ou MM).
Nesse caso, apenas o número do texto é armazenado na base de dados, não o próprio texto. Isso significa que:
  - O texto é facilmente traduzível e pode ser visualizado em qualquer um dos idiomas disponíveis.
  - Quando o texto é modificado, nenhuma modificação de dados é necessária nos campos relacionados.

## A função mess()
- A função mess() retorna um texto de menu local. Ela é amplamente utilizada para exibir mensagens no software Sage X3. As mensagens nunca são escritas diretamente no código, mas sim criadas como menus locais e usadas por meio dessa função. Isso permite que todas as mensagens do aplicativo sejam traduzidas sem nenhuma alteração no código:

 - mess("Texto", "Capítulo", 1) retorna o número do texto "Texto" no capítulo "Capítulo".
Exemplo: mess(291, 192, 1) retorna "A loan order cannot be inter-site!" quando conectado em inglês, "Une commande de prêt ne peut pas être inter-sites !" quando conectado em francês, e "Encomenda de empréstimo n/pode ser inter-estab. !" em português.

## Utilização de Menus Locais
- O tipo de dados M identifica um Menu Local, juntamente com o número do capítulo:
  - Campos com esse tipo de dados apresentarão uma escolha de valores de texto.
    - Na forma de uma lista suspensa (drop-down).
    - Na forma de botões de rádio (Radio buttons).
    - Como uma caixa de seleção para o menu Sim/Não (Capítulo 1).
- O tipo de dados MM identifica um Menu Local modificável pelo usuário:
- Num único capítulo, os textos são identificados por números na faixa de 1 a 123.
- Menus locais usados como mensagens do aplicativo podem ser acedidos usando a instrução mess().
    - mess(1, 110, 1) retorna o texto 1 do capítulo 110 no idioma da conexão.
- Menus locais específicos podem ser criados nos capítulos designados.
  - Eles podem ser identificados usando a opção para mostrar os intervalos reservados.
- Menus Locais vs. Mensagens:
  - Se um menu local não é explicitamente marcado como "menu local", então é uma mensagem.
  - Os textos são identificados por números na faixa de 1 a 9999.
  - Os valores não podem ser alterados pelos utilizadores.
  - Não são transferidos para o computador do usuário (cliente-servidor).
  - Costumam ser usados para lidar com mensagens no código-fonte (mensagens de erro, etc.).
  - São também traduzíveis.
  - São também armazenados na tabela APLSTD.


