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
* Temos que escrever todo o SQL de nossa aplicação manualmente, tornando o desenvolvimento do projeto muito mais improdutivo.
* Temos que nos preocupar em não usar nenhum código SQL específico de determinado SGDB para não corrermos o risco de ficarmos preso ao mesmo.
* Temos mais classes para gerenciar e dar manutenção.
<p>Além disso, o modelo de dados relacional possui algumas limitações em comparação com o modelo de objetos (Nota do DevMan 1), como por exemplo:
* Não possui herança
* Não possui polimorfismo
* Não permite relações N para N entre duas entidades (tabelas)
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
  
~~~
1  <?xml version="1.0" encoding="utf-8" ?>
2     <hibernate-mapping xmlns="urn:nhibernate-mapping-2.2"
3         namespace="DevMedia.Exemplo " assembly="DevMedia.Exemplo">
4       <class name="DevMedia.Exemplo.Cliente,
5         DevMedia.Exemplo" table="TB_CLIENTE">
6         <id name="Codigo" column="CodCliente"/>
7         <property name="Nome"/>
8         <property name="CPF"/>
9       </class>
10     </hibernate-mapping>
~~~
  
<p>Pode-se observar um exemplo de mapeamento através do framework NHibernate. Veja que na linha 2 é definido o namespace e o assembly onde está a classe e na linha 3 é indicado o nome da mesma seguido do nome de sua respectiva tabela no banco de dados. Na linha 4 tem-se uma tag Id que indica que o campo Codigo da classe é o identificador do objeto, mapeando o mesmo para a coluna CodCliente que é a chave primária da tabela. Por fim, nas linhas 5 e 6 temos o mapeamento das propriedades da classe Cliente. Vale ressaltar que nestes casos não foi informado o nome da coluna no banco de dados, pois as colunas possuem o mesmo nome das propriedades do objeto Cliente.
<p>Com todo este mapeamento realizado, o framework passa a ter todas as informações necessárias para recuperar e persistir objetos na base de dados.
<p>Além disso, acima foi demonstrado um exemplo de mapeamento via arquivo XML externo, através do NHibernate, porém existem outros tipos de mapeamento normalmente disponibilizados pelos frameworks ORM, sendo eles:
* Usando atributos customizados em nossas classes
* Usando Fluent API
<p>O mapeamento por XML, exemplificado na Listagem 1, é um dos mais comuns e está presente em muitos ORMs, como por exemplo, no próprio NHibernate. Um inconveniente deste mapeamento é a quantidade de XMLs gerados, além da manutenção um pouco mais trabalhosa, uma vez que você terá que fazê-la em arquivos XMLs, sem os recursos de refatoração e Intellisense nativos do Visual Studio.
<p>O outro tipo de mapeamento é através de anotações, onde nós definimos no código do modelo as características da tabela ou coluna representada por cada classe e atributo. Em .NET temos os Custom Attributes que são utilizados entre colchetes, sendo aplicados às classes e propriedades, para realização do mapeamento. 
  
~~~
1     using System;
2     using System.Collections.Generic;
3     using System.Linq;
4     using System.Text;
5    using NHibernate.Mapping.Attributes;
6
7     namespace DevMedia.Exemplo
8    {
9            [Class(Table = "TB_CLIENTE")]
10            public class Cliente
11            {
12             [Id(Column = "CodCLiente")]
13             public Double Codigo { get; set; }
14
15             [Property]
16             public Double Nome { get; set; }
17
18             [Property]
19            public Double CPF { get; set; }
20            }
21     }
~~~
  
<p>Exemplo de mapeamento com anotações com Hibernate.
<p>Na linha 9 tem-se a definição do atributo Class com o parâmetro Table indicando o nome da tabela onde esta classe está mapeada, enquanto que na linha 12 tem-se a indicação de que a propriedade Codigo é o identificador do objeto e está mapeada para a coluna CodCliente da base de dados. Por fim tem-se o mapeamento das outras propriedades nas linhas 15 e 18.
<p>O que muitos consideram como um inconveniente das anotações é que a classe que usa muitos Custom Attributes fica poluída e, caso o framework ORM fosse trocado,tería que alterar todas as as classes para que usassem os atributos do respectivo framework.
<p>Como alternativa ao mapeamento, tem ainda normalmente o uso de uma Fluent API, que trata-se de uma API de mapeamento que implementa o pattern Fluent Interface (Nota do DevMan 2).

~~~
01     using System;
02     using System.Collections.Generic;
03     using System.Linq;
04     using System.Text;
05     using FluentNHibernate.Mapping;
06     using DevMedia.Exemplo.ExemploHeranca;
07
08     namespace DevMedia.Exemplo
09     {
10            public class ClienetMap:ClassMap<Cliente>
11            {
12             public ClienetMap() {
13                 Id(x => x.Codigo).Column("CodCliente");
14                 Map(x => x.Nome);
15                 Map(x => x.CPF);
16
17                 Table("TB_CLIENTE");
18             }
19           }
20     }
~~~
  
