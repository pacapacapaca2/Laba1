# Лабораторная работа №1. Создание activity и передача параметров между ними
- _Выполнил:_ Стан
- _Язык программирования:_ Java

## Описание приложения
Приложение состоит из двух экранов и осуществляет передачу параметра с первого экрана на второй по нажатию кнопки.


### Внешний вид

При запуске приложения открывается первый экран (`MainActivity`) на котором расположена кнопка с текстом "Нажми". После нажатия на кнопку происходит: 
- переход на второй экран (`MainActivity2`)
- передача параметра из `MainActivity` во второй экран
- на втором экране отображается текст: "Переданный параметр: Стан".
<p align="center">
    <img src="https://github.com/pacapacapaca2/images/blob/main/eMzMomELExM.jpg" width="250"> 
    <img src="https://github.com/pacapacapaca2/images/blob/main/qHwRu6lmnRI.jpg" width="250">
</p> 


### Механизм передачи параметра
Когда пользователь нажимает на кнопку, выполняются следующие действия:
- создается объект `intent`
- через метод `putExtra`передается пара ключ-значение
- запускается активность `MainActivity2`
``` java
Intent intent = new Intent(MainActivity.this, MainActivity2.class);
intent.putExtra("surname", "Стан");
startActivity(intent);
```

На стороне второго экрана  `MainActivity2` передача данных обрабатывается следующим образом:
- создается объект `bundle`, который через методы `getIntent()` и `getExtras()`,получает данные, переданные через `intent`
- проверяется, что данные получены и не равны null
- в текстовое поле `TextView`выводится переданный параметр:
    - сначала добавляется строка `"Переданный параметр: "`
    - атем извлекается значение параметра по ключу и добавляется к тексту.

``` java
TextView text = findViewById(R.id.textView2);
Bundle extras = getIntent().getExtras();
assert extras != null;
text.setText("Переданный параметр: " + extras.getString("surname"));
```
