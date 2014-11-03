---
layout: post
title:  "Começando com JavaScript"
date:   2014-11-01 20:37:00

---

### Qual o comprimento do seu nome?

`'igor apa'.length` o retorno deve ser 8 (contando com o espaço).

### Fazendo contas matemáticas

fazendo os cálculos abaixo no console do browser, será retornado o resultado de cada conta feita.

{% highlight js %}
// Forma de comentar no código para facilitar o entendimento na leitura do código
// O browser irá ignorar esse trecho.
2+2
3*8
10-6
100/15
{% endhighlight %}

Alguns exemplos: <br>
`50/10` é igual a 5 <br>
`'igor'.length * 10` é igual a 40 <br>
`10/(10*10)` é igual a 10 <br>
`()` controle da ordem das operações

### O Resto em Matemática

Esse símbolo `%` é chamado de __resto__, usado ente dois números o computador irá dividir o primeiro pelo segundo e retorna o __resto__ da divisão.

Exemplos: <br>
`14 % 6` é igual a 2 <br>
`100 % 23` é igual a 1 <br>
`50 % 5` é igual a 0

É ótimo ter o poder de calcular o resto, para que possamos testar a divisibilidade, se não houver resto então o resultado será `0`.


### Retornando True ou False

{% highlight js %}
	confirm('Escolha entre as duas opções');
{% endhighlight %}

Clicando em `OK` o retorno dessa ação será `true` e em `Cancel` o retorno será `false`. Essas duas ações são válidas quando queremos dar partida para um trecho do código usando a interação dos usuários.

### Recebendo entradas

{% highlight js %}
prompt("Quantos anos você tem?");
// ou
prompt("Qual sua cor favorita?");
// ou
prompt("Qual sua profissão?");
// entre inúmeras opções
{% endhighlight %}

O que for escrito no campo de entrada, será retornado como `string` mesmo sendo passado um número `5`, colocando esse valor, a entrada ficará assim `'5'`, a aspas simples ou duplas define o tipo para `string`.

### Tipo de Dados

São elas `strings`, `numbers` e `booleanos`. 

Números são apenas números quando estão sem aspas, como dito no tópico anterior, se o número conter aspas `'100'` já é interpretado como `string`, então se for passado dessa forma `100` ou dessa `100.9878` é interpretado como `number`.

Strings são todas sequências de caracteres com letras, números, espaços e caracteres especiais `'JavaScript'` `'56.899'` `'Gosta de programar?'`. Reforçando que número passa ser uma string estando entre aspas.

Booleanos são `true` ou `false`, ótimo para fazer comparações, tipo `100 > 10` é `true` ou `100 < 10` é `false` ou melhor ainda `'igor apa.length' > 5` é `true`.

Então:<br>
__String__ `'Seu nome'` `'98.77'`<br>
__Number__ `33.33` `20`<br>
__Bolleano__ `true` `false` `10 > 5`<br>

### Console.log

Para que você possa visualizar no console do browser algum trecho do seu código entrando em ação, você deve inserir no meio do seu código, ou no fluxo que aquele trecho será rodado o `console.log('aqui virá sua variável, ou um objeto ou uma condição, entre outras formas')`.

Com `console.log()` exibimos no console o que quer que colocamos entre parênteses.

### Comparando

`>` Maior que <br>
`<` Menor que <br>
`<=` Menor ou igual a <br>
`>=` Maior ou igual a <br>
`===` Igual a <br>
`!==` Diferente de

Quando se faz comparação o resultado é um bolleano retornando `true` ou `false` para aquela condição.

`100 === 10*10` retorna `true` <br>
`'js'.length > 1` retorna `true` <br>
`10 === '10'` retorna `false`

### Decidindo com Condicionais

Com o esquema de bolleano podemos fazer validações para decidir por onde seguir, referente ao valor ou evento que ocorra.

{% highlight js %}
var name = prompt('Qual seu nome?');

