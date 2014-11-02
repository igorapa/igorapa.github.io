---
layout: post
title:  "Começando com JavaScript"
date:   2014-11-01 20:37:00

---

> Qual o comprimento do seu nome?

`"igor apa".length` o retorno deve ser 8 (contando com o espaço).

> Fazendo contas matemáticas

`2+2`<br>
`3*8`
`10-6`
`100/15`

 
 
 ```
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```


{% highlight ruby %}
def show
  puts "Outputting a very lo-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-ong lo-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-ong line"
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}






{% highlight js %}
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}

var friends = {};
friends.bill = {
  firstName: "Bill",
  lastName: "Gates",
  number: "(206) 555-5555",
  address: ['One Microsoft Way','Redmond','WA','98052']
};
friends.steve = {
  firstName: "Steve",
  lastName: "Jobs",
  number: "(408) 555-5555",
  address: ['1 Infinite Loop','Cupertino','CA','95014']
};

var list = function(obj) {
  for(var prop in obj) {
    console.log(prop);
  }
};

var search = function(name) {
  for(var prop in friends) {
    if(friends[prop].firstName === name) {
      console.log(friends[prop]);
      return friends[prop];
    }
  }
};

list(friends);
search("Steve");
{% endhighlight %}



