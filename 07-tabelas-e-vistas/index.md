# Tabelas e Vistas

# Tabelas e Campos

## Campos de tabela
- Os campos (colunas da tabela) são identificados principalmente pelos seguintes elementos:
  - Código
  - Tipo de dado e comprimento
  - Designação (Normal / Longa / Curta)
  - Dimensão
- Os campos podem estar associados a uma tabela de referência (Tabela Relacionada):
  - A expressão de vínculo contém os valores para vincular tabelas com índices complexos.
  - As opções de cancelamento especificam as verificações de integridade de dados a serem realizadas quando um registro relacionado é excluído.
- Tipos Fortes ou Fracos podem ser usados como campos de tabela. 
  Tipos Fortes estão principalmente relacionados com Objetos Sage X3 (por exemplo, Produtos (ITM), Clientes (BPC) etc.).
  Principais Tipos Fracos:
  - A (Texto/String)
  - C (Número inteiro curto)
  - L (Número inteiro longo)
  - D (Data)
  - DCB (Ponto Flutuante/Floating Point)

## Códigos de Campos
- Campos específicos podem ser adicionados às **tabelas standard** existentes. Nesse caso, seus códigos devem **começar com X, Y ou Z**. Códigos para campos adicionados a uma **tabela específica** podem começar com **qualquer letra**.
- Os códigos de campo standard são codificados usando pedaços de 3 letras em inglês. Por exemplo, o campo BPC é um cliente (Business Partner Customer) e o campo BPCORD é o cliente do pedido de vendas (ORD = Order). STOFCY é a STOring FaCilitY (Estabelecimento de Armazenagem), etc.
- O código do campo identifica o campo em todo o software Sage X3. Por exemplo, o campo MEUCAMPO na tabela XTABLE com a abreviação XTB será identificado por [F:XTB]MEUCAMPO.

## Descrição de Campos
- As três colunas de descrição definem as descrições dos campos como serão propostas por padrão no dicionário de ecrãs (dependendo do espaço disponível no ecrã, a descrição abreviada é limitada a 12 caracteres, a descrição normal a 20 caracteres e a descrição longa a 35 caracteres).

Essas descrições são textos traduzíveis e são armazenadas numa tabela dedicada, ATEXTE. Quando um novo texto é inserido, o programador tem a opção de selecionar um texto existente ou criar um novo (personalizado).

## Tipos de Dados no Sage X3
- No software Sage X3, vários tipos de dados "fracos" são predefinidos, como A (Texto/Caractere), C (Número inteiro curto), etc. No entanto, um conjunto de tipos de dados "fortes" foi criado, com base nos tipos fracos e nas definições de objetos (veja a seção Tipos de Dados). Por exemplo, um campo do tipo BPC (Clientes) ou SOH (Encomendas de Vendas) pode ser definido, e, nesse caso, ele seguirá os parâmetros e formatos definidos para esses objetos.

## Links de Integridade de Dados
- Um campo pode estar ligado a outra tabela no software, usando a coluna Tabela Ligada. Quando a tabela ligada possui um índice com mais de um componente, a Expressão de ligação contém os valores exatos aos quais o campo deve se ligar: seja constantes ou campos da tabela atual, expressos por seus códigos.
- A coluna Anulação define verificações de integridade de dados a serem realizadas quando o registo na tabela ligada é excluído:
  - **Bloqueante**: O registro na tabela ligada não pode ser excluído se houver algum registro que faça referência àquela chave na tabela atual.
  - **Suprimir**: Quando o registro na tabela ligada é excluído, todos os registros na tabela atual que fazem referência àquela chave serão excluídos.
  - **V. a Zero**: Quando o registro na tabela ligada é excluído, o valor do campo na tabela atual será substituído por um valor em branco.
  - **Outro**: Nenhuma verificação de integridade de dados.

## Restrições
- Cada ocorrência de um campo dimensionado é uma coluna na tabela da base de dados.
- O número máximo de campos nomeados é 255.
- O número máximo de colunas (Campo*dimensão) é 512.
- Tamanho Máximo do Registro
  - **MSSQL** - 8K (8 kilobytes)
  - **Oracle** - 32K (32 kilobytes)

