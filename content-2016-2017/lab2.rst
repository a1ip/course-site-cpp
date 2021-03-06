Сортировка. Двоичный поиск. Математические функции. Стандартная библиотека.   
###########################################################################

:date: 2016-09-06 00:30
:lecture_link: https://youtu.be/_iotDcBr0-s

.. default-role:: code
.. contents:: Содержание

Сортировки
==========

Cортировка -- это упорядочивание элементов в списке или массиве. В случае, когда элемент списка имеет несколько полей, поле, служащее критерием порядка, называется ключом сортировки. На практике в качестве ключа часто выступает число, а в остальных полях хранятся какие-либо данные, никак не влияющие на работу алгоритма.

Оценка алгоритма сортировки
---------------------------

Алгоритмы сортировки оцениваются по скорости выполнения и эффективности использования памяти:

* Время — основной параметр, характеризующий быстродействие алгоритма. Называется также вычислительной сложностью. Для упорядочения важны худшее, среднее и лучшее поведение алгоритма в терминах мощности входного множества A. Если на вход алгоритму подаётся множество A, то обозначим n = \|A\|. Для типичного алгоритма хорошее поведение — это O(n log(n)) и плохое поведение — это O(n\ :sup:`2`\). Идеальное поведение для упорядочения — O(n). Алгоритмы сортировки, использующие только абстрактную операцию сравнения ключей всегда нуждаются по меньшей мере в O(n log(n)) сравнениях. 

* Память — ряд алгоритмов требует выделения дополнительной памяти под временное хранение данных. Как правило, эти алгоритмы требуют O(log(n)) памяти. При оценке не учитывается место, которое занимает исходный массив и независящие от входной последовательности затраты, например, на хранение кода программы (так как всё это потребляет O(1)). Алгоритмы сортировки, не потребляющие дополнительной памяти, относят к сортировкам на месте.

Оптимальность O(n log(n))
---------------------------

Задача сортировки в общем случае предполагает, что единственной обязательно наличествующей операцией для элементов является сравнение. 

Пусть по ходу работы алгоритмом производится k сравнений. Ответом на сравнение двух элементов a и b может быть один из двух вариантов ( a<b или a>b). Значит, всего возможно 2\ :sup:`k`\  вариантов комбинаций ответов на k вопросов.

Количество перестановок из n элементов равно n!. Для того, чтобы можно было провести сюръекцию из множества ответов на сравнения на множество перестановок, количество сравнений должно быть не меньше, чем log\ :sub:`2`\(n!) (это обеспечивается тем, что сравнение — единственная разрешённая операция).

Прологарифмировав формулу Стирлинга, можно обнаружить, что log\ :sub:`2`\(n!) = O(n log(n))


Свойства и классификация
------------------------

* Устойчивость — устойчивая сортировка не меняет взаимного расположения элементов с одинаковыми ключами.

* Естественность поведения — эффективность метода при обработке уже упорядоченных или частично упорядоченных данных. Алгоритм ведёт себя естественно, если учитывает эту характеристику входной последовательности и работает лучше.

* Использование операции сравнения. Алгоритмы, использующие для сортировки сравнение элементов между собой, называются основанными на сравнениях. Минимальная трудоемкость худшего случая для этих алгоритмов составляет O(n log(n)), но они отличаются гибкостью применения. Для специальных случаев (типов данных) существуют более эффективные алгоритмы.


Список алгоритмов сортировки
----------------------------

В этой таблице n — это количество записей, которые необходимо упорядочить, а k — это количество уникальных ключей.

Алгоритмы устойчивой сортировки
*******************************

