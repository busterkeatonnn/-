# Технологии разработки программного обеспечения
### Ефимов Е.А. ПИМО-01-24

### Практическая работа №5
## 1. Задачи на линейное программирование (без условных операторов и циклов)

### Задание 1.1.
Напишите программу, которая принимает целое число и вычисляет сумму его цифр.
```go
package main

import "fmt"

func addNumberDigits(number int32) int32 {
	//Максимальное количество цифр в числе типа int32 - 10, 
	//поэтому повторяем операцию 10 раз, чтобы не использовать цикл
  digit1 := num % 10
	digit2 := (num / 10) % 10
	digit3 := (num / 100) % 10
	digit4 := (num / 1000) % 10
  digit5 := (num / 10000) % 10
  digit6 := (num / 100000) % 10
  digit7 := (num / 1000000) % 10
  digit8 := (num / 10000000) % 10
  digit9 := (num / 100000000) % 10
  digit10 := (num / 100000000) % 10

	return digit1 + digit2 + digit3 + digit4 + digit5 + digit6 + digit7 + digit8 + digit9 + digit10
}

func main() {
	fmt.Println(addNumberDigits(1234567890))
}
```

### Задание 1.2.
Напишите программу, которая преобразует температуру из градусов Цельсия в Фаренгейты и обратно. 
```go
package main

import (
	"fmt"
  "strconv"
	"strings"
)

func ToF(temp int) float32 {
	return float32(temp)* 9.0 / 5.0 + 32
}

func ToC(temp int) float32 {
	return (float32)(temp-32) * 5.0 / 9.0
}


func main() {
	cel := "25 (Celsius)"
  //Получаем значение градуса из входной строки и приводим к типу int
	temp1, _ := strconv.Atoi(strings.Split(cel, " ")[0])

	fmt.Printf("%f (Farhrenheit)\n", ToF(temp1))

	far := "32 (Farhrenheit)"
  //Получаем значение градуса из входной строки и приводим к типу int
	temp2, _ := strconv.Atoi(strings.Split(far, " ")[0])

	fmt.Printf("%f (Celsius)\n", ToC(temp2))

}
```

### Задание 1.3.
Напишите программу, которая принимает массив чисел и возвращает новый массив, где каждое число удвоено.
```go
package main

import "fmt"

func SliceTwice(src []int) []int {
	newSlice := make([]int, len(src))

	for i := range src {
		newSlice[i] = src[i] * 2
	}

	return newSlice
}


func main() {
	fmt.Println(SliceTwice([]int{1, 2, 3, 4}))
}

```

### Задание 1.4.
Напишите программу, которая принимает несколько строк и объединяет их в одну строку через пробел.
```go
package main

import (
    "fmt"
    "strings"
)

func main() {
    // Принимаем несколько строк
    input := []string{"1", "2", "aaa", "dddd", "cccccc"}

    // Объединяем строки через пробел
    result := strings.Join(input, " ")

    // Выводим результат
    fmt.Println(result)
}

```

### Задание 1.5.
Напишите программу, которая вычисляет расстояние между двумя точками в 2D пространстве.
```go
package main

import (
    "fmt"
    "math"
)

func main() {
    // Координаты двух точек
    x1, y1 := 1.0, 2.0
    x2, y2 := 4.0, 6.0

    // Вычисляем расстояние 
    distance := math.Sqrt(math.Pow(x2-x1, 2) + math.Pow(y2-y1, 2))

    // Выводим результат
    fmt.Printf("Расстояние между точками: %.2f\n", distance)
}
```

## 2. Задачи с условным оператором

### Задание 2.1.
Напишите программу, которая проверяет, является ли введенное число четным или нечетным.
```go
package main

import "fmt"

func main() {
	var num int
	fmt.Println("Введите число")
	fmt.Scan(&num)

	if num%2 == 0 {
		fmt.Println("Чётное")
	} else {
		fmt.Println("Нечётное")
	}
}
```

### Задание 2.2.
Напишите программу, которая проверяет, является ли введенный год високосным.
```go
package main

import "fmt"

func main() {
 var year int
 fmt.Print("Введите год: ")
 fmt.Scan(&year)

 // Проверка, является ли год високосным
 if (year%4 == 0 && year%100 != 0) || (year%400 == 0) {
  fmt.Printf("Год %d является високосным", year)
 } else {
  fmt.Printf("Год %d не является високосным", year)
 }
}
```

