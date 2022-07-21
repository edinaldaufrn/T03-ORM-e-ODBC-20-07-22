# T03-ORM-e-ODBC-20-07-22
## ORM - Object Relational Mapper
<p>ORM ou mapeador objeto relaciona, é um tipo de ferramenta muito utilizada hoje em dia, com o propósito de unir o mundo orietado a objetos e o mundo relacional.
<p>Este crescimento tem se dado principalmente pelo fato de muitos desenvolvedores não se sentirem a vontade em escrever código SQL e pela produtividade que esta técnica nos proporciona. Existem ótimos ORM´s como Hibernate, NHibernate, Entity Framework e etc.

  ![ORM](https://www.devmedia.com.br/imagens/articles/233575/orm.png)
  
<p>No mundo relacional prevalecem princípios matemáticos com a finalidade de armazenar e gerenciar corretamente os dados, de forma segura e se trabalha com a linguagem SQL que é utilizada para dizer o banco de dados “O QUE?” fazer e não como fazer.
<p> Já no mundo orientado a objetos trabalha-se com classes e métodos, ou seja, trabalha-se fundamentados na engenharia de software e seus princípios que nos dizem “COMO” fazer. O ORM é justamente, a ponte entre estes dois mundos, ou seja, é ele quem vai permitir que você armazene os seus objetos no banco de dados.
  <p>Para isto é preciso fazer um mapeamento dos objetos para as tabelas do banco de dados.
    
![Como o ORM trabalha](https://www.devmedia.com.br/imagens/articles/233575/ORM-Overview.png)
    
<p>A imagem nos traz uma ideia de como o ORM trabalha. Ela faz o mapeamento da classe para o banco de dados e cada ORM tem suas particularidades para gerar o SQL referente a inserção do objeto que corresponde a uma tabela no banco de dados e realizar a operação. Utilizando ORM, também se ganha produtividade, pois deixa-se de escrever os comando SQL para deixar que o próprio ORM, faça isto por você.

## ODBC
  
# Tutorial
## ORM - Object Relational Mapping - Revista Easy .Net Magazine 28
<p>Neste tutorial veremos os conceitos principais por trás da técnica e dos frameworks ORMs, como a sua mecânica e funcionamento. Veremos o que são e como trabalham, conceituando as principais características destes e apresentando quais os principais frameworks existentes no mercado.
<p>Por exemplo: Quase todo sistema precisa gravar dados durante seu uso que podem ser guardados para posterior processamento ou leitura como, por exemplo, num sistema de uma loja que precisa guardar os dados dos produtos, vendas, funcionários, dentre outros.
<p>No mundo .NET temos um caminho padrão para acessar dados em SGDBs relacionais através do ADO.NET, biblioteca que nos fornece diversas classes para acesso e manipulação de dados, não somente de SGDBs relacionais como também de XMLs e documentos do Office (como excel e access).
<p>Por outro lado, ao adotar uma solução baseada puramente em ADO.NET sofremos com alguns problemas, como:
1.Temos que escrever todo o SQL de nossa aplicação manualmente, tornando o desenvolvimento do projeto muito mais improdutivo.
2.Temos que nos preocupar em não usar nenhum código SQL específico de determinado SGDB para não corrermos o risco de ficarmos preso ao mesmo.
3.Temos mais classes para gerenciar e dar manutenção.
<p>Além disso, o modelo de dados relacional possui algumas limitações em comparação com o modelo de objetos (Nota do DevMan 1), como por exemplo:
1.Não possui herança
2.Não possui polimorfismo
3.Não permite relações N para N entre duas entidades (tabelas)
<p>Diante disto, corremos o risco de limitar a arquitetura de nossa aplicação orientada a objetos ao modelo relacional. Para resolvermos este problema precisamos realizar um parse dos dados de um modelo para o outro. Este parse pode ser feito manualmente, através de consultas SQL acessando as tabelas de nosso banco de dados e alimentando objetos de nossa aplicação, ou de forma automática utilizando uma camada de mapeamento, chamada ORM.
<p>ORM (Object Relational Mapping) é uma técnica para mapeamento entre um modelo de dados relacional e um modelo orientado a objetos que visa resolver, ou pelo menos minimizar, as diferenças entres estes dois modelos. Para facilitar a aplicação desta técnica surgiram os frameworks ORM, como por exemplo, o NHibernate e o Entity Framework. Desta forma, esses frameworks se localizam em uma camada intermediária entre a lógica da sua aplicação e o seu SGDB.
<p>O framework passa a receber as solicitações de interação com o SGDB através de objetos de sua aplicação e gera automaticamente todo o SQL necessário para a operação solicitada, nos poupando do trabalho de escrita e manutenção deste SQL e abstraindo o uso do SGDB, fazendo com que nos preocupemos apenas com nosso modelo de objetos. Além disso, o framework já trata as variações de tipos de dados existentes entre nossa aplicação e nosso SGDB.
<p>Com isso, a aplicação passa a interagir com o framework e não mais com a base de dados diretamente, desacoplando nosso sistema de SGDBs específicos. Além disso, com uso de frameworks ORM a produtividade aumenta devido ao fato de não precisarmos escrever códigos SQL para inserir, alterar, excluir e recuperar dados do SGDB.
##Os Principais ORMs
<p>Os principais ORMs que trabalham com o .NET são o Entity Framework e NHibernate mas estes não são os únicos. A primeira tentativa de ORM da Microsoft no .NET foi o LinqToSQL, que ainda é usado por muita pessoas mas que aos poucos foi sendo substituído pelo Entity Framework. Na versão 4 do .NET a Microsoft anunciou que iria descontinuar o LinqToSql, tornando o Entity Framework a opção nativa para ORM.
<p>O Entity Framework vem ganhando melhorias muito rapidamente, no momento em que escrevo este artigo a versão 6 já está disponível em alpha e a opção da Microsoft por torná-lo Open Source aumentou o ritmo de melhorias e sugestões ao framework.
<p>Porém, o NHibernate ainda possui uma consideravel preferência por possuir uma comunidade ativa e por suportar mais escolhas de bancos de dados do que o Entity. A conversa sobre performace pode ser esquecida a partir da versão 5 do Entity Framework quando a performace se equiparou entre eles.
#Como funciona o ORM?
<p>O ORM funciona através do mapeamento das características da base de dados para os objetos de nossa aplicação. O primeiro conceito chave é traçar um paralelo entre Classe x Tabela e Propriedade x Coluna. O ORM nos permite informar em que tabela cada classe será persistida e em que coluna do SGDB cada propriedade ficará armazenada.

![Alt ou título da imagem](URL da imagem)