<p>Exemplo de mapeamento com Fluent API em NHibernate.
<p>Pode-se observar o mapeamento com o FluentNHibernate, que é uma iniciativa da comunidade que visa permitir o mapeamento usando uma Fluent API para o NHibernate. Veja que nossa classe de mapeamento herda de uma classe base de mapeamento do FluentNHibernate, chamada ClassMap (linha 10), indicando no tipo genérico a classe que queremos mapear. Esta classe é a responsável por determinar o mapeamento de um objeto do sistema para a base de dados.Na linha 13 temos um método que nos permite indicar a propriedade identificadora do objeto e a coluna para onde a mesma está mapeada. Nas linhas 14 e 15 nós temos o mapeamento das propriedades Nome e CPF, não sendo necessária a definição da coluna da base de dados, pois esta possui o mesmo nome das propriedades do objeto. Por fim, na linha 17 temos a definição da tabela onde os dados da classe Cliente serão persistidos.
<p>Para muitos o uso de Fluent Interface é o melhor dos dois mundos, onde pode-se realizar todo o mapeamento em arquivos separados utilizando o próprio C#, com todos os recursos de refatoração e intellisense disponíveis e sem poluir nossos objetos.
##Persistência de Dados
<p>Agora que já compreendemos como as tabelas e colunas são mapeadas para classes e propriedades, como é feita a persistência destes dados através de frameworks ORM?
<p>Cada ORM tem seu estilo de código para a persistência dos dados, mas em geral eles possuem o mesmo caminho: interpretar o comando que você solicitou, verificar qual função ou conjunto de funções SQL são necessárias para executar o comando solicitado, efetuar a leitura do mapeamento da classe que você está usando, gerar o SQL necessário, abrir uma conexão com o SGDB, executar o SQL e retornar o resultado.
<p>A seguir terá dois exemplos bem diferentes, um em ruby com o ActiveRecord, um ORM muito popular dentro do framework Rails, e um exemplo em C# com o Entity Framework.
  
~~~
1  pessoa = Pessoa.new
2  pessoa.nome = "Priscila Mayumi Sato"
3  pessoa.save
~~~

<p>Exemplo de comando para salvar com ActiveRecord.

~~~
1  using (CFcontext db = new CFcontext())
2  {
3    Pessoa pessoa = new Pessoa();
4    pessoa.Nome = "Priscila Mayumi Sato";
5    db.Pessoas.Add(pessoa);
6    db.SaveChanges();
7  }
~~~
  
<p>Exemplo de comando para salvar com Entity Framework.
<p>Pod-se notar diferentes formas de persistir os dados. Na Listagem temos o exemplo com ActiveRecord: que podemos ver que foi instanciado um objeto do tipo Pessoa, foi atribuido um valor para o atributo Nome e depois o próprio objeto pessoa se persistiu no banco de dados com o método save.
<p>Na Listagem em C# com Entity Framework, temos a declaração de um contexto de persistência de dados (objeto db), instanciando um objeto do tipo Pessoa, atribuindo um valor a propriedade Nome e posteriormente adicionando este objeto pessoa a um container (Pessoas) de seu tipo, e após isso o objeto foi persistido usando o método SaveChanges do contexto de persistência.
<p>Os métodos Save e SaveChanges possuem o mesmo objetivo: persistir mudanças de objetos da memória para o banco de dados, porém foram disponibilizados de formas diferentes, uma sendo chamada diretamente no objeto mapeado e o outro solicitando que o objeto a ser persistido seja adicionado a um container.
<p>No momento em que estes métodos foram acionados, o framework ORM verificou o mapeamento das classes para identificar qual o nome da tabela responsável e das respectivas colunas do banco de dados e gerou um SQL dinamicamente, semelhante código abaixo, e executou o mesmo no SGDB em questão.
  
~~~
1  INSERT
2  INTO TB_PESSOA(NOME) VALUES ("Priscila Mayumi Sato";);
~~~
  
##Formas de acesso aos dados
<p>Os frameworks ORM nos fornecem uma série de maneiras para acessar os dados persistidos no nosso SGDB, dentre estas formas pode-se destacar:

* OCL – Object Constraint Language – São consultas baseadas em critérios definidos em objetos, como por exemplo, os objetos Criteria do NHibernate.
* SQL – São consultas baseadas em um SQL tradicional. Neste caso normalmente é passado o código SQL para o framework e o mesmo retorna uma lista de objetos com o resultado da consulta.
* Linguagens específicas – Consultas baseadas em linguagens específicas do framework ORM em questão, ou seja, ao invés de usar SQL utilizamos uma linguagem específica que o próprio framework suporta, como por exemplo, o Linq no caso do Entity Framework.
<p>Além disso, cada framework possui características e recursos adicionais, como por exemplo, o NHibernate que possui um recurso chamado Named Queries que nos permite armazenar consultas SQL (ou também HQLs) em arquivos xml separados e depois mapeie os mesmos, como mapeou suas tabelas, podendo assim usá-las a qualquer momento no seu código.  

~~~
01     using (CFcontext db = new CFcontext())
02     {
03           string nativeSQLQuery = "SELECT count(*) FROM dbo.Edicoes"
04           var queryResult = db.ExecuteStoreQuery<int>(nativeSQLQuery);
05           int totalEdicoes = queryResult.FirstOrDefault();
06     }
~~~
  
<p>Exemplo de uso de querys SQL no Entity Framework.
<p>Não é uma regra mas não é incomum encontrar uma linguagem própria de consulta nos frameworks ORM (Exemplo HQL / Linq). A mecânica é que os comandos na linguagem específica passem por um interpretador da framework e depois sejam traduzidos para uma query SQL para ser executada no SGDB.
<p>Normalmente essas linguagens de consulta são parecidas com a linguagem SQL. Exemplos de linguagens de consulta são o LINQ do .NET, o HQL do NHibernate, a DQL (Doctrine Query Language) do Doctrine (framework de ORM para linguagem PHP), e a LIQUidFORM, uma linguagem que se inspirou no LINQ só que para rodar no JPA (Java Persistence API) da plataforma Java.
<p>A mecânica é semelhante ao passar um comando do framework para que ele interprete e crie os comandos SQL, a diferença é a flexibilidade, pois com uma linguagem própria de consultas, temos mais liberdade para trabalhar com os dados. Além disso, você não precisa se preocupar com o uso de comandos específicos de cada SGDB, pois a própria framework já trata isso.
  
  
  
  
  
![Alt ou título da imagem](URL da imagem)
