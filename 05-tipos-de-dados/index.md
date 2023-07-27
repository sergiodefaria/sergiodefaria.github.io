# Tipos de dados


# Tipos de Dados

Existem vários tipos de dados básicos predefinidos no Sage X3, como L (inteiro longo), D (Data), A (alfanumérico). Além disso, existe um conjunto de tipos "fortes"  construído com base em tipos fracos e em definições de objeto. Por exemplo, um campo do tipo BPC (Cliente) ou SOH (Encomendas de Vendas) pode ser definido, caso em que estará em conformidade com os parâmetros e formatos definidos para esses objetos. 

## Existem 3 categoria de tipos de dados

 - ### Básicos
    - Incorporados no software
    - Exemplos:
      - A (alfanumérico)
      - DCB (decimal)
      - D (data)
      - L (inteiro longo)
      - ...

  - ### Definidos pelo utilizador
    - Definidos especificando-se o tamanho, formato, opções de edição e acções opcionais (eventos)
    Exemplos:
      - MD1 (Formato moeda)
      - BID (Código bancário)
  
  - ### Objecto
    - Tipos objecto herdam o seguinte dos objectos base
      - Controlos
      - Túneis automáticos e caixas de selecção
      - Verificações de integridade dos dados

## Tipos de dados avançados

- ### Tipo interno:

  - Menu local
  - Inteiro curto/longo
  - Precisão dupla / Decimal de ponto flutuante
  - Clob/Blob
  - Alfanumérico
  - Data

- ### Formato Sage X3:
  - Expressão Sage X3 para formatos complexos
  - Formatos variáveis podem ser especificados inserindo uma expressão Sage X3 precedida pelo sinal '='
  - Opções adicionais estão disponíveis dependendo do tipo de dado básico.

- ### Tipos de dados definidos pelo utilizador 
  - Podem ser construídos com formatos fixos. Exemplos: SHO, NAM.
    - Isso permite que um formato amplamente utilizado seja definido em uma função central e usado em várias tabelas: os dados são homogêneos em todo o software. Além disso, quando o tipo de dado precisa ser alterado, apenas uma modificação é necessária e, em seguida, a revalidação de todos os elementos associados usando a função Desenvolvimento > Utilitários > Dicionário > Validação/Dicionário.

- ### Tipos de dados de objeto 
  - Estão vinculados a objetos e permitem que um campo seja automaticamente associado a um objeto: existem tipos de dados de cliente (BPC) ou tipos de dados de encomendas de venda (SOH). Quando um tipo de dado de objeto é atribuído a um campo de ecrã:
    - Um menu de contexto com clique direito automático está disponível nesse campo, fornecendo uma janela de seleção, um acesso rápido à função do objeto e um menu de propriedades.
    - A coerência dos dados é verificada automaticamente ao preencher o campo.
    - A designação do registro pode ser exibida dinamicamente à direita do campo.