* Сортировка пузырьком (англ. Bubble sort) — для каждой пары индексов производится обмен, если элементы расположены не по порядку. Сложность алгоритма: O(n\ :sup:`2`\).
* Сортировка перемешиванием (англ. Cocktail sort). Сложность алгоритма: O(n\ :sup:`2`\).
* Гномья сортировка (англ. Gnome sort). — схожа с сортировкой пузырьком и сортировкой вставками. Сложность алгоритма — O(n\ :sup:`2`\).
* Сортировка вставками (Insertion sort) — Определяем, где текущий элемент должен находиться в упорядоченном списке, и вставляем его туда. Сложность алгоритма: O(n\ :sup:`2`\).
* Сортировка слиянием (Merge sort) — выстраиваем первую и вторую половину списка отдельно, а затем объединяем упорядоченные списки. Сложность алгоритма: O(n log(n)). Требуется O(n) дополнительной памяти.
* Сортировка с помощью двоичного дерева (англ. Tree sort). Сложность алгоритма: O(n log(n)). Требуется O(n) дополнительной памяти.
* Сортировка Timsort (англ. Timsort) — комбинированный алгоритм (используется сортировка вставками и сортировка слиянием). Сложность алгоритма: O(n log(n)). Требуется O(n) дополнительной памяти. Разработан для использования в языке Python.
* Сортировка подсчётом (Counting sort). Сложность алгоритма: O(n+k). Требуется O(n+k) дополнительной памяти.
* Блочная сортировка (Корзинная сортировка, Bucket sort) — требуется O(k) дополнительной памяти и знание о природе сортируемых данных, выходящее за рамки функций «переставить» и «сравнить». Сложность алгоритма: O(n).
* Поразрядная сортировка (она же цифровая сортировка) — сложность алгоритма: O(n k); требуется O(k) дополнительной памяти.

Алгоритмы неустойчивой сортировки
*********************************

* Сортировка выбором (англ. Selection sort) — поиск наименьшего или наибольшего элемента и помещение его в начало или конец упорядоченного списка. Сложность алгоритма: O(n\ :sup:`2`\).
* Сортировка Шелла (Shell sort). сложность алгоритма: O(n log\ :sub:`2`\(n)); улучшение сортировки вставками.
* Сортировка расчёской (Comb sort) — сложность алгоритма: O(n log(n)).
* Пирамидальная сортировка (сортировка кучи, Heapsort) — сложность алгоритма: O(n log(n)); превращаем список в кучу, берём наибольший элемент и добавляем его в конец списка.
* Плавная сортировка (Smoothsort) — сложность алгоритма: O(n log(n)).
* Быстрая сортировка (Quicksort), в варианте с минимальными затратами памяти — сложность алгоритма: O(n log(n)) — среднее время, O(n\ :sup:`2`\) — худший случай; широко известен как быстрейший из известных для упорядочения больших случайных списков; с разбиением исходного набора данных на две половины так, что любой элемент первой половины упорядочен относительно любого элемента второй половины; затем алгоритм применяется рекурсивно к каждой половине. При использовании O(n) дополнительной памяти, можно сделать сортировку устойчивой.
* Интроспективная сортировка (Introsort) — сложность алгоритма: O(n log(n)), сочетание быстрой и пирамидальной сортировки. Пирамидальная сортировка применяется в случае, если глубина рекурсии превышает log(n).
* Терпеливая сортировка (Patience sorting) — сложность алгоритма: O(n log(n)) — наихудший случай, требует дополнительно O(n) памяти, также находит самую длинную увеличивающуюся подпоследовательность.
* Stooge sort — рекурсивный алгоритм сортировки с временной сложностью O(n\ :sup:`2.71`\).

Упражнение №1
-------------

Напишите программу, сортирующую последовательность чисел {31, 30, 69, 8, 74, 11, 40, 7, 48, 26, 65, 43, 73, 89, 44, 67, 41, 95, 55, 68} любым из перечисленных выше алгоритмов.
 
Двоичный поиск в массиве
========================

Целочисленный двоичный поиск (бинарный поиск) (англ. binary search) — алгоритм поиска объекта по заданному признаку в множестве объектов, упорядоченных по тому же самому признаку, работающий за логарифмическое время.
Двоичный поиск заключается в том, что на каждом шаге множество объектов делится на две части и в работе остаётся та часть множества, где находится искомый объект. Или же, в зависимости от постановки задачи, мы можем остановить процесс, когда будет найден первый или же последний индекс вхождения элемента. Последнее условие — это левосторонний/правосторонний двоичный поиск.

Алгоритм двоичного поиска
-------------------------

Идея поиска заключается в том, чтобы брать элемент посередине, между границами, и сравнивать его с искомым. Если искомое больше(в случае правостороннего — не меньше), чем элемент сравнения, то сужаем область поиска так, чтобы новая левая граница была равна индексу середины предыдущей области. В противном случае присваиваем это значение правой границе. Проделываем эту процедуру до тех пор, пока правая граница больше левой более чем на 1. В случае правостороннего бинарного поиска ответом будет индекс l, а в случае левостороннего — r.

Пример
-------

Задан отсортированный массив [1, 2, 2, 2, 2, 3, 5, 8, 9, 11], x = 2. Правосторонний поиск двойки выдаст в результате 4, в то время как левосторонний выдаст 1 (нумерация с нуля). Отсюда следует, что количество подряд идущих двоек равно длине отрезка [1;4], то есть 4. Если искомого элемента в массиве нет, то правосторонний поиск выдаст минимальный элемент, больший искомого, а левосторонний наоборот, максимальный элемент, меньший искомого. Алгорим можно модифицировать, чтобы при отсуствии искомного значения выдавалось специальное число (например -1).       


.. code-block:: c

    int binary_search (int arr[], int size, int key)
    {
        int mid = 0;
        int left = 0;
        int right = size;
        while (1)
        {
            mid = (left + right) / 2;
            
            if (key < arr[mid])       // если искомое меньше значения в ячейке
                right = mid - 1;      // смещаем правую границу поиска
            else if (key > arr[mid])  // если искомое больше значения в ячейке
                left = mid + 1;       // смещаем левую границу поиска
            else                      // иначе (значения равны)
                return mid;           // функция возвращает индекс ячейки
     
            if (left > right)         // если границы сомкнулись 
                return -1;
        }
    }


Математические функции языка C++
================================

Для использования математических функций в языке C++ необходимо включение в программу заголовка <cmath>. Этот заголовок не только объявляет математические функции, но и определяет макрос HUGE_VAL. Макросы EDOM и ERANGE также используются математическими функциями. Эти макросы определены в заголовке <cerrno>. Если аргумент математической функции не попадает в допустимую область значений функцией возвращается некоторое значение, зависящее от конкретной реализации, а встроенная глобальная целая переменная errno устанавливается равной значению EDOM. Если функция генерирует результат, который слишком велик для возможностей представления, происходит переполнение. В этом случае функция возвращает значение HUGE_VAL, а переменная errno устанавливается равной значению ERANGE, сигнализирующему об ошибке диапазона. Если аргумент функции лежит за границей допустимых значений, то функция возвращает нуль и устанавливает переменную errno равной значению ERANGE.
Все углы задаются в радианах.

* acos - Возвращает значение арккосинуса
* asin - Возвращает значение арксинуса
* atan - Возвращает значение арктангенса
* atan2 - Возвращает значение арктангенса от у/х
* ceil - Возвращает наименьшее целое которое больше или равно заданного значения
* cos - Возвращает значение косинуса
* cosh - Возвращает значение гиперболического косинуса
* exp - Возвращает значение экспоненты
* fabs - Возвращает абсолютное значение
* floor - Возвращает наибольшее целое которое меньше или равно значения заданного аргумента
* fmod - Остаток от деления значений аргументов х/у
* frexp - Разбивает число на мантиссу и экспоненту
* ldexp - Возвращает значение выражения num*2^ехр
* log - Возвращает значение натурального логарифма
* log10 - Возвращает значение логарифма по основанию 10
* modf - Разбивает аргумент на целую и дробную части
* pow - Возвращает значение аргумента которое возведено в заданную степень
* sin - Возвращает значение синуса
* sinh - Возвращает значение гиперболического синуса
* sqrt - Возвращает значение квадратного корня
* tan - Возвращает значение тангенса
* tanh - Возвращает значение гиперболического тангенса

