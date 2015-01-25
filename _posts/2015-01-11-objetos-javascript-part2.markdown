---
layout: post
title:  "Objetos JavaScript part2"
date:   2015-01-25 15:02:00
---

Olá mais uma vez, vamos continuar de onde paramos do post [Objetos JavaScript part1](/objetos-javascript-part1.html) se tu não leu ainda, recomendo a leitura para acompanhar esse post! Vai lá, eu espero...

Paramos em Método, e como método é bacana entender, vamos continuar nesse assunto!

##Mais sobre Método de um Objeto

{% highlight js %}
var predio = new Object();
predio.companyName = 'Amanco';
predio.height = 150;
predio.width = 80;
predio.set = function(newHeight, newWidth) {
  this.height = newHeight;
  this.width = newWidth;
};

predio.set(110, 90);

console.log(predio);
{% endhighlight %}

No exemplo acima, criamos um Objeto da forma construtora chamada predio, em seguida criamos 3 Propriedades que entre elas recebe `string` e `number`, mas a última `set` é um Método que altera a altura e largura desse prédio assim que chamada. Esse Método é chamado dessa forma `predio.set(110, 90);` que altera a altura do Objeto predio para `110` e a largura para `90`.

Perceba que podemos chamar um Método igual uma função, porém temos que citar o Objeto antes `objeto.metodo()`.

Método é ótimo para alterar valores de Propriedades, podendo fazer cálculos com seus valores, receber parâmetros de dados externos entre outras formas.

##"this"

Para o Método funcionar em qualquer Objeto, temos que usar a palavra `this`, já usamos ele nos exemplos anteriores, mas vamos falar sobre ele!

Ele indica qualquer Objeto que esteja chamando um Método

Usando o mesmo exemplo do Objeto predio acima, percebemos que foi criado um Objeto pelo construtor e depois criado um Método para ele, porém esse Método ficou exclusivo para o Objeto predio `predio.set`, caso queira usar esse mesmo Método para outro Objeto, não será possível.

Vamos separá-los.

{% highlight js %}
var set = function(newHeight, newWidth) {
  this.height = newHeight;
  this.width = newWidth;
};
var predio = new Object();
predio.companyName = 'Amanco';
predio.height = 150;
predio.width = 80;
predio.set = set;

var casa = new Object();
casa.height = 25;
casa.width = 18;
casa.set = set;

predio.set(110, 90);
casa.set(20, 15);

console.log(predio);
console.log(casa);
{% endhighlight %}

Veja que agora que estão separados, podemos usar o mesmo Método para o Objeto casa... Faça o teste e veja você mesmo! Olha que Maravilha...

Sabemos agora que não estamos presos em um único Objeto, `this` nos permite evitar mais linhas de códigos!

##Mais sobre Construtor

Já falamos sobre Construtor no post anterior [Objetos JavaScript part1](/objetos-javascript-part1.html), mas é bom lembrar.

A palavra chave `new` cria de forma construtora algo como um Array, Objeto, etc... Para criar um Objeto vazio, sem propriedades e métodos, basta escrever `var foo = new Object()` na qual foo será um Objeto vazio, esse construtor já está definido na linguagem JavaScript.

Depois que criado o Objeto vazio, você terá que criar um por um as Propriedades e Métodos.

##Faça seus Construtores

Você leu que depois que criado um Objeto vazio, terá que adicionar um por um as Propriedades e Métodos de cada Objeto, mas isso é muito chato... Podemos resolver isso criando nossos próprios construtores, e assim que cada Objeto for criados, já teremos algum conteúdo. Exemplo:

{% highlight js %}
function Carro(marca, cor, ano) {
  this.marca = marca;
  this.cor = cor;
  this.ano = ano;
  this.mudaCor = function(novaCor) {
    this.cor = novaCor;
  };
}

var modelo1 = new Carro('fiat', 'vermelho', 2015);
var modelo2 = new Carro('ford', 'preto', 2014);
var modelo3 = new Carro('volkswagen', 'azul', 2015);

modelo3.mudaCor('branco');

console.log(modelo3);
{% endhighlight %}

Acima, criamos um Construtor chamado __Carro__ que toma como parâmetro __marca__, __cor__ e __ano__, esse Construtor recebe 3 Propriedades e 1 Método que toma __novaCor__ como parâmetro para alterar a Propriedade __cor__ para __novaCor__.

Perceba que ficou muito mais fácil criar um Objeto, com apenas uma linha, já criamos um Objeto. Perceba também que todos os Objetos que forem criados usando esse nosso Construtor, terá o Método __mudaCor__ já que está definido antes de criar um Objeto e não é preciso definir todas as propriedades com parâmetros. 

Caso queira adicionar um outro Método para um Objeto específico, você poderá sim, sem problemas dessa forma:

{% highlight js %}
modelo3.novoMetodo = function() {
  this.ano = 2020;
}
{% endhighlight %}

Todos os Objetos do exemplo são bem parecidos, porém só o Objeto modelo3 terá um Método a mais. Dúvidas?

Resumindo ainda mais, quero dizer que sempre que encontrar um padrão nos Objetos, você poderá construir seu próprio Construtor e facilitar seu desenvolvimento e sua vida.

Por hoje paro por aqui... Com certeza existe muito mais coisas para falar! Mas acho que para uma base, já é o bastante e estou a continuar meus estudos sobre JS e espero que em breve eu fale mais nos próximos posts.

Caso tenha críticas e sugestões, fique a vontade aí nos comentários!

Até breve...









