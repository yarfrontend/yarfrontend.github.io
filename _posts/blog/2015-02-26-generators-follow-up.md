---
layout: post
title: "ES6. Генераторы. Послесловие."
modified:
categories: blog
author: elifantiev_oleg
excerpt:
tags: [javascript, es6, generators]
image:
  feature:
date: 2015-02-26T12:00:00+04:00
comments: true
share: true
---

[Доклад про генераторы][generator-talk] породил довольно продолжительную дискуссию о их пригодности к использованию
в чем либо, кроме ленивой генерации последовательностей.

Первой задачей, которая не была решена на митапе, была проблема чтения файла, представленного
потоком, построчно, с использованием генераторов (речь, конечно же, про node.js).

Вторая проблема &mdash; пример с AJAX содержал слишком много зависимостей и &#8222;все кишки наружу&#8220;.
Использовать в таком виде &mdash; невозможно.

В итоге мне удалось придумать решение для обоих проблем. По потоку &#8222;клиентский&#8220; код получился такой:

{% highlight javascript %}
var strm = require('fs').createReadStream(__filename);
readStreamByLine(strm, function *gen(nextPlease) {
 
   while(true) {
      var line = yield nextPlease();
      if (line === false) {
         return;
      }
      console.log('Got line: ' + line);
   }
});
{% endhighlight %}

А &#8222;синхронную асинхронность&#8220; удалось упаковать до следующего кода:
{% highlight javascript %}
asyncWrap(function *() {
 
    var currentTime;
    
    log('Lets wait 5 sec');
    
    currentTime = yield promiseFromTimer(5000);
    
    log('Current time is ' + currentTime + '. Now lets wait 10 sec');
    
    try {
        currentTime = yield exceptionFromTimer(10000);
        // Will never happen
        log('Current time is ' + currentTime + '. Ok then, lets stop');
    } catch(e) {
        log('Got exception: ' + e + ' at ' + (new Date()));
    }
    
    var fourtytwo = yield plusTwo(40);
    
    log('And... the meaning of life is ' + fourtytwo);
    
});
{% endhighlight %}

В последнем примере есть ограничение: асинхронная операция должна возвращать [Promise][promise].
Все остальное трактуется как синхронный вызов.

Конкретная реализация оберток [доступна в виде Gist'а][full-source], живой пример с &#8222;асинхронностью&#8220; 
[доступен на jsFiddle][async-live-demo].  

[generator-talk]: /talks/es6-generators/
[promise]: https://promisesaplus.com/
[full-source]: https://gist.github.com/Olegas/7a04d5a58bd931827eb1
[async-live-demo]: http://jsfiddle.net/Olegas/v8Lujpr8/4/