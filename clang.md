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
## Разное

```c
	"#define"	имя		текст для подстановки // определяет символическое имя или символическую константу. Всякий раз, когда в программе встретися определенное таким образом "имя"(не в кавычках и не в составе другого имени), оно будет заменено соответствующим "текст для подстановки. "Имя" задается в той же форме, что и имя переменной,т.е. как последовательность букв и цифр, начинающаяся с буквы. "Текст для подстановки" может представлять собой последовательность любых символов, а не 	только цифр.
	"getchar()" // функция считывает следующий символ текстового потока ввода и возвращает его в качестве своего значения 
	"putchar()" // функция при каждом вызове выводит один символ 
	"||"		// Логическая операция ИЛИ 
	"&&"		// Логическая операция И, имеет выше приоритет, чем ИЛИ 
	"a+=b equal a = a + b" - //инкремент//
```
## Функция

*Синтаксис функции:*
```
return_type function_name(arg_type_1 arg_1, arg_type_2 arg_2, ...) {
    	...
        ...
        ...
        [if return_type is non void]
        	return something of type `return_type`;
    }
```
*Пример*:
```
int sum_of_four(int a, int b, int c, int d) {
    	int sum = 0;
        sum += a;
        sum += b;
        sum += c;
        sum += d;
        return sum;
    }
```