Стандартная библиотека
======================

Ни в С, ни в C++ нет ключевых слов, обеспечивающих ввод-вывод, обрабатывающих строки, выполняющих различные математические вычисления или какие-нибудь другие полезные процедуры. Все эти операции выполняются за счет использования набора библиотечных функций, поддерживаемых компилятором. Существует два основных вида библиотек: библиотека С-функций, которая поддерживается всеми компиляторами С и C++, и библиотека классов C++, которая применима только для языка C++. 
Прежде чем программа сможет использовать какую-нибудь библиотеку функций, она должна включить соответствующий заголовочный файл.
В современной спецификации для языка C++ заголовки указываются с использованием стандартных имен заголовков, которые не имеют расширения .h (т.е. заголовки C++ не означают имена файлов). Это просто стандартные идентификаторы, которые компилятор может обрабатывать так, как считает нужным (т.е. заголовок может быть преобразован в имя файла, но это вовсе необязательно). С++-заголовки приведены ниже. Указанная в скобках аббревиатура STL означает прямую или косвенную связь данного заголовка со стандартной библиотекой шаблонов (Standard Template Library).


+-----------------+---------------------------------------------------------------------------------+ 
| Заголовок C++   | Функционал                                                                      |
+=================+=================================================================================+
| <algorithm>     | Различные операции на контейнерах (STL)                                         |
+-----------------+---------------------------------------------------------------------------------+ 
| <bitset>        | Битовые множества (STL)                                                         |
+-----------------+---------------------------------------------------------------------------------+ 
| <complex>       | Комплексные числа                                                               |
+-----------------+---------------------------------------------------------------------------------+ 
| <deque>         | Двухсторонние очереди (STL)                                                     |
+-----------------+---------------------------------------------------------------------------------+ 
| <exception>     | Обработка исключительных ситуаций                                               |
+-----------------+---------------------------------------------------------------------------------+ 
| <fstream>       | Работа с файловыми потоками для чтения и записи в файл                          |
+-----------------+---------------------------------------------------------------------------------+ 
| <functional>    | Различные объекты-функции (STL)                                                 |
+-----------------+---------------------------------------------------------------------------------+ 
| <iomanip>       | Манипуляторы ввода-вывода                                                       |
+-----------------+---------------------------------------------------------------------------------+ 
| <ios>           | Классы ввода-вывода нижнего уровня                                              |
+-----------------+---------------------------------------------------------------------------------+ 
| <iosfwd>        | Упреждающие объявления для систем ввода-вывода                                  |
+-----------------+---------------------------------------------------------------------------------+ 
| <iostream>      | Стандартные классы ввода-вывода                                                 |
+-----------------+---------------------------------------------------------------------------------+ 
| <istream>       | Обработка входных потоков                                                       |
+-----------------+---------------------------------------------------------------------------------+ 
| <iterator>      | Доступ к содержимому контейнеров (STL)                                          |
+-----------------+---------------------------------------------------------------------------------+ 
| <limits>        | Различные ограничения реализации                                                |
+-----------------+---------------------------------------------------------------------------------+ 
| <list>          | Линейные списки (STL)                                                           |
+-----------------+---------------------------------------------------------------------------------+ 
| <locale>        | Информация, связанная с традициями конкретных стран или географических регионов |
+-----------------+---------------------------------------------------------------------------------+ 
| <map>           | Отображения (ключи и значения) (STL)                                            |
+-----------------+---------------------------------------------------------------------------------+ 
| <memory>        | Распределение памяти с помощью распределителей памяти (STL)                     |
+-----------------+---------------------------------------------------------------------------------+ 
| <new>           | Выделение памяти с помощью оператора new                                        |
+-----------------+---------------------------------------------------------------------------------+ 
| <numeriс>       | Универсальные операции над числами                                              |
+-----------------+---------------------------------------------------------------------------------+ 
| <ostream>       | Обработка выходных потоков                                                      |
+-----------------+---------------------------------------------------------------------------------+ 
| <queue>         | Очереди (STL)                                                                   |
+-----------------+---------------------------------------------------------------------------------+ 
| <set>           | Множества (STL)                                                                 |
+-----------------+---------------------------------------------------------------------------------+ 
| <sstream>       | Обработка строковых потоков                                                     |
+-----------------+---------------------------------------------------------------------------------+ 
| <stack>         | Реализация стека(STL)                                                           |
+-----------------+---------------------------------------------------------------------------------+ 
| <stdexcept>     | Стандартные исключительные ситуации                                             |
+-----------------+---------------------------------------------------------------------------------+ 
| <streambuf>     | Буферизированная обработка потоков                                              |
+-----------------+---------------------------------------------------------------------------------+ 
| <string>        | Стандартный класс string (STL)                                                  |
+-----------------+---------------------------------------------------------------------------------+ 
| <typeinfo>      | Динамическая информация о типе                                                  |
+-----------------+---------------------------------------------------------------------------------+ 
| <utility>       | Шаблоны общего назначения (STL)                                                 |
+-----------------+---------------------------------------------------------------------------------+ 
| <valarray>      | Операции над массивами, содержащими значениях                                   |
+-----------------+---------------------------------------------------------------------------------+ 
| <vector>        | Векторы (динамические массивы) (STL)                                            |
+-----------------+---------------------------------------------------------------------------------+


