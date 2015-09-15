---
title:  5 features do SASS
date:   2015-09-15 10:18:00
description: Aprendendo um pouco do SASS
---

### Váriaveis

Variáveis são um lugar onde guardam-se informações que serão utilizadas muitas vezes, e no SASS essas informações são qualquer valor CSS. Com as variáveis, podemos deixar de lado a preocupação de decorar valores hexadecimais. A variável é declarada com $ e o nome da variável.

{% highlight ruby %}
$buttoncolor: #c3c3c3;

button {
  background: $buttoncolor;
}
{% endhighlight %}

### Nesting

O HTML possui uma hierarquia visual entre seus elementos; no CSS porém, não existe. O SASS possibilita uma hierarquia que facilita e organiza a leitura do CSS.

{% highlight ruby %}
div {
  width: 300px;
  heigth: 300px;

  h2 {
   padding: 6px 12px;
  }

  p {
   color: #000;
  }

}
{% endhighlight %}

### Import

Particionar o CSS é uma ótima maneira  de organizar e facilitar o código. O SASS conta com uma função, @import, onde pode-se escrever um CSS de uma parte fixa da página, como o header ou footer, e importar para o CSS principal da aplicação. Assim, caso haja a necessidade de melhorar ou corrigir o código, não será preciso procurar em inúmeras linhas.

{% highlight ruby %}

@import "header.scss";

{% endhighlight %}

### Mixins

Algumas coisas no CSS são muito repetitivas, e acabam se tornando tediosas. Com os Mixins, é possível fazer grupos que contenham declarações CSS que serão reutilizadas na aplicação. Ao declarar o Mixin, pode-se utilizar parâmentros.

{% highlight ruby %}

@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }

{% endhighlight %}

### Extend/Inheritance

O @extend permite o compartilhamento de propriedades entre elementos, fazendo com que o código se torne mais clean. Abaixo, a forma escrita em SASS:

{% highlight ruby %}

.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}

{% endhighlight %}

Acima o código faz com que as classes .sucess, .error e .warning recebam a propriedade do elemento .message. Abaixo o código compilado:

{% highlight ruby %}
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}

{% endhighlight%}


