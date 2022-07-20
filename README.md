# T03-ORM-e-ODBC-20-07-22
## ORM - Object Relational Mapper
<p>ORM ou mapeador objeto relaciona, é um tipo de ferramenta muito utilizada hoje em dia, com o propósito de unir o mundo orietado a objetos e o mundo relacional.
<p>Este crescimento tem se dado principalmente pelo fato de muitos desenvolvedores não se sentirem a vontade em escrever código SQL e pela produtividade que esta técnica nos proporciona. Existem ótimos ORM´s como Hibernate, NHibernate, Entity Framework e etc.

  ![ORM](https://www.devmedia.com.br/imagens/articles/233575/orm.png)
  
<p>No mundo relacional prevalecem princípios matemáticos com a finalidade de armazenar e gerenciar corretamente os dados, de forma segura e se trabalha com a linguagem SQL que é utilizada para dizer o banco de dados “O QUE?” fazer e não como fazer.
<p> Já no mundo orientado a objetos trabalhamos com classes e métodos, ou seja, trabalhamos fundamentados na engenharia de software e seus princípios que nos dizem “COMO” fazer. O ORM é justamente, a ponte entre estes dois mundos, ou seja, é ele quem vai permitir que você armazene os seus objetos no banco de dados.
  <p>Para isto precisamos fazer um mapeamento dos seus objetos para as tabelas do banco de dados.
    
![Como o ORM trabalha](https://www.devmedia.com.br/imagens/articles/233575/ORM-Overview.png)
    
<p>A imagem nos traz uma ideia de como o ORM trabalha. Ela faz o mapeamento da classe para o banco de dados e cada ORM tem suas particularidades para gerar o SQL referente a inserção do objeto que corresponde a uma tabela no banco de dados e realizar a operação. Utilizando um ORM, também se ganha produtividade, pois deixa-se de escrever os comando SQL para deixar que o próprio ORM, faça isto por você.

## ODBC
