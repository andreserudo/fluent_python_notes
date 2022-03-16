# The Python Data Model

O primeiro ponto é identificar como é possível criar classes sem implementações de métodos somente nomeando ele como uma collections.

`Card = collections.namedtuple('Card', ['rank', 'suit'])`

No exemplo de classe no arquivo `cards.py` podemos ver algumas funcionalidades muito bacanas. Definimos uma classe e atribuímos em seu construtor um atributo interno self._cards que recebe a implementação de uma classe. O fato de ele ser uma atribuição de um vetor faz com que possamos trabalhar com o operator len().

Essa classe reforça a importância de trabalharmos com métodos especiais do python. Utilizar o __len__ e __getitem__ nos permite desvincular a tratativa desses itens para que a classe possa trabalhar ele de acordo com a tratativa nativa de suas operações.
Exemplo: tente remover esses dois métodos e veja se ainda é possivel realizar o len() ou chamar um card por uma posição.

Ter implementado o médoto __getitem__ também permite que funções nativas de iterações sejam posiveis tais como:

`for card in deck:
    print(card)`


No exempĺo no arquivo `vector.py` temos mais alguns métodos especiais criados. O método __repr__ faz uma representação em string de um objeto. Experimente comentar esse trecho do código e veja que o resultado vai ser algo do tipo: `<__main__.Vector object at 0x7f96a7759160>`
Vimos também os métodos aritméticos __add__ e __mul__ que criam e retornam uma nova instância da classe Vector e não modificam nenhum operando. Esse é um excelente padrão para nossas classes já que queremos com esses métodos criar novas classes e não alterar os operandos.
Para determinar que um valor é verdadeiro ou falso, podemos aplicar o método bool(x) que retorna True ou False. Por default, instâncias de classes definidas por usuários são consideradas verdadeiro, a não ser que tenham ou o método __bool__ ou o método __len__ implementados. Basicamente, bool(x) chama x.__bool__() e usa seu resultado. Se __bool__ não foi implementado, Python tenta invocar x.__len__() e se retornar zero, bool retorna False.