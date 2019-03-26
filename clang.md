# dictionary/help

## escape sequences (управляющие последовательности)

```c	
	"\n" // перевод строки
	"\t" // знак табуляции
	"\b" // вовзрат на один символ назад с затиранием (backspace)
	"\"" // кавычки
	"\\" // обратная косая черта
```

## элементарные типы данных
	
int - целочисленные данные
float - вещественные числа с плавающей точкой
char - символ (1 байт)
short - короткое целое число
long - длинное целое число
double - вещественное число двойной точности

## спецификация формата из функции printf

```c	
	"%d" // вывести аргумент как десятичное целое цисло
	"%25d" // вывести аргумент как десятичное целое число в поле шириной не менее 6 символов
	"%f" // вывести аргумент как вещественное число с плавающей точкой
	"%25f" // вывести аргумент как вещественное число в поле шириной не менее 25 символов
	"%.2f" // вывевести аргумент как вещественное число с двумя цифрами после десятичной точки
	"%6.2f" // вывести аргумент как вещественное число в поле не короче 6 символов и с двумя цифрами после точки
	"%o" // вывод восьмеричного числа
	"%x" // вывод шестнадцатеричного числа
	"%c" // вывод отдельного символа (char)
	"%s" // вывод строки (string)
	"%%" // вывод знака процента
```