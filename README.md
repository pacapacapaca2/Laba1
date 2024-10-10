# Лабораторная работа №1. Создание activity и передача параметров между ними
- _Выполнил:_ Стан
- _Язык программирования:_ Java

## Что делает приложение?
Приложение состоит из 2 экранов и передает параметр с 1го на 2й по клику на кнопку. Для того, чтобы запустить проект можно прочитать ["Как собрать проект?"](#title1)


### Внешний вид

После запуска открывается экран 1 (`MainActivity`) с кнопкой "Нажми". По тапу на кнопку -> 
- переход на экран 2 (`MainActivity2`)
- передается параметр из `MainActivity` в переменную экрана `MainActivity2`
- отображается текст "Переданный параметр: Стан".
<p align="center">
    <img src="https://github.com/user-attachments/assets/60b5be7f-f869-4bdd-84b6-8a9efbe24112" width="250"> 
    <img src="https://github.com/user-attachments/assets/c879feed-e7fa-4a12-a63a-e9e3c8856e30" width="250">
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

## <a id="title1">Как собрать проект?</a>
_Описан один из многих возможных способов_
1. Скачать ZIP проекта:
    - Клик на зеленую кнопку "<> Code".
    - Клик на "Download ZIP".
2. Распаковать загруженный архив.
3. Запустить Android Studio.
4. Клик на "Open..." на начальном экране / в верхней панели file -> open...
5. Выбрать распакованный архив "Lab1-master".
6. Дождаться завершения всех процессов внутри проекта.
7. Выбрать эмулятор / подключить реальное устройство.
8. Клик на "Run" (должна быть выбрана конфигурация "app").
9. Готово ✅