В стандартном языке C++ вся информация, связанная со стандартной библиотекой, определена в пространстве имен std. Следовательно, для получения прямого доступа к этим элементам после включения нужного заголовка необходимо использовать оператор using.


.. code-block:: c

    using namespace std;

В качестве альтернативного варианта, чтобы не вносить целую библиотеку в глобальное пространство имен, каждый библиотечный идентификатор можно квалифицировать с помощью обозначения std::, например std::cout. Однако в этом случае квалификация каждого имени будет выглядеть весьма громоздко.

Поиск корня методом биссекции
=============================

Метод бисекции или метод деления отрезка пополам — простейший численный метод для решения нелинейных уравнений вида f(x)=0. Предполагается только непрерывность функции f(x). Поиск основывается на теореме о промежуточных значениях.

Алгоритм основан на следующем следствии из теоремы Больцано — Коши:

Пусть функция f(x) непрерывна на отрезке [a, b]. Тогда, если sign(f(a)) != sign(f(b)), тогда на отрезке [a, b] существует такая точка c, для которой f(c) = 0.    
Таким образом, если мы ищем ноль, то на концах отрезка функция должна быть противоположных знаков. Разделим отрезок пополам и возьмём ту из половинок, на концах которой функция по-прежнему принимает значения противоположных знаков. Если значение функции в серединной точке оказалось искомым нулём, то процесс завершается.

Точность вычислений задаётся одним из двух способов:

* На очередном шаге i модуль значения функции \|f(x\ :sub:`i`\)\| < e

* На очередном шаге i размер интревала \|x\ :sub:`i-1`\ - x\ :sub:`i`\| < e

Процедуру следует продолжать до достижения заданной точности.

Для поиска произвольного значения достаточно вычесть из значения функции искомое значение и искать ноль получившейся функции.

Упражнение №2
-------------
Напишите программу, находящую корень уравнения exp(x)-1=cos(x) на отрезке [0, 1] с точностью 0.001, методом биссекции.
