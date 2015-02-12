---
layout: post
title:  "Prototype"
date:   2015-02-02 15:02:00
---

Venho estudando bastante sobre JavaScript avançado, e tropecei em Prototype! Considero muito importante entender o funcionamento dele, ao mesmo tempo que parece fácil o entendimento, é meio confuso (pelo menos para mim) aplicar o seu funcionamento. 

Vou tentar ser claro e simples com o que entendi! 

##O que é Prototype?

Antes de explicar o que é, tenho que deixar claro que JavaScript não trabalha com Classe, e sim Construtor! Caso você veja sendo citado Classe em JavaScript em algum lugar da Web, saiba que a pessoa está querendo dizer Construtor... Continuando!

Prototype é forma de conseguir adicionar e acessar Propriedades e Métodos de um Objeto já existente ou que será criado. É ótimo para criar vários Objetos onde você terá um grande controle sobre eles.

A grande jogada de Prototype é poder incluir Métodos de execução a um Objeto, entrando no famoso POO (programação orientada a objetos).

Vamos ver um pouco de código.

{% highlight js %}
function Carro(){
  this.rodas = 4;
}
Carro.prototype.andar = function(algo) {
  return algo;
}
var honda = new Carro();  
{% endhighlight %} 

No exemplo acima, foi criado um Construtor chamado `Carro` que tem a Propriedade `rodas` com o valor `4`, em seguida foi adicionado ao Prototype um o Método `andar` que toma `algo` como parâmetro e o retorna, na linha seguinte criamos um Objeto chamado `honda` que recebe o Construtor `Carro`.

Quando você chamar o Objeto `honda` apenas:

{% highlight js %}
console.log(honda);
{% endhighlight %} 

Será mostrado apenas a Propriedade `rodas` e não `andar`. Porém, se você tentar chamar `andar`, esse comando irá funcionar perfeitamente. Tente!

{% highlight js %}
console.log(honda.rodas, honda.andar(true));
{% endhighlight %} 

Mas Igor, ao invés de colocar o Método `andar` via Prototype, não posso adicioná-lo direto no Construtor? Numa situação pequena como essa, até que pode, mas numa escala maior é melhor via Prototype.

Vamos para um outro exemplo para entender melhor.

{% highlight js %}
function Cachorro(nome, raca, idade) {
  this.nome = nome;
  this.raca = racal;
  this.idade = idade;
}

var bob = new Cachorro('Bob', 'Labrador', '1 ano');
var rex = new Cachorro('Rex', 'Pastor Alemão', '4 anos');

Cachorro.prototype.latir = function() {
  console.log('Som de latido assustador');
}

bob.latir(); // return 'Som de latido assustador'
rex.latir(); // return 'Som de latido assustador'
{% endhighlight %} 

Entendeu o que aconteceu aí em cima? Existe um Construtor chamado Cachorro e dois Objetos criados em base do Construtor, `bob` e `rex`. Perceba que colocamos várias Propriedades, mas para nosso exemplo não iremos usá-los. Em seguida adicionamos o Método `latir` ao Prototype.

O que quero dizer com todo esse exemplo é que podemos criar mais de 10 mil Objetos com nomes, raças e idades diferentes (que no caso é único para cada cachorro), e o Método `latir` irá funcionar para todos eles e não irá ter várias repetições do mesmo Método em cada Objeto, já que 1 Prototype será acessado por esses 10 mil cachorros!

Se mudar o Prototype de Cachorro, todos Objetos terão essa alteração.

Fui claro?

##Herança ou Cascata?

Alguns falam que Prototype tem o efeito de Herança, outros falam que é efeito Cascata, eu não sei qual é a definição certa, mas acredito e irei seguir a de Cascata.

Na Programação Orientada a Objetos, o efeito Cascata do Prototype permite que você use Métodos e Propriedades de outro Construtor. Podemos pensar que temos um Construtor Animal, que recebe Propriedades que define qualquer característica de um animal, e teremos outro Construtor Macaco que tem dentro dele as características de uma macaco comum, mas que ao mesmo tempo "herda" características do Construtor Animal.

Vamos entender melhor:

{% highlight js %}
function Animal(nome, especie, numPernas) {
  this.nome = nome || 'algum nome';
  this.especie = especie || 'alguma espécie';
  this.numPernas = numPernas || 1000;
}

Animal.prototype.fala = function() {
  console.log('Tenho ' + this.numPernas + ' pernas');
};

function Macaco(especie, numPernas) {
  this.especie = especie;
  this.numPernas = numPernas;
}

Macaco.prototype = new Animal();

var mico = new Macaco('Sagui', 2);

mico.fala();

{% endhighlight %} 


No exemplo acima, criamos dois Construtores onde Macaco herda Propriedades de Animal, as Propriedades de Macaco que forem iguais a de Animal, serão sobrescritas e as que tiverem em Animal e não tiverem em Macaco, serão acessadas via Prototype.

Por exemplo, se eu quiser acessar o número de pernas do `mico`, é só passar `mico.numPernas` que irá me retornar `2`, já que definimos na criação do Objeto `mico` usando o Construtor Macaco, mas se eu quiser usar o Método `falar` que foi atribuído ao Construtor Animal via Prototype, eu também consigo, já que "herdamos" tudo de Animal dessa forma `Macaco.prototype = new Animal();`. Então passamos `mico.falar()` que irá retornar uma string `"Tenho 2 patas"`.

É possível ir criando uma cadeia de Construtores onde cada um vai herdando do outro, essa cadeia pode ter apenas alguns Construtores como vários também, o efeito num gráfico fica igual a uma cascata, daí o nome!

Se o JavaScript não encontrar uma Propriedade ou Método no Construtor atual, ele sobe a cadeia de Prototype até encontrar, ele vai subindo até chegar no topo que é o `Object.prototype` e se mesmo assim não for encontrado, será retornado `undefined`.

Por padrão do JavaScript, todo Construtor criado, tem uma "herança" do Object.prototype, então todos Objetos que forem criados usando qualquer Construtor terá por exemplo o Método `hasOwnProperty` que vem por padrão do Object.prototype.

Bom, chegamos ao fim desse post! Espero que tenha entendido e qualquer dúvida, críticas ou sugestões, será bem vindo aqui nos comentários abaixo.











<!-- Lembre-se, herança nos permite ver e usar propriedades e métodos de outra classe. -->