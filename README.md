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
    <img src="https://private-user-images.githubusercontent.com/163531602/375938860-bd6dc254-0fd1-4df9-975a-ba0e5ab65a95.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MjkxODU1MTQsIm5iZiI6MTcyOTE4NTIxNCwicGF0aCI6Ii8xNjM1MzE2MDIvMzc1OTM4ODYwLWJkNmRjMjU0LTBmZDEtNGRmOS05NzVhLWJhMGU1YWI2NWE5NS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQxMDE3JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MTAxN1QxNzEzMzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMjJlZGRhOTU2OWU1YWVjNTEwMTRiMjY0YzJkNDRhNThiOGZmM2VmZWRhMDM2YTBkYTlhNDkyNzQ0ZDI1OWZmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.tjrbt3M5f3SIPlLWz78WAB1fSOLH2uXuG74DhI2Hi2Y" width="250"> 
    <img src="https://private-user-images.githubusercontent.com/163531602/375938860-bd6dc254-0fd1-4df9-975a-ba0e5ab65a95.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjg3MjAyMTYsIm5iZiI6MTcyODcxOTkxNiwicGF0aCI6Ii8xNjM1MzE2MDIvMzc1OTM4ODYwLWJkNmRjMjU0LTBmZDEtNGRmOS05NzVhLWJhMGU1YWI2NWE5NS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQxMDEyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MTAxMlQwNzU4MzZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02Mjg1NTk2MTBhZmRmMTE1Mzc2YmZhMThiMjMxZDNjYzg5MzcwZGVlY2ZkMTJmOWI1MTIyYzZiZDRhNWYwM2U0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.K42W6gdio1zgeyIzYYSnVSKzuzAxS9RD1ewYSPUEa4w" width="250">
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
