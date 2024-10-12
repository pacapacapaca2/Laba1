# Лабораторная работа №1. Создание activity и передача параметров между ними
- _Выполнил:_ Стан
- _Язык программирования:_ Java

## Что делает приложение?
Приложение состоит из 2 экранов и передает параметр с 1го на 2й по клику на кнопку.


### Внешний вид

После запуска открывается экран 1 (`MainActivity`) с кнопкой "Нажми". По тапу на кнопку -> 
- переход на экран 2 (`MainActivity2`)
- передается параметр из `MainActivity` в переменную экрана `MainActivity2`
- отображается текст "Переданный параметр: Стан".
<p align="center">
    <img src="https://github.com/pacapacapaca2/images/blob/main/eMzMomELExM.jpg" width="250"> 
    <img src="https://github.com/pacapacapaca2/images/blob/main/qHwRu6lmnRI.jpg" width="250">
</p> 


### Как передается параметр
Как только приложение получает сигнал о том, что пользователь нажал на кнопку:
- создается объект `intent`
- при помощи его метода `putExtra`задается пара ключ и значение, которая будет передаваться
- запускается `MainActivity2`
``` java
Intent intent = new Intent(MainActivity.this, MainActivity2.class);
intent.putExtra("surname", "Стан");
startActivity(intent);
```

Со стороны `MainActivity2` это выглядит так:
- создается объект `bundle`, который при помощи методов `getIntent()` и `getExtras()`, получает сигнал о том, что передаются данные и какие это данные (в нашем случае ключ + значение)
- проверяется, что данные действительно получены и они не null
- задается значение `TextView`:
    - хардкод `"Переданный параметр: "`
    - по ключу определяется значение переданного параметра и преобразуется в строку, которое добавляется к хардкоду

``` java
TextView text = findViewById(R.id.textView2);
Bundle extras = getIntent().getExtras();
assert extras != null;
text.setText("Переданный параметр: " + extras.getString("surname"));
```
