# Estrutura de desenvolvimento no modo clássico

Este artigo fornece informações sobre como uma função do Sage X3 é construída. Nos artigos seguintes, darei mais detalhes sobre a criação da interface gráfica do utilizador e o processamento que ocorre nos bastidores.

Muitos componentes são usados para construir e gerar uma função do Sage X3. O ponto de partida é criar uma tabela que irá armazenar os dados. Os ecrãs são utilizados para exibir dados de uma ou mais tabelas de referência para entrada de dados. As Janelas agrupam ecrãs num conjunto.

{{< img src="images/processoGeralDesenv.png" >}}

Um modelo de objeto pode ser usado para manter os dados da tabela principal desse objeto. Por exemplo, para encomendas de venda, o objeto principal é SOH, que gere a tabela de cabeçalho de encomendas de venda. Um objeto pode ser referenciado por uma função. Por sua vez, as funções podem ser iniciadas a partir de um bloco na página de navegação do Sage X3.

{{< img src="images/object.png" >}}
