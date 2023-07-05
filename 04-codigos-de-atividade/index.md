# Códigos de atividade


# Os códigos de atividade são códigos de assinatura usados para realizar o seguinte:

**Proteger e identificar desenvolvimentos específicos (Tipo = Funcional)**
- Os códigos de atividade verticais devem começar com X
- Os códigos de atividade específicos devem começar com Y ou Z
- Proteção na instalação de patches e atualizações
- Identificação para extração de patch e validação de dicionário

**Ativar ou desativar elementos do Sage X3 (Tipo = Funcional)**
- Tabelas, índices de tabelas, campos de tabelas
- Ecrãs, blocos de ecrãs, campos de ecrãs
- Objetos, parâmetros individuais do objeto
- Separadores de janelas

**Anexar uma dimensão personalizável aos elementos de matriz (Tipo = Dimensão)**
- Campos de tabela
- Campos de ecrã

**Identificar localizações (Tipo = Localização)**
- Os códigos de atividade de localização devem começar com a letra K.

Quando um código de atividade funcional é associado a um elementos do dicionário (por exemplo, um bloco de ecrã, um campo de ecrã, um campo de tabela etc.) e ele está desativado (campo Ativo definido como Não), o sistema age como se esses elementos do dicionário não existissem: campos de ecrã não aparecem e não estão disponíveis na classe [M], campos de tabela não estão disponíveis na classe [F] e não estão presentes na base de dados, etc.

Todos os elementos associados a um código de atividade de dimensão recebem a mesma dimensão. Ao modificar a dimensão do código de atividade e validar novamente os elementos associados a ele, essa dimensão é aplicada a todos os elementos (principalmente blocos de ecrã e campos de ecrã e tabela).

## Definir códigos de atividade
Utilizar a função códigos de atividade (GESACV) em Configuração de desenvolvimento no bloco Desenvolvimento > Dicionário de Dados > Abertura à parametrização, para ativar ou desativar elementos no dicionário, como tabelas, índices de tabela, separadores, seções de ecrã ou campos. Por exemplo, pode-se optar por ativar ou desativar determinados campos em ecrãs. Este tópico fornece detalhes sobre a definição de códigos de atividade do ponto de vista de desenvolvimento.

{{< img src="images/activitycodes.jpg" >}}

- **Ativo:** Esta caixa de seleção ativa ou desativa um código de atividade, bem como todos os elementos do dicionário a ele associado (requer validação de pasta ou dicionário).

- **Rang (Sequência):** Define a ordem de aparência na função Dossier (GESADS).

- No campo **Tipo**, pode-se selecionar uma das seguintes opções:

  - **Funcional:** Quando um código de atividade funcional está associado a elementos do dicionário (como blocos de ecrã, campos de ecrã ou campos de tabela) e é desativado (a caixa de seleção Ativo é desmarcada), o sistema age como se esses elementos não existissem. Os campos de ecrã não aparecem e não estão disponíveis na classe [M], e os campos de tabela não estão disponíveis na classe [F].

  - **Dimensionamento:** Os códigos de atividade de dimensão ou dimensionamento são usados para dimensionar elementos do dicionário, como blocos de ecrã e campos de tabela e ecrã. Todos os elementos associados a um código de atividade de dimensão recebem a mesma dimensão. Ao modificar a dimensão do código de atividade e revalidar os elementos a ele associados, essa dimensão é aplicada a todos os elementos (principalmente blocos de ecrã e campos de tabela e ecrã).

  - **Localização:** Os códigos de atividade de localização são reservados para os programadores Sage X3 da Sage e são usados para ativar ou desativar recursos específicos de cada país. Esses códigos começam com a letra K.

- **Dependência:** O status de um código de atividade pode estar vinculado a outro código de atividade. Nesse caso, esse código de atividade não aparece na função Dossiers. No campo Dependência, pode-se selecionar entre as seguintes opções:

  - **Inverso:** Se o código de referência estiver ativo, o código vinculado estará inativo e vice-versa.

  - **Dimensionamento:** O tamanho será vinculado ao tamanho de um código de referência, mas não ao seu status.

  - **Fórmula:** Para dependência em mais do que um código de atividade, uma fórmula pode ser inserida. Exemplo: O código de atividade SLO depende dos códigos de atividade LOT e SLT e será ativo somente se ambos estiverem ativos. 
  A fórmula é: `LOT<>0 & SLT<>0`

## Gerir códigos de atividade

- Gerir códigos de atividade na função Dossiers

  - Os códigos de atividade **específicos** aparecem no separador Específicos na função Dossiers.

  - Os códigos de atividade **funcional** standard e os códigos de atividade de **localização** aparecem no separador Opções.

  - Os códigos de atividade de **dimensionamento** são listados no separador Ecrãs.

- Após modificar um código de atividade, os elementos aos quais ele está vinculado devem ser revalidados.

  - Através da validação completa de dossiers (função Dossiers).
  - Através da função de Validação do Dicionário (Desenvolvimento > Utilitários > Dicionário > Validações > Dicionário) com um filtro no código de atividade.

- A função de Pesquisa de Código de Atividade (Desenvolvimento > Utilitários > Pesquisas > Cód. de activ.) lista todos os elementos do Sage X3 vinculados a um único código de atividade.

## Utilizar códigos de atividade

Proteger os desenvolvimentos específicos utilizando códigos de atividade:

- Proteção contra **patches:** Evitar conflitos com patches que contenham os mesmos elementos.
- Proteção contra **atualizações:** Garantir a validação de dossiers e/ou alteração da versão da aplicação.
- É **obrigatório** associar e proteger todos os desenvolvimentos específicos usando códigos de atividade específicos (começando com X, Y ou Z):
  - Campos inseridos em tabelas ou ecrãs existentes.
  - Novos blocos em ecrãs standard.
  - Novos separadores em janelas standard.
  - Como regra geral, todos os **novos elementos** nos dicionários de desenvolvimento (todos os elementos sob o menu de Desenvolvimento).

- Não é necessário proteger elementos de **personalização** considerados como parametrização:
  - Alguns parâmetros de objeto, como parâmetros de seleção (função Personalização de Objeto).
  - Novos solicitantes, regras de workflow, parâmetros estatísticos etc., ou modificações dos standard.
  - Como regra geral, todos os elementos sob o menu **Parametrização**.

## Visualizar elementos associados a um código de atividade
Para visualizar todos os elementos vinculados a um único código de atividade, utilize a função "Código de Atividade" em Pesquisas no bloco Utilitários do menu Desenvolvimento. Insira um código de atividade e os elementos para pesquisar, em seguida, clique em OK. Isso permitirá que você veja uma lista dos elementos vinculados ao código de atividade especificado.

{{< img src="images/pesquisacodigoatividade.jpg" >}}
