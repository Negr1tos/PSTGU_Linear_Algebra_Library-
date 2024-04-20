![image](https://upload.wikimedia.org/wikipedia/ru/0/00/%D0%9B%D0%BE%D0%B3%D0%BE%D1%82%D0%B8%D0%BF_%D0%9F%D0%A1%D0%A2%D0%93%D0%A3.jpg)# PSTGU_Linear_Algebra_Library

## Библиотека для работы с линейной алгеброй
Эта библиотека предоставляет классы и методы для работы с линейной алгеброй, включая
операции с векторами, матрицами и многомерными массивами.
Кратко:
### Классы
1. **`ComplexNumber`**
 - Представляет комплексное число.
 - Операции: сложение, вычитание, умножение, деление.
2. **`NArray`**
 - Базовый класс для представления N-мерных массивов.
 - Инициализация: `$nArray = new NArray($data)` или `$nArray = new NArray($dimensions,
$fillType, $isImaginaryInt)`.
 - Методы: `getElement`, `setElement`, `getDimensions`, `getShape`, `display`.
3. **`Matrix`**
 - Класс для представления двумерных массивов (матриц).
 - Наследует от `NArray`.
 - Инициализация: `$matrix = new Matrix($rows, $cols, $fillType, $isComplex, $isPrime)`.
 - Методы: `add`, `multiply`, `solveLinearSystem`, `determinant`, `renderMatrix`,
`renderStyledMatrix`.
4. **`Vector`**
 - Класс для представления векторов.
 - Наследует от `Matrix`.
 - Инициализация: `$vector = new Vector($data, $isComplex)`.
 - Методы: `add`, `multiply`, `dotProduct`, `angleWithVector`, `visualize`,
`composeTransformations`, `kernelOfTransformation`, `imageOfTransformation`.
### Инициализация переменных
1. Инициализация `NArray` с входными данными:
 ```php
 $data = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
 $nArray = new NArray($data);
 ```
2. Инициализация `NArray` с размерностями и способом заполнения:
 ```php
 $nArray = new NArray([2, 3, 4], 'random_complex', true);
 ```
3. Инициализация `Matrix` с размерами и способом заполнения:
 ```php
 $matrix = new Matrix(3, 4, 'zero', false, true);
 ```
4. Инициализация `Vector` с данными:
 ```php
 $vector = new Vector([1, 2, 3, '4.5:6.7', ':8', 9]);
 ```
Библиотека позволяет выполнять различные операции с векторами, матрицами и
многомерными массивами, включая сложение, умножение, решение систем линейных
уравнений, вычисление определителей и другие операции линейной алгебры.
Более подробно:
подробное описание каждой публичной функции в классе ComplexNumber:
1. __construct($real, $imaginary)
• Назначение: Конструктор класса, инициализирующий комплексное число с
заданными вещественной и мнимой частями.
• Входные параметры:
• $real (число): Вещественная часть комплексного числа.
• $imaginary (число): Мнимая часть комплексного числа.
• Возвращаемое значение: Нет (конструктор не возвращает значение).
• Пример использования:
php
Copy code
$z = new ComplexNumber(2, 3); // Создает комплексное число 2 + 3i
2. getReal()
• Назначение: Получить вещественную часть комплексного числа.
• Входные параметры: Нет.
• Возвращаемое значение: Вещественная часть комплексного числа (число).
• Пример использования:
php
Copy code
$z = new ComplexNumber(2, 3);
$real = $z->getReal(); // $real = 2
3. getImaginary()
• Назначение: Получить мнимую часть комплексного числа.
• Входные параметры: Нет.
• Возвращаемое значение: Мнимая часть комплексного числа (число).
• Пример использования:
php
Copy code
$z = new ComplexNumber(2, 3);
$imaginary = $z->getImaginary(); // $imaginary = 3
4. add(ComplexNumber $other)
• Назначение: Сложить два комплексных числа.
• Входные параметры:
• $other (ComplexNumber): Комплексное число, которое будет прибавлено
к текущему.
• Возвращаемое значение: Новый объект ComplexNumber, представляющий
сумму двух комплексных чисел.
• Пример использования:
php
Copy code
$z1 = new ComplexNumber(1, 2);
$z2 = new ComplexNumber(3, 4);
$z3 = $z1->add($z2); // $z3 = 4 + 6i
5. subtract(ComplexNumber $other)
• Назначение: Вычесть одно комплексное число из другого.
• Входные параметры:
• $other (ComplexNumber): Комплексное число, которое будет вычтено из
текущего.
• Возвращаемое значение: Новый объект ComplexNumber, представляющий
разность двух комплексных чисел.
• Пример использования:
php
Copy code
$z1 = new ComplexNumber(5, 6);
$z2 = new ComplexNumber(2, 3);
$z3 = $z1->subtract($z2); // $z3 = 3 + 3i
6. multiply(ComplexNumber $other)
• Назначение: Умножить два комплексных числа.
• Входные параметры:
• $other (ComplexNumber): Комплексное число, на которое будет
умножено текущее число.
• Возвращаемое значение: Новый объект ComplexNumber, представляющий
произведение двух комплексных чисел.
• Пример использования:
php
Copy code
$z1 = new ComplexNumber(2, 3);
$z2 = new ComplexNumber(4, 5);
$z3 = $z1->multiply($z2); // $z3 = -7 + 22i
7. divide(ComplexNumber $other)
• Назначение: Разделить одно комплексное число на другое.
• Входные параметры:
• $other (ComplexNumber): Комплексное число, на которое будет
разделено текущее число.
• Возвращаемое значение: Новый объект ComplexNumber, представляющий
частное двух комплексных чисел.
• Пример использования:
php
Copy code
$z1 = new ComplexNumber(8, 6);
$z2 = new ComplexNumber(2, 3);
$z3 = $z1->divide($z2); // $z3 = 3 - 0.5i
публичные функции класса NArray из вашей библиотеки на PHP.
1. __construct(array $data = null, array $dimensions = null,
$fillType = 'zero', $isImaginaryInt = false)
Назначение: Конструктор класса NArray, предназначенный для инициализации N-мерного
массива. Он может инициализировать массив из предоставленных данных или создать новый
массив с указанными размерностями и способом заполнения.
Входные параметры:
• $data (array|null, по умолчанию null): многомерный массив с данными для
инициализации массива. Если не указан, массив будет создан с нулями или согласно
другим параметрам.
• $dimensions (array|null, по умолчанию null): массив с размерностями
создаваемого N-мерного массива в формате [размерность_1, размерность_2,
..., размерность_N]. Если не указан, размерности будут определены из $data.
• $fillType (string, по умолчанию 'zero'): способ заполнения массива, если он
создается заново. Доступные значения: 'zero' (по
умолчанию), 'random' (случайные вещественные числа от -1 до
1), 'random_complex' (случайные комплексные
числа), 'random_complex_int' (случайные комплексные числа с целочисленной
мнимой частью).
• $isImaginaryInt (bool, по умолчанию false): флаг, указывающий, что мнимая
часть комплексных чисел должна быть целочисленной. Действует только
при $fillType = 'random_complex' и $data не указано.
Возвращаемое значение: N-мерный массив, инициализированный согласно входным
параметрам.
Примеры использования:
php
Copy code
// Создание 2х2х2 массива со случайными вещественными числами
$nArray = new NArray(null, [2, 2, 2], 'random');
// Инициализация массива из предоставленных данных
$data = [
 [1, 2, 3],
 [4, '5:6', 7]
];
$nArray = new NArray($data);
// Создание 3х2 массива со случайными комплексными числами с целочисленной
мнимой частью
$nArray = new NArray(null, [3, 2], 'random_complex_int', true);
2. getElement($indices, $asComplexNumber = false)
Назначение: Метод для получения значения элемента N-мерного массива по индексам.
Входные параметры:
• $indices (array): массив индексов для доступа к элементу.
• $asComplexNumber (bool, по умолчанию false): флаг, указывающий, что
значение должно быть возвращено как комплексное число.
Возвращаемое значение: Значение элемента по указанным индексам (вещественное или
комплексное число).
Примеры использования:
php
Copy code
// Получение элемента по индексам [1, 0, 1] как вещественного числа
$value = $nArray->getElement([1, 0, 1]);
// Получение элемента по индексам [0, 1, 0] как комплексного числа
$complexValue = $nArray->getElement([0, 1, 0], true);
3. setElement($indices, $value, $asComplexNumber = false)
Назначение: Метод для установки значения элемента N-мерного массива по индексам.
Входные параметры:
• $indices (array): массив индексов для доступа к элементу.
• $value (mixed): значение для установки (вещественное или комплексное число).
• $asComplexNumber (bool, по умолчанию false): флаг, указывающий,
что $value является комплексным числом.
Возвращаемое значение: Ничего не возвращает, устанавливает значение элемента по
указанным индексам.
Примеры использования:
php
Copy code
// Установка элемента по индексам [1, 0, 1] вещественным числом
$nArray->setElement([1, 0, 1], 42);
// Установка элемента по индексам [0, 1, 0] комплексным числом
$nArray->setElement([0, 1, 0], new ComplexNumber(1, 2), true);
4. display()
Назначение: Метод для отображения содержимого N-мерного массива в виде текста.
Входные параметры: Нет.
Возвращаемое значение: Ничего не возвращает, выводит содержимое массива на экран.
Примеры использования:
php
Copy code
$nArray->display();
5. getData()
Назначение: Метод для получения данных N-мерного массива.
Входные параметры: Нет.
Возвращаемое значение: Многомерный массив с данными N-мерного массива.
Примеры использования:
php
Copy code
$data = $nArray->getData();
6. setData(array $data)
Назначение: Метод для установки данных N-мерного массива.
Входные параметры:
• $data (array): многомерный массив с новыми данными для установки.
Возвращаемое значение: Ничего не возвращает, устанавливает новые данные для N-мерного
массива.
Примеры использования:
php
Copy code
$newData = [
 [1, 2, 3],
 [4, 5, 6]
];
$nArray->setData($newData);
публичные функции класса Matrix
1. __construct($rows, $cols, $type = 'zero', $isComplex = false, $isPrime = false)
• Назначение: Конструктор класса Matrix, создающий новую матрицу
заданных размеров.
• Входные параметры:
• $rows (int): количество строк в матрице.
• $cols (int): количество столбцов в матрице.
• $type (string, опционально): тип инициализации матрицы. Допустимые
значения: 'zero' (по умолчанию), 'one', 'random'.
• $isComplex (bool, опционально): если true, элементы матрицы будут
комплексными числами, иначе - действительными.
• $isPrime (bool, опционально): если true, матрица будет заполнена
простыми числами.
• Возвращаемое значение: Новый объект Matrix.
• Пример использования:
php
Copy code
// Создать матрицу 3x4 с нулевыми элементами
$matrix = new Matrix(3, 4);
// Создать матрицу 2x2 с единичными элементами
$identity = new Matrix(2, 2, 'one');
// Создать матрицу 5x5 со случайными комплексными числами
$random = new Matrix(5, 5, 'random', true);
// Создать матрицу 4x4, заполненную простыми числами
$primes = new Matrix(4, 4, 'zero', false, true);
2. add(Matrix $other)
• Назначение: Сложение двух матриц.
• Входные параметры:
• $other (Matrix): матрица, которую нужно прибавить к текущей.
• Возвращаемое значение: Новый объект Matrix, представляющий сумму двух
матриц.
• Пример использования:
php
Copy code
$A = new Matrix(2, 2, 'one');
$B = new Matrix(2, 2, [[1, 2], [3, 4]]);
$C = $A->add($B); // [[2, 3], [4, 5]]
3. multiply(Matrix $other)
• Назначение: Умножение двух матриц.
• Входные параметры:
• $other (Matrix): матрица, на которую нужно умножить текущую.
• Возвращаемое значение: Новый объект Matrix, представляющий
произведение двух матриц.
• Пример использования:
php
Copy code
$A = new Matrix(2, 3, [[1, 2, 3], [4, 5, 6]]);
$B = new Matrix(3, 2, [[7, 8], [9, 10], [11, 12]]);
$C = $A->multiply($B); // [[58, 64], [139, 154]]
4. solveLinearSystem($b)
• Назначение: Решение системы линейных уравнений методом Гаусса.
• Входные параметры:
• $b (array): вектор правых частей системы уравнений.
• Возвращаемое значение: Массив комплексных чисел, представляющий
решение системы уравнений.
• Пример использования:
php
Copy code
$A = new Matrix(3, 3, [[1, 2, 3], [4, 5, 6], [7, 8, 9]]);
$b = [1, 2, 3];
$x = $A->solveLinearSystem($b); // [-1, 1, 0]
5. determinant($method = 'gaussian')
• Назначение: Вычисление определителя матрицы.
• Входные параметры:
• $method (string, опционально): метод вычисления определителя.
Допустимые значения: 'gaussian' (по умолчанию) или 'lu'.
• Возвращаемое значение: Комплексное число, представляющее определитель
матрицы.
• Пример использования:
php
Copy code
$A = new Matrix(3, 3, [[1, 2, 3], [4, 5, 6], [7, 8, 9]]);
$det = $A->determinant(); // 0
$det = $A->determinant('lu'); // 0
6. renderMatrix()
• Назначение: Отображение матрицы в виде HTML-таблицы.
• Входные параметры: Нет.
• Возвращаемое значение: Строка, содержащая HTML-код для отображения
матрицы.
• Пример использования:
php
Copy code
$A = new Matrix(2, 2, [[1, 2], [3, 4]]);
$html = $A->renderMatrix();
echo $html;
7. renderStyledMatrix($styles = [])
• Назначение: Отображение матрицы в виде HTML-таблицы со стилями.
• Входные параметры:
• $styles (array, опционально): ассоциативный массив со стилями CSS
для таблицы, ячеек, четных и нечетных строк.
• Возвращаемое значение: Строка, содержащая HTML-код для отображения
матрицы со стилями.
• Пример использования:
php
Copy code
$A = new Matrix(2, 2, [[1, 2], [3, 4]]);
$styles = [
 'table' => 'border: 1px solid black;',
 'td' => 'padding: 5px;',
 'even-row' => 'background-color: #eee;',
 'odd-row' => 'background-color: #fff;'
];
$html = $A->renderStyledMatrix($styles);
echo $html;
8. inverse()
• Назначение: Вычисление обратной матрицы.
• Входные параметры: Нет.
• Возвращаемое значение: Новый объект Matrix, представляющий обратную
матрицу, или null, если матрица вырожденная.
• Пример использования:
php
Copy code
$A = new Matrix(2, 2, [[1, 2], [3, 4]]);
$B = $A->inverse(); // [[-2, 1], [1.5, -0.5]]
публичные функции класса Vector:
1. __construct($data, $isComplex = false):
• Назначение: Конструктор класса Vector, создающий новый объект вектора.
• Входные параметры:
• $data (массив): Массив элементов, представляющих компоненты
вектора.
• $isComplex (логический, необязательный): Флаг, указывающий,
являются ли элементы вектора комплексными числами. По умолчанию -
false.
• Возвращаемое значение: Новый объект Vector.
• Примеры использования:
php
Copy code
$vector1 = new Vector([1, 2, 3]); // Создает вектор (1, 2, 3)
$vector2 = new Vector([1, 2j, 3 + 4j], true); // Создает вектор с
комплексными компонентами (1, 2i, 3 + 4i)
2. angleWithVector(Vector $other, $metric = 'euclidean'):
• Назначение: Вычисляет угол между текущим вектором и другим
вектором $other по заданной метрике.
• Входные параметры:
• $other (объект Vector): Вектор, с которым необходимо вычислить
угол.
• $metric (строка, необязательная): Метрика, используемая для
вычисления угла. Допустимые значения: 'euclidean' (евклидова метрика),
'manhattan' (манхэттенская метрика) и 'minkowski' (минковского
метрика). По умолчанию используется евклидова метрика.
• Возвращаемое значение: Значение угла в радианах.
• Примеры использования:
php
Copy code
$vector1 = new Vector([1, 1]);
$vector2 = new Vector([1, -1]);
$angle = $vector1->angleWithVector($vector2); // Угол между
векторами (1, 1) и (1, -1) по евклидовой метрике (pi/2 радиан)
$angle = $vector1->angleWithVector($vector2, 'manhattan'); // Угол
по манхэттенской метрике
3. visualize(Vector $other = null):
• Назначение: Визуализирует текущий вектор и, при наличии, вектор $other, а
также угол между ними.
• Входные параметры:
• $other (объект Vector, необязательный): Второй вектор для
визуализации и вычисления угла между векторами. Если не задан, то
визуализируется только текущий вектор.
• Возвращаемое значение: Функция не возвращает значение, а выводит
визуализацию.
• Примеры использования:
php
Copy code
$vector1 = new Vector([1, 2]);
$vector1->visualize(); // Визуализирует только вектор (1, 2)
$vector2 = new Vector([-1, 1]);
$vector1->visualize($vector2); // Визуализирует векторы (1, 2) и (-
1, 1), а также угол между ними
4. composeTransformations(...$transformations):
• Назначение: Создает новую функцию, которая применяет последовательность
линейных преобразований к вектору.
• Входные параметры:
• $transformations (массив функций): Массив функций,
представляющих линейные преобразования, которые будут применяться
к вектору последовательно.
• Возвращаемое значение: Новая функция, принимающая вектор в качестве
аргумента и возвращающая результат последовательного применения всех
заданных преобразований.
• Примеры использования:
php
Copy code
$vector = new Vector([1, 2]);
$rotation = function (Vector $v) {
 return new Vector([-$v->getElement([1, 0]), $v->getElement([0,
0])]);
};
$scaling = function (Vector $v) {
 return new Vector([$v->getElement([0, 0]) * 2, $v-
>getElement([1, 0]) * 2]);
};
$transformedVector = $vector->composeTransformations($rotation,
$scaling)($vector);
// $transformedVector содержит вектор (-2, 4) - результат
последовательного применения поворота и масштабирования
5. kernelOfTransformation($transformation):
• Назначение: Находит ядро (нуль-пространство) заданного линейного
преобразования для текущего вектора.
• Входные параметры:
• $transformation (функция): Функция, представляющая линейное
преобразование, для которого необходимо найти ядро.
• Возвращаемое значение: Ядро линейного преобразования, представленное как
объект Vector или набор векторов.
• Примеры использования: Функция не реализована в предоставленном коде.
6. imageOfTransformation($transformation):
• Назначение: Находит образ (значения) заданного линейного преобразования
для текущего вектора.
• Входные параметры:
• $transformation (функция): Функция, представляющая линейное
преобразование, для которого необходимо найти образ.
• Возвращаемое значение: Образ линейного преобразования, представленный
как объект Vector или набор векторов.
• Примеры использования: Функция не реализована в предоставленном коде.
7. add(Matrix $other):
• Назначение: Сложение текущего вектора с другим вектором $other.
• Входные параметры:
• $other (объект Matrix или Vector): Вектор, который необходимо
сложить с текущим вектором.
• Возвращаемое значение: Новый объект Vector, представляющий сумму двух
векторов.
• Примеры использования:
php
Copy code
$vector1 = new Vector([1, 2]);
$vector2 = new Vector([-1, 3]);
$sum = $vector1->add($vector2); // $sum содержит вектор (0, 5)
8. dotProduct(Vector $other):
• Назначение: Вычисляет скалярное произведение (dot product) текущего вектора
и вектора $other.
• Входные параметры:
• $other (объект Vector): Вектор, для которого необходимо вычислить
скалярное произведение с текущим вектором.
• Возвращаемое значение: Скалярное произведение двух векторов в виде
объекта ComplexNumber.
