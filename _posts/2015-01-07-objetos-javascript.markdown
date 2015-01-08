---
layout: post
title:  "Objetos JavaScript"
date:   2015-01-07 20:37:00
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