### Задание 2.3.
Напишите программу, которая принимает три числа и выводит наибольшее из них.
```go
package main

import "fmt"

func main() {
 var a, b, c int

 fmt.Print("Введите первое число: ")
 fmt.Scan(&a)
 fmt.Print("Введите второе число: ")
 fmt.Scan(&b)
 fmt.Print("Введите третье число: ")
 fmt.Scan(&c)

 var max int

 // Проверка наибольшего числа с использованием условных операторов
 if a >= b && a >= c {
  max = a
 } else if b >= a && b >= c {
  max = b
 } else {
  max = c
 }

 fmt.Print("Наибольшее из введенных чисел: ", max)
}
```

### Задание 2.4.
Напишите программу, которая принимает возраст человека и выводит, к какой возрастной группе он относится (ребенок, подросток, взрослый, пожилой. В комментариях указать возрастные рамки).
```go
package main

import "fmt"

func main() {
 var age int

 fmt.Print("Введите ваш возраст: ")
 fmt.Scan(&age)

 // Определяем возрастную группу
 if age >= 0 && age <= 12 { // 0-12 лет – ребенок
  fmt.Println("Вы ребенок.")
 } else if age >= 13 && age <= 17 { // 13-17 лет – подросток
  fmt.Println("Вы подросток.")
 } else if age >= 18 && age <= 59 { // 18-59 лет – взрослый
  fmt.Println("Вы взрослый.")
 } else if age >= 60 { // 60+ лет – пожилой
  fmt.Println("Вы пожилой.")
 } else {
  fmt.Println("Некорректный возраст.")
 }
}
```

### Задание 2.5.
Напишите программу, которая проверяет, делится ли число одновременно на 3 и 5.
```go
package main

import "fmt"

func main() {
 var number int

 fmt.Print("Введите число: ")
 fmt.Scan(&number)
 
 if number%3 == 0 && number%5 == 0 {
  fmt.Println("Число", number, "делится на 3 и 5.")
 } else {
  fmt.Println("Число", number, "не делится на 3 и 5 одновременно.")
 }
}

```

## 3. Задачи на циклы
### Задание 3.1.
Напишите программу, которая вычисляет факториал числа.
```go
package main

import "fmt"

func main() {
 var n int
 fmt.Print("Введите число для вычисления факториала: ")
 fmt.Scan(&n)

 if n < 0 {
  fmt.Println("Факториал отрицательного числа не определен.")
  return
 }
 factorial := 1
 for i := 1; i <= n; i++ {
    factorial *= i
 }
 fmt.Printf("Факториал числа %d равен %d", n, factorial)
}
```

### Задание 3.2.
Напишите программу, которая выводит первые "n" чисел Фибоначчи.
```go
package main

import "fmt"

func main() {
 var n int
 fmt.Print("Введите количество чисел Фибоначчи для вывода: ")
 fmt.Scan(&n)

 // Первые два числа Фибоначчи
 a, b := 0, 1

 fmt.Printf("Первое %d чисел Фибоначчи: ", n)
 for i := 1; i <= n; i++ {
  fmt.Print(a, " ")
  next := a + b
  a = b
  b = next
 }
}
```

### Задание 3.3.
Напишите программу, которая переворачивает массив чисел.
```go
package main

import "fmt"

func reverseArray(arr []int) []int {
 // Создаем новый массив для хранения перевернутых элементов
 reversed := make([]int, len(arr))

 // Заполняем новый массив элементами в обратном порядке
 for i := 0; i < len(arr); i++ {
  reversed[i] = arr[len(arr)-1-i]
 }

 return reversed
}

func main() {
 // Объявляем массив
 arr := []int{1, 2, 3, 4, 5}

 // Переворачиваем массив
 reversedArr := reverseArray(arr)

 // Выводим результат
 fmt.Println("Original array:", arr)
 fmt.Println("Reversed array:", reversedArr)
}

```

### Задание 3.4.
Напишите программу, которая выводит все простые числа до заданного числа.
```go
package main

import "fmt"

// Функция для проверки, является ли число простым
func isPrime(num int) bool {
 if num <= 1 {
  return false
 }
 for i := 2; i*i <= num; i++ {
  if num%i == 0 {
   return false
  }
 }
 return true
}

func main() {
 var n int
 fmt.Print("Введите верхнюю границу: ")
 fmt.Scan(&n)

 fmt.Printf("Простые числа до %d: ", n)
 for i := 2; i <= n; i++ {
  if isPrime(i) {
   fmt.Println(i)
  }
 }
}
```

### Задание 3.5.
Напишите программу, которая вычисляет сумму всех чисел в массиве.
```go
package main

import "fmt"

func main() {
 // Объявляем массив с числами
 numbers := []int{1, 2, 3, 4, 5}

 // Переменная для хранения суммы
 sum := 0

 // Используем цикл для вычисления суммы
 for number := range numbers { sum += number }

 // Выводим результат
 fmt.Printf("Сумма всех чисел в массиве: %d", sum)
}
```

