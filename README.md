
Описание
========

Функция Scanf из пакета "fmt" языка Go работает не совсем так, как функция scanf языка C.
Более того, использование fmt.Scanf зачастую приводит к неправильному считыванию данных
со стандартного потока ввода.

Кроме того, стандартная библиотека языка Go не предоставляет аналога функции gets языка C.

Пакет "input" экспортирует функции Scanf и Gets, которые фактически являются обёртками
над функциями scanf и gets языка C.

Утановка
--------

Для установки пакета "input" убедитесь, что в вашей системе установлена система управления
версиями git. Для этого в командной строке выполните:

	git

Если команда не сработала, установите git с помощью программы установки программного
обеспечения, принятой в вашей системе.

Затем запустите из командной строки команду

	go get -u "github.com/skorobogatov/input"

Исходные тексты пакета будут загружены с github.com, откомпилированы и установлены
в дерево пакетов Go.

Использование
-------------

Функция input.Scanf объявлена как

	func Scanf(format string, a ...interface{})

Её первый параметр представляет собой форматную строку, составленную по тем же правилам,
что и форматная строка функции scanf языка C, за исключением того, что поддерживаются
только форматные спецификаторы %c, %d и %s.

Последующие параметры задают адреса переменных, куда будут помещены считываемые
функцией значения. Переменные, соответствующие вхождениям спецификаторов %c и %d,
должны быть целочисленными (поддерживаются все целочисленные типы языка Go).
Переменные, соответствующие вхождениям спецификатора %s, должны иметь тип string.

Функция аварийно завершается как при обнаружении любых несоответствий типов параметров
форматным спецификаторам, так и при несовпадении количества параметров и количества
форматных спецификаторов.

Функция input.Gets объявлена как

	func Gets() string

Она считывает строку из стандартного потока ввода до тех пор, пока в нём не появится
символ перевода строки.

Пример использования функций:

	package main

	import (
		"fmt"
		"github.com/skorobogatov/input"
	)

	func main() {
		var m, n int
		input.Scanf("%d%d", &m, &n)

		input.Scanf("\n") // Чтобы считать \n, оставшийся после Scanf
		s := input.Gets()

		fmt.Printf("%d %d\n", m, n)
		fmt.Printf("%s\n", s)
	}
