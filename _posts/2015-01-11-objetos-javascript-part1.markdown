---
layout: post
title:  "Objetos JavaScript part1"
date:   2015-01-11 23:11:00
---

Estou (Estão) me cobrando para postar algo mais no blog, até tenho uns 3 drafts, porém tenho um sério problema de me cobrar demais, e tudo que faço, acho que daria para ficar melhor e acabo nem postando nada... Triste!

Sem enrolar, vamos começar o ano com objetivos e definições.

Como já deve ter visto, vou falar do que entendi sobre Objetos no JavaScript, talvez eu quebre para mais um post caso fique grande.

E se eu falar alguma besteira aqui, por toda gentileza, comente no post para que eu possa corrigir, discutir, persistir... Ou quebrar o pau, mas ó! Sou da paz :)

##O que é Objeto?

É possível representar algo do mundo virtual e real com um Objeto (carros, animais, conta de banco e mais zilhões de coisas), e dentro é possível armazenar as informações para caracterizar aquele Objeto, seja ele qual for.

Exemplo:

{% highlight js %}
var igor = {
  fistName: 'Igor',
  lastName: 'APA',
  height: 1.80,
  weight: '86kg',
  age: 26
}
{% endhighlight %} 

Veja acima que criei um Objeto com meu nome, mas não necessariamente ele precise de nome, mas para frente iremos ver como adicionar Objetos dentro de Objeto e Objetos dentro de Arrays e assim achá-los por índice e não por nome específico, enfim...

Diferentes de Array que usa colchete `[]`, Objeto usa chave `{}`. Dentro dessa chave temos as informações que são conhecidas como Propriedades.

MAAAASSSSSSSSSSSSSSSS, com `{}` é a forma de criar Objetos chamada de __notação literal de objeto__

##Propriedades o que são?

Propriedades são as características do nosso Objeto, uma Propriedade tem nome `:` valor e uma vírgula `,` no final, porém sempre a última Propriedade não termina com vírgula, como nosso Objeto __igor__. E se o Objeto obter apenas uma única Propriedade, não será preciso a utilização dá vírgula.

{% highlight js %}
fistName: 'Igor',
age: 26
{% endhighlight %} 

Entenda melhor...

Nesse pequeno trecho acima temos duas Propriedades. A primeira se chama `fistName` e seu valor é `'Igor'` uma `string`, a segunda Propriedade se chama `age` e seu valor é `26` um `number`. Simples não?

##Como acesso as informações de um Objeto?

Para acessar é fácil (espero que você já tenho alguma base em JS). Vamos criar um Objeto chamado cat, definir algumas propriedades que caracteriza um gato normal, e acessar apenas duas Propriedades desse Objeto imprimindo no `console.log()`. Vamos lá...

{% highlight js %}
var cat = {
  specie: 'Persa',
  color: 'gray',
  age: 2
}

console.log('Meu gato é ' + cat.specie + ' e tem ' + cat.age + ' anos!');
{% endhighlight %}

Nosso Objeto acima tem 3 Propriedades com seus respectivos valores, e um `console.log` que imprime uma string já colhendo duas informações desse Objeto, no caso, o valor da Propriedade `specie` que é `Persa` e o valor da Propriedade `age` que é `2`. O console irá devolver essa string:

`Meu gato é Persa e tem 2 anos!`

Muito fácil né? 

Você percebeu que usamos ponto `.` para atingir a Propriedade de um Objeto? Assim `object.property`, essa forma é chamada de __notação de ponto__ e existe mais outra forma que podemos acessar as Propriedades chamada de __notação de colchetes__ que fica dessa forma:

{% highlight js %}
console.log('Meu gato é ' + cat["specie"] + ' e tem ' + cat["age"] + ' anos!');
{% endhighlight %}

Viu? Para acessar a Propriedade nesse caso, não precisa do ponto `.`, apenas do `[ ]` com `" "` apesar de preferir usar a notação de ponto. Porém existe algumas situações que é melhor usar de colchetes, irei falar disso mais para frente, talvez em outro post.

##Objeto com Construtor

Mas acima, informei que a forma da criação do Objeto que fizemos foi em __notação literal__ usando `{ }`, agora vamos falar da forma __construtor__ que usa a definição `new` e não usa `{ }`. Após o operador `new` vem o nome da função construtora que inicializa o Objeto.

A palavra chave `new` seguida por `Object()` é usada para criar um objeto vazio. Veja um exemplo abaixo!

{% highlight js %}
var obj = new Object();
{% endhighlight %}

Perceba que mesmo vazio, é simples criar um Objeto com construtor... Caso queira imprimir no console, ele não irá mostrar nada. Tente!

{% highlight js %}
console.log(obj);
{% endhighlight %}

Nada será impresso, mas para saber se realmente é um objeto podemos testar com o `typeof` dessa forma.

{% highlight js %}
console.log(typeof obj);
{% endhighlight %}

Com toda certeza será impresso `"object"` no console. Agora vamos preencher com Propriedades esse Objeto construtor.

{% highlight js %}
var obj = new Object();
obj.size = 40;
obj.color = "blue";
obj.name = 'obj';
{% endhighlight %}

Diferente da forma notação literal, não usamos vírgula `,` dois pontos `:` chave `{ }`... Mas a forma de criar a propriedade se parece muito com a forma de declarar uma variável com `=` para receber o valor e `;` no final para finalizar a declaração. Igor, posso pensar Propriedade como uma variável vinculada ao Objeto? Claro que pode!

Para criação das Propriedades do Objeto construtor usamos a notação de ponto, mas podemos usar também a notação de colchetes.

{% highlight js %}
var obj = new Object();
obj['algo'] = 'alguma coisa';
{% endhighlight %}

Simples demais? Eu sei!

##Método de um Objeto

Tu sabe o que é uma função? Método é como uma função acoplada ao Objeto ou da mesma forma quando um Objeto invoca uma função. Vejamos!

{% highlight js %}
function liquidificador(status) {
  obj.velocidade = 100;
  obj.ligado = status;
}

var obj = new Object();
obj.velocidade = 50;
obj.ligado = true;

liquidificador(false);
{% endhighlight %}

Viu? Acima temos uma função `liquidificador` que no momento não é um Método, um Objeto construtor `obj` e a chamada da função que passa o parâmetro `false`. O Objeto já tem duas Propriedades até a função ser chamada com o parâmetro, após isso o Objeto terá suas duas Propriedades alteradas, `velocidade` que era `50` passou a ser `100` e `ligado` que era `true` passou a ser `false`.

Vamos para uma outra situação...

{% highlight js %}

function liquidificador(status) {
  this.velocidade = 150;
  this.ligado = status;
}

var arno = new Object();
arno.velocidade = 100;
arno.ligado = false;
arno.liquidificador = liquidificador;

arno.liquidificador(true);
console.log(arno);

{% endhighlight %}

Agora aquela mesma função que não era um Método passou a ser um... Vamos verificar!

Criamos um Objeto da forma construtora chamado `arno` e criamos 3 Propriedades, `velocidade` que recebe `100`, `ligado` que recebe `false` e `liquidificador` que recebe a função `liquidificador` criado anteriormente. Essa última Propriedade é um Método que passa `status` como parâmetro e altera (assim que chamada) as duas primeiras Propriedades citadas, `velocidade` para `150` e `ligado` para `true`.

Temos o trecho `arno.liquidificador(true);` que chama o Método, e só a partir daí que as Propriedades serão alteradas, depois no console é impresso o resultado.

Acho podemos parar por aqui por enquanto para não ficar muito cansativo. Em breve teremos a segunda parte!

Aquele Abraço o/







