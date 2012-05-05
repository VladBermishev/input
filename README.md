
Описание
========

Функция Scanf из пакета "fmt" языка Go работает не совсем так, как функция scanf языка C.
Более того, использование fmt.Scanf зачастую приводит к неправильному считыванию данных
со стандартного потока ввода.

Пакет "input" экспортирует функцию Scanf, которая фактически является обёрткой над функцией
scanf языка C.

Утановка
--------

Для установки пакета "input" запустите из командной строки команду

	go get -u "github.com/skorobogatov/input"

Исходные тексты пакета будут загружены с github.com, откомпилированы и установлены
в дерево пакетов Go.

Использование
-------------

Функция input.Scanf объявлена как

	func Scanf(format string, a ...interface{})

Её первый параметр представляет собой форматную строку, составленную по тем же правилам,
что и форматная строка функции scanf языка C, за исключением того, что поддерживаются
только форматные спецификаторы %c и %d.

Последующие параметры задают адреса переменных, куда будут помещены считываемые
функцией значения. Переменные должны быть целочисленными, при этом поддерживаются
все целочисленные типы языка Go.

Пример использования функции:

	package main
	
	import (
		"fmt"
		"github.com/skorobogatov/input"
	)
	
	func main() {
		var m, n rune
		input.Scanf("%d%d", &m, &n)
		fmt.Printf("%d %d\n", m, n)
	}

Функция аварийно завершается как при обнаружении любых несоответствий типов параметров
форматным спецификаторам, так и при несовпадении количества параметров и количества
форматных спецификаторов.
