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
*Temos que escrever todo o SQL de nossa aplicação manualmente, tornando o desenvolvimento do projeto muito mais improdutivo.
*Temos que nos preocupar em não usar nenhum código SQL específico de determinado SGDB para não corrermos o risco de ficarmos preso ao mesmo.
*Temos mais classes para gerenciar e dar manutenção.
<p>Além disso, o modelo de dados relacional possui algumas limitações em comparação com o modelo de objetos (Nota do DevMan 1), como por exemplo:
*Não possui herança
*Não possui polimorfismo
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
<p>Exemplo de mapeamento em XML com NHibernate.
  
~~
  <?xml version="1.0" encoding="utf-8" ?>
     <hibernate-mapping xmlns="urn:nhibernate-mapping-2.2"
         namespace="DevMedia.Exemplo " assembly="DevMedia.Exemplo">
       <class name="DevMedia.Exemplo.Cliente,
         DevMedia.Exemplo" table="TB_CLIENTE">
         <id name="Codigo" column="CodCliente"/>
         <property name="Nome"/>
         <property name="CPF"/>
       </class>
     </hibernate-mapping>
~~~~
  
<p>Pode-se observar um exemplo de mapeamento através do framework NHibernate. Veja que na linha 2 é definido o namespace e o assembly onde está a classe e na linha 3 é indicado o nome da mesma seguido do nome de sua respectiva tabela no banco de dados. Na linha 4 tem-se uma tag Id que indica que o campo Codigo da classe é o identificador do objeto, mapeando o mesmo para a coluna CodCliente que é a chave primária da tabela. Por fim, nas linhas 5 e 6 temos o mapeamento das propriedades da classe Cliente. Vale ressaltar que nestes casos não foi informado o nome da coluna no banco de dados, pois as colunas possuem o mesmo nome das propriedades do objeto Cliente.
<p>Com todo este mapeamento realizado, o framework passa a ter todas as informações necessárias para recuperar e persistir objetos na base de dados.
<p>Além disso, acima foi demonstrado um exemplo de mapeamento via arquivo XML externo, através do NHibernate, porém existem outros tipos de mapeamento normalmente disponibilizados pelos frameworks ORM, sendo eles:
*Usando atributos customizados em nossas classes
*Usando Fluent API
<p>O mapeamento por XML, exemplificado na Listagem 1, é um dos mais comuns e está presente em muitos ORMs, como por exemplo, no próprio NHibernate. Um inconveniente deste mapeamento é a quantidade de XMLs gerados, além da manutenção um pouco mais trabalhosa, uma vez que você terá que fazê-la em arquivos XMLs, sem os recursos de refatoração e Intellisense nativos do Visual Studio.
<p>O outro tipo de mapeamento é através de anotações, onde nós definimos no código do modelo as características da tabela ou coluna representada por cada classe e atributo. Em .NET temos os Custom Attributes que são utilizados entre colchetes, sendo aplicados às classes e propriedades, para realização do mapeamento. 
  
~~~
     using System;
     using System.Collections.Generic;
     using System.Linq;
     using System.Text;
     using NHibernate.Mapping.Attributes;

     namespace DevMedia.Exemplo
     {
            [Class(Table = "TB_CLIENTE")]
            public class Cliente
            {
             [Id(Column = "CodCLiente")]
             public Double Codigo { get; set; }

             [Property]
             public Double Nome { get; set; }

             [Property]
             public Double CPF { get; set; }
            }
     }
~~~
  
<p>Exemplo de mapeamento com anotações com Hibernate.
  
  
  
  
  
  
  
  
  
  
  
  
![Alt ou título da imagem](URL da imagem)