if (name.length > 10) {
    console.log("Seu nome é meio grande");
} else {
    console.log('Seu nome é pequeno');
}
{% endhighlight %}

Existe também...

{% highlight js %}
var name = prompt('Qual seu nome?');

if (name.length > 10) {
    console.log("Seu nome é meio grande");
} else if (name.length === 4) {
    console.log('Seu nome é do mesmo tamanho que o meu');
} else {
    console.log('Seu nome é pequeno');
}
{% endhighlight %}

Com o `prompt`, perguntamos ao usuário o seu nome guardando na váriavel `name`, e com o `if` é passado a condição "se" o nome inserido for `>` maior que 10, o console irá mostrar a mensagem de que o nome dele é meio grande e `else` é caso contrário dessa condição não seja `true` no caso seja `false` e exibir no console que o nome é meio pequeno.

Não precisamos só exibir algo quando uma condição for `true` ou `false` podemos dar partida para outro trecho de código, chamando outra função, ou criando um objeto, ou pedindo outro trecho de um jogo... O que quero dizer que vai do seu limite até onde vc quer com aquela condição tendo várias alternativas. :)

### Substrings

Caso você não queira visualizar toda string, apenas uma parte dela, o `substring` é uma ótima maneira de fazer isso.

`'aqui temos uma grande frase'.substring(x, y)` onde `x` é onde começa a cortar e `y` é onde termina o corte da string original.

Digamos que seja bacana exibir apenas esse trecho `aqui temos` da string acima, então a condição será dessa forma:

`'aqui temos uma grande frase'.substring(0, 10);` o retorno será `'aqui temos'` como desejado.

O `x` está sempre uma posição anterior da letra que vc quer escolher, e o `y` é a posição exata na qual vc deseja atingir, exemplo usando a mesma string anterior:

`'aqui temos uma grande frase'` dessa string, quero visualizar apenas `'s uma gra'` o `s` está na posição `10` então `x` será `9` (lembra? Sempre uma posição anterior da qual desejar) e `a` está na posição `18` então `y` será `18` (lembra? Será a posição exata na qual desejar atingir).

Então:

`'aqui temos uma grande frase'.substring(9, 18)` o retorno será a string que optamos para esse teste que é `'s uma gra'`.

Outro exemplo rápido é `'oi como vai você?'` se eu quiser pegar apenas o `'oi'` terei que fazer um x e y dessa forma `(0,2)`. Meio confuso, não?

Não sei se consegui ser claro, mas caso não tenha entendido pois sei que é meio confuso, deixe sua dúvida no comentário abaixo!

### Variáveis

Depois de entender um pouco de tudo, como podemos __salvar__ os números, strings, bolleanos para reutilizar em algum momento?

É agora que entra as Variáveis, definindo com um nome simples e de preferência com algo que tenha sentido com aquilo que estiver recebendo. Se for receber um nome poderia colocar a variável como `var name` ou `userName`.

Depois que a variável receber algum valor, podemos referenciar aquele valor chamando apenas a variável.

Exemplos: <br>
`var name = 'igor apa';` <br>
`var age = 25;` <br>
`var js = true;` <br>

`console.log(name)` o retorno no console será `'igor apa'`. Percebeu que apenas chamando a variável conseguimos mostrar o que existe nela?

Sempre que você digita o nome da variável, está pedindo para o computador para trocar o nome da vairável pelo valor da variável.

Exemplos: <br>
`var name = 'igor apa';` <br>
`name.substring(0, 4)` o retorno será `'igor'`

Para mudar o valor de uma variável é muito fácil, basta pegar uma variável que já exista e troque o valor dela.

Exemplo: <br>
`var idade = 25;` <br>
`console.log(idade);` será retornado o número 25; <br>
`var idade = 26;` <br>
`console.log(idade);` será retornado o número 26;

Perceba que usei a mesma variável, a última rescreveu a primeira.



