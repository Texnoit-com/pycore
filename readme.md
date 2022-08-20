## **Ядро планеты Python**

## Структуры данных

### Массив <a name="basicarray"></a>  

Массив может быть одномерным, многомерным или массивом массивов.  
Количество измерений и длина каждого из измерений задаются, когда создается экземпляр массива. Эти значения нельзя изменить во время существования экземпляра.  
Все массивы реализуют _IList_ и _IEnumerable_. Одномерные массивы также реализуют _IList<T>_ и _IEnumerable<T>_.  

Для типов значений элементы массива инициализируются со значением по умолчанию.
Все ссылочные типы имеют значение null.  
Для типов nullable параметр HasValue имеет значение false, а для элементов будет установлено значение null.  

### Динамический массив <a name="basicdarray"></a>  

В C# это List\<T>. Реализует ICollection\<T>, IEnumerable\<T>, IList\<T>, IReadOnlyCollection\<T>, IReadOnlyList\<T>, ICollection, IEnumerable, IList.  

List\<T> реализован на базе массива, размер которого динамически увеличивается по мере необходимости.  

Имеет методы BinarySearch и Sort.  

### Односвязный список <a name="basicslist"></a>  

Односвязный список представляет набор связанных узлов, каждый из которых хранит собственно данные и ссылку на следующий узел. В практике малоприменим, но его любят использовать интервьюеры на собеседованиях, чтобы кандидат мог блеснуть своими алгоритмическими знаниями.  

### Двусвязный список <a name="basicdlist"></a>  

В C# - [LinkedList\<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.linkedlist-1), гораздо практичнее и удобнее односвязного списка. Реализует ICollection\<T>, IEnumerable\<T>, IReadOnlyCollection\<T>, ICollection, IEnumerable, IDeserializationCallback, ISerializable.  


### Хэш-таблица <a name="basichashtable"></a>  

В C# это HashSet\<T>, Dictionary\<K,V> и OrderedDictionary\<T>. HashSet\<T>  Dictionary\<K,V> имеют [сходное быстродействие](https://stackoverflow.com/questions/2728500/hashsett-versus-dictionaryk-v-w-r-t-searching-time-to-find-if-an-item-exist) и оба сильно выигрывают у List\<T> на операциях поиска нужного значения.  

### Решение проблем вычисления хеша <a name="basichashtableproblem"></a>  

В HashSet\<T> объекты, имеющие одинаковый хеш, будут размещены в одной bucket (корзине). В идеале, для максимального ускорения поиска, желательно иметь один объект в каждой корзине, поэтому функцию вычисления хеша делают [позиционно-зависимой](https://stackoverflow.com/questions/7666509/hash-function-for-string), чтобы, например, хеш от строки "ab" отличался от хеша строки "ba".  

### Бинарное дерево <a name="basicbinarytree"></a>  

Иерархическая структура данных, в которой каждый узел имеет не более двух потомков. В C# это [SortedDictionary\<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.sorteddictionary-2).  

### B-дерево (Би-дерево)<a name="basicbtree"></a>  

Сбалансированное дерево, оптимизированное для доступа к относительно медленным элементам памяти (например, дисковым структурам или индексам баз данных), как ветви, так и листья представляют собой списки (для того, чтобы можно было считать такой список в один проход для дальнейшего разбора в ОЗУ), но обычно различаются по структуре.  

### Красно-черное дерево <a name="basicrbtree"></a>  

Самобалансирующееся двоичное дерево поиска, позволяющее быстро выполнять основные операции дерева поиска: добавление, удаление и поиск узла. В коллекциях C# представлено SortedSet\<T>. Сбалансированность достигается за счёт введения дополнительного признака узла дерева — «цвета». Этот атрибут может принимать одно из двух возможных значений — «чёрный» или «красный». Листовые узлы КЧ деревьев не содержат данных, поэтому не требуют выделения памяти — достаточно просто записать в узле-предке нулевой указатель на потомка.

### АВЛ-дерево <a name="basicavltree"></a>  

В АВЛ-деревьях операции вставки и удаления работают медленнее, чем в красно-черных деревьях (при том же количестве листьев красно-чёрное дерево может быть выше АВЛ-дерева, но не более чем в 1,388 раза). Поиск же в АВЛ-дереве выполняется быстрее (максимальная разница в скорости поиска составляет 39 %).  

### Префиксное дерево <a name="basictrie"></a>  

Структура данных, позволяющая хранить ассоциативный массив, ключами которого являются строки.  

### Таблица выбора структуры данных <a name="basicstructselectiontable"></a>  

В квадратных скобках показан худший случай.

<style>
table th:first-of-type {
    width: 25%;
}
table th:nth-of-type(2) {
    width: 25%;
}
table th:nth-of-type(3) {
    width: 25%;
}
table th:nth-of-type(4) {
    width: 5%;
}
table th:nth-of-type(5) {
    width: 5%;
}
table th:nth-of-type(6) {
    width: 5%;
}
table th:nth-of-type(7) {
    width: 5%;
}
table th:nth-of-type(8) {
    width: 5%;
}
</style>

| Структура | Реализация | Применение | Индекс. | Поиск | Вставка | Удал. | Память |
| :- | :- | :- | :-: | :-: | :-: | :-: | :-: |
| Массив | Array,<br> SortedList (на базе двух массивов для ключей и значений),<br> Stack,<br> Queue,<br> PriorityQueue |  | 1 | n |  |  | n |
| Динамический массив | List\<T> |  | 1 | n | n | n | n |
| Односвязный список | ListDictionary | Не рекомендуется для применения, как и другие коллекции из пространства имен [System.Collections.Specialized](https://docs.microsoft.com/en-us/dotnet/api/system.collections.specialized) | n | n | 1 | 1 | n |
| Двусвязный список | [LinkedList\<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.linkedlist-1) |  | n | n | 1 | 1 | n |
| Хэш таблица | HashSet\<T>, Dictionary\<K,V>, [OrderedDictionary\<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.specialized.ordereddictionary) |  |  | 1<br> [n] | 1<br> [n] | 1<br> [n] | n |
| Бинарное дерево | [SortedDictionary\<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.sorteddictionary-2) |  | logn<br> [n] | logn<br> [n] | logn<br> [n] | logn<br> [n] | n |
| [B-дерево](https://en.wikipedia.org/wiki/B-tree)<br> (Би-дерево) |  | Для памяти с медленным доступом | logn | logn | logn | logn | n |
| КЧ дерево | SortedSet\<T> |  | logn | logn | logn | logn | n |
| АВЛ дерево |  |  | logn | logn | logn | logn | n |
| Префиксное дерево |  | T9,<br> алгоритм [Ахо–Корасик](https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm),<br> алгоритм [LZW](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch) |  | key | key | key |  |

### List (список)


```python
a = []  # Создаем пустой список

a: list[int] = [10, 20]
b: list[int] = [30, 40]
a.append(50)  # Добавляем значение в конец списка
b.insert(2, 60)  # Вставляем значение по определенному индексу
print(a, b)

a += b
print(f"Add: {a}")

a.reverse()
b = list(reversed(a))  # reversed() возвращает итератор, а не список
print(f"Reverse: {a}, {b}")

b = sorted(a)  # Возвращает новый отсортированный список
a.sort()  # Модифицирует исходный список и не возвращает ничего
print(f"Sort: {a}, {b}")

s: str = "A whole string"
list_of_chars: list = list(s)
print(list_of_chars)
list_of_words: list = s.split()
print(list_of_words)

i: int = list_of_chars.index("w")  # Возвращает индекс первого вхождения искомого элемента или вызывает исключение ValueError
print(i)
list_of_chars.remove("w")  # Удаляет первое вхождение искомого элемента или вызывает исключение ValueError
e = list_of_chars.pop(9)  # Удаляет и возвращает значение, расположенное по индексу. pop() (без аргумента) удалит и вернет последний элемент списка
print(list_of_chars, e)
a.clear()  # Очистка списка
```

    [10, 20, 50] [30, 40, 60]
    Add: [10, 20, 50, 30, 40, 60]
    Reverse: [60, 40, 30, 50, 20, 10], [10, 20, 50, 30, 40, 60]
    Sort: [10, 20, 30, 40, 50, 60], [10, 20, 30, 40, 50, 60]
    ['A', ' ', 'w', 'h', 'o', 'l', 'e', ' ', 's', 't', 'r', 'i', 'n', 'g']
    ['A', 'whole', 'string']
    2
    ['A', ' ', 'h', 'o', 'l', 'e', ' ', 's', 't', 'i', 'n', 'g'] r
    

### Dictionary (словарь)


```python
d = {}  # Создаем пустой словарь

d: dict[str, str] = {"Italy": "Pizza", "US": "Hot-Dog", "China": "Dim Sum"}  # Непосредственное создание словаря

k = ["Italy", "US", "China"]
v = ["Pizza", "Hot-Dog", "Dim Sum"]
d = dict(zip(k, v))  # Создание словаря из двух коллекций при помощи zip

k = d.keys()  # Коллекция ключей. Отражает изменения в основном словаре
v = d.values()  # Коллекция значений. Тоже отражает изменения в основном словаре
k_v = d.items()  # Кортежи ключ-значение, которые тоже отражают изменения в основном словаре

print(d)
print(k)
print(v)
print(k_v)

print(f"Mapping: {k.mapping['Italy']}")

d.update({"China": "Dumplings"})  # Добавление значение. При совпадении ключа старое значение будет перезаписано
print(f"Replace item: {d}")

c = d["China"]  # Читаем значение
print(f"Read item: {c}")

try:
    v = d.pop("Spain")  # Удаляет значение или вызывает исключение KeyError
except KeyError:
    print("Dictionary key doesn't exist")

# Примеры dict comprehension
b = {k: v for k, v in d.items() if "a" in k}  # Вернет новый словарь, отфильтрованный по значению ключа
print(b)

c = {k: v for k, v in d.items() if len(v) >= 7}  # Вернет новый словарь, отфильтрованный по длине значений
print(c)

d.clear() # Очистка списка
```

    {'Italy': 'Pizza', 'US': 'Hot-Dog', 'China': 'Dim Sum'}
    dict_keys(['Italy', 'US', 'China'])
    dict_values(['Pizza', 'Hot-Dog', 'Dim Sum'])
    dict_items([('Italy', 'Pizza'), ('US', 'Hot-Dog'), ('China', 'Dim Sum')])
    Mapping: Pizza
    Replace item: {'Italy': 'Pizza', 'US': 'Hot-Dog', 'China': 'Dumplings'}
    Read item: Dumplings
    Dictionary key doesn't exist
    {'Italy': 'Pizza', 'China': 'Dumplings'}
    {'US': 'Hot-Dog', 'China': 'Dumplings'}
    

### defaultdict

The *defaultdict* will create any items that you try to access (provided of course they do not exist yet) without throws a KeyError.


```python
from collections import defaultdict

dd = defaultdict(int)  # defaultdict
print(dd[10])  # Печать int, будет выведен ноль, значение по умолчанию

dd = {}  # "Обычный" словарь
# print(dd[10])  # вызовет исключение KeyError
```

    0
    

### Counter (счетчик)

A Counter is a dict subclass for counting hashable objects, it is a collection where elements are stored as dictionary keys and their counts are stored as dictionary values.


```python
from collections import Counter

shirts_colors = ["red", "white", "blue", "white", "white", "black", "black"]
c = Counter(shirts_colors)
print(c)

c["blue"] += 1
print(f"After shopping: {c}")

# We can explain how Counter() works with defaultdict():
from collections import defaultdict

d = defaultdict(int)
for shirt in shirts_colors:
    d[shirt] += 1
d["blue"] += 1

print(d)
```

    Counter({'white': 3, 'black': 2, 'red': 1, 'blue': 1})
    After shopping: Counter({'white': 3, 'blue': 2, 'black': 2, 'red': 1})
    defaultdict(<class 'int'>, {'red': 1, 'white': 3, 'blue': 2, 'black': 2})
    

### Set (множество)


```python
big_cities: set["str"] = {"New-York", "Los Angeles", "Ottawa"}
american_cities: set["str"] = {"Chicago", "New-York", "Los Angeles"}

big_cities |= {"Sydney"}  # Add item (or you can use add())
american_cities |= {"Salt Lake City", "Seattle"}  # Add set (or you can use update())

print(big_cities, american_cities)

union_cities: set["str"] = big_cities | american_cities  # Or union()
intersected_cities: set["str"] = big_cities & american_cities  # Or intersection()
dif_cities: set["str"] = big_cities - american_cities  # Or difference()
symdif_cities: set["str"] = big_cities ^ american_cities  # Or symmetric_difference()

issub: bool = big_cities <= union_cities  # Or issubset()
issuper: bool = american_cities >= dif_cities  # Or issuperset()

print(union_cities)
print(intersected_cities)
print(dif_cities)
print(symdif_cities)

print(issub, issuper)

big_cities.add("London")  # Add items

big_cities.remove("Ottawa")  # Removes an item from the set if it is present or raises KeyError
big_cities.discard("Los Angeles")  # Remove an item from the set if it is present without raising KeyError
big_cities.pop()  # Remove and return a random item from the set or raises KeyError
big_cities.clear()  # Removes all items from the set
```

    {'Sydney', 'Ottawa', 'New-York', 'Los Angeles'} {'Chicago', 'Seattle', 'Salt Lake City', 'New-York', 'Los Angeles'}
    {'Ottawa', 'Chicago', 'Seattle', 'Salt Lake City', 'Los Angeles', 'Sydney', 'New-York'}
    {'New-York', 'Los Angeles'}
    {'Sydney', 'Ottawa'}
    {'Sydney', 'Ottawa', 'Chicago', 'Seattle', 'Salt Lake City'}
    True False
    

### Frozen Set

Frozen set is just an immutable and hashable version of a set object. Frozen set can be used as key in Dictionary or as element of another set.


```python
s = frozenset({"New-York", "Los Angeles", "Ottawa"})
```

### Tuple (кортеж)  
Tuple is an immutable and hashable list


```python
a = (2, 3)
b = ("Boson", "Higgs", 1.56e-22)

print(a, b)
```

    (2, 3) ('Boson', 'Higgs', 1.56e-22)
    

### Named Tuple (именованный кортеж)
Subclass of tuple with named elements


```python
from collections import namedtuple

rectangle = namedtuple('rectangle', 'length width')
r = rectangle(length = 1, width = 2)

print(r)
print(r.length)
print(r.width)
print(r._fields)
```

    rectangle(length=1, width=2)
    1
    2
    ('length', 'width')
    

### Enum


```python
from enum import Enum, auto
import random

class Currency(Enum):
    euro = 1
    us_dollar = 2
    yuan = auto()

# If there are no numeric values before auto(), it returns 1, otherwise it returns an increment of the last numeric value

local_currency = Currency.us_dollar  # Returns a member
print(local_currency)

local_currency = Currency["us_dollar"]  # Returns a member or raises KeyError
print(local_currency)

local_currency = Currency(2)  # Returns a member or raises ValueError
print(local_currency)

print(local_currency.name)
print(local_currency.value)

list_of_members = list(Currency)
member_names    = [e.name for e in Currency]
member_values   = [e.value for e in Currency]
random_member   = random.choice(list(Currency))

print(list_of_members, "\n",
      member_names, "\n",
      member_values, "\n",
      random_member)
```

    Currency.us_dollar
    Currency.us_dollar
    Currency.us_dollar
    us_dollar
    2
    [<Currency.euro: 1>, <Currency.us_dollar: 2>, <Currency.yuan: 3>] 
     ['euro', 'us_dollar', 'yuan'] 
     [1, 2, 3] 
     Currency.euro
    

### Range


```python

r1: range = range(11)  # Creates a sequence of numbers from 0 to 10
r2: range = range(5, 21) # Creates a sequence of numbers from 5 to 20
r3: range = range(20, 9, -2)  # Creates a sequence of numbers from 20 to 10 with step 2

print("To exclusive: ", end="")
for i in r1:
  print(f"{i} ", end="")

print("\nFrom inclusive to exclusive: ", end="")
for i in r2:
  print(f"{i} ", end="")

print("\nFrom inclusive to exclusive with step: ", end="")
for i in r3:
  print(f"{i} ", end="")

print(f"\nFrom = {r3.start}")
print(f"To = {r3.stop}")
```

    To exclusive: 0 1 2 3 4 5 6 7 8 9 10 
    From inclusive to exclusive: 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 
    From inclusive to exclusive with step: 20 18 16 14 12 10 
    From = 20
    To = 9
    

### Dataclass  
Decorator that automatically generates init(), repr() and eq() special methods


```python
from dataclasses import dataclass
from decimal import *
from datetime import datetime

@dataclass
class Transaction:
    value: Decimal
    issuer: str = "Default Bank"
    dt: datetime = datetime.now()

t1 = Transaction(value=1000_000, issuer="Deutsche Bank", dt = datetime(2022, 1, 1, 12))
t2 = Transaction(1000)

print(t1)
print(t2)
```

    Transaction(value=1000000, issuer='Deutsche Bank', dt=datetime.datetime(2022, 1, 1, 12, 0))
    Transaction(value=1000, issuer='Default Bank', dt=datetime.datetime(2022, 8, 20, 16, 2, 23, 327826))
    

Objects can be made immutable with *frozen=True*.


```python
from dataclasses import dataclass

@dataclass(frozen=True)
class User:
    name: str
    account: int

```

### Deque

A thread-safe list with efficient appends and pops from either side.


```python
from collections import deque
d = deque([1, 2, 3, 4], maxlen=1000)

d.append(5)  # Add element to the right side of the deque
d.appendleft(0)  # Add element to the left side of the deque by appending elements from iterable

d.extend([6, 7])  # Extend the right side of the deque
d.extendleft([-1, -2])  # Extend the left side of the deque
print(d)

a = d.pop()  # Remove and return an element from the right side of the deque. Can raise an IndexError
b = d.popleft()  # Remove and return an element from the left side of the deque. Can raise an IndexError
print(a, b)
print(d)
```

    deque([-2, -1, 0, 1, 2, 3, 4, 5, 6, 7], maxlen=1000)
    7 -2
    deque([-1, 0, 1, 2, 3, 4, 5, 6], maxlen=1000)
    

### Queue

The queue module implements multi-producer, multi-consumer FIFO queues. It is especially useful in threaded programming when information must be exchanged safely between multiple threads. For LIFO queue use LifoQueue. For a priority queue use PriorityQueue.


```python
from queue import Queue
q = Queue(maxsize=1000)

q.put("eat", block=True, timeout=10)  # Put an element to the queue with 10 seconds timeuot, block if necessary until a free slot is available
q.put("sleep")  # Default values block=True, timeout=None
q.put("code")
q.put_nowait("repeat")  # Equivalent to put("repeat", block=False). Put an element on the queue if a free slot is immediately available, else raise the queue.Full exception
print(q.queue)

a = q.get(block=True, timeout=10)  # Remove and return an item from the queue
b = q.get()  # Default values block=True, timeout=None
c = q.get_nowait()  # Equivalent to get(False)
print(a, b, c, q.queue)
```

    deque(['eat', 'sleep', 'code', 'repeat'])
    eat sleep code deque(['repeat'])
    

### Array (массив)  
Object type that can only hold numbers of a predefined type.


```python
from array import array

a1 = array("l", [1, 2, 3, -4])  # Array from collection of numbers
a2 = array("b", b"1234567890")  # Array from bytes object
b = bytes(a2)

print(a1)
print(a2[0])
print(b)

print(a1.index(-4))  # Returns an index of a member or raises ValueError
```

    array('l', [1, 2, 3, -4])
    49
    b'1234567890'
    3
    

### Generator (генератор)

Any function that contains a yield statement returns a generator.


```python
def count(start, step):
    current = start
    while True:
        yield current
        current += step

c = count(100, 10)

print(next(c))
print(next(c))
print(next(c))
```

    100
    110
    120
    

## String (строка)


```python
se: str = ""  # Empty string
si: str = str(12345)  # Creates the string from int
sj: str = " ".join(["Follow", "the", "white", "rabbit"])  # Joins items using string as a separator
print(f"Joined string: {sj}")

is_contains: bool = "rabbit" in sj  # Checks if string contains a substring
is_startswith = sj.startswith("Foll")
is_endswith = sj.endswith("bbit")
print(f"is_contains = {is_contains}, is_startswith = {is_startswith}, is_endswith = {is_endswith}")

sr: str  = sj.replace("rabbit", "sheep")  # Replaces substrings. Also you can use times:  sr: str  = sj.replace("rabbit", "sheep", times)
print(f"After replace: {sr}")

i1 = sr.find("rabbit")  # Returns start index of the first match or -1. Also rfind()
i2 = sr.index("sheep")  #  Returns start index of the first match or raises ValueError. Also rindex()   
print(f"Start index of 'rabbit' is {i1}, start index of 'sheep' is {i2}")

d = str.maketrans({"a" : "x", "b" : "y", "c" : "z"})
st  = "abc".translate(d)
print(f"Translate string: {st}")

sr = sj[::-1]  # Reverse (Explanation: stackoverflow.com/questions/931092/reverse-a-string-in-python)
print(f"Reverse string: {sr}")
```

    Joined string: Follow the white rabbit
    is_contains = True, is_startswith = True, is_endswith = True
    After replace: Follow the white sheep
    Start index of 'rabbit' is -1, start index of 'sheep' is 17
    Translate string: xyz
    Reverse string: tibbar etihw eht wolloF
    

### lower(), upper(), capitalize() и title()


```python
s: str = "camelCase string"

print(s.lower())
print(s.upper())
print(s.capitalize())
print(s.title())
```

    camelcase string
    CAMELCASE STRING
    Camelcase string
    Camelcase String
    

### Property Methods

```text
+---------------+----------+----------+----------+----------+----------+
|               | [ !#$%…] | [a-zA-Z] |  [½¼¾]   |  [²³¹]   |  [0-9]   |
+---------------+----------+----------+----------+----------+----------+
| isprintable() |   yes    |   yes    |   yes    |   yes    |   yes    |
| isalnum()     |          |   yes    |   yes    |   yes    |   yes    |
| isnumeric()   |          |          |   yes    |   yes    |   yes    |
| isdigit()     |          |          |          |   yes    |   yes    |
| isdecimal()   |          |          |          |          |   yes    |
+---------------+----------+----------+----------+----------+----------+
```

*isspace()* checks for *[ \t\n\r\f\v\x1c-\x1f\x85…]*

### strip()


```python
s: str = "  ~~##A big blahblahblah##~~  "

s = s.strip()  # Strips all whitespace characters from both ends
print(s)

s = s.strip("~#")  # Strips all passed characters from both ends
print(s)

s = s.lstrip(" A")  # Strips all passed characters from left end
print(s)

s = s.rstrip("habl")  # Strips all passed characters from right end
print(s)

```

    ~~##A big blahblahblah##~~
    A big blahblahblah
    big blahblahblah
    big 
    

### split()


```python
s1: str = "Follow the white rabbit, Neo"

c1 = s1.split()  # Splits on one or more whitespace characters
print(c1)

c2 = s1.split(sep=", ", maxsplit=1)  # Splits on "sep" str at most "maxsplit" times
print(c2)

s2: str = "Beware the Jabberwock, my son!\n The jaws that bite, the claws that catch!"

c3 = s2.splitlines(keepends=False)  # On [\n\r\f\v\x1c-\x1e\x85\u2028\u2029] and \r\n.
print(c3)

# split() vs rsplit()

c4 = s2.split(maxsplit=2)
c5 = s2.rsplit(maxsplit=2)

print(c4, c5)
```

    ['Follow', 'the', 'white', 'rabbit,', 'Neo']
    ['Follow the white rabbit', 'Neo']
    ['Beware the Jabberwock, my son!', ' The jaws that bite, the claws that catch!']
    ['Beware', 'the', 'Jabberwock, my son!\n The jaws that bite, the claws that catch!'] ['Beware the Jabberwock, my son!\n The jaws that bite, the claws', 'that', 'catch!']
    

### ord(), chr()


```python
s1: str = "abcABC!"

for ch in s1:
    print(f"{ch} -> {ord(ch)}")  # Returns an integer representing the Unicode character

nums = [72, 101, 108, 108, 111, 33]

for num in nums:
    print(f"{num} -> {chr(num)}")
```

    a -> 97
    b -> 98
    c -> 99
    A -> 65
    B -> 66
    C -> 67
    ! -> 33
    72 -> H
    101 -> e
    108 -> l
    108 -> l
    111 -> o
    33 -> !
    

## Regex

Argument flags=re.IGNORECASE can be used with all functions


```python
import re

s1: str = "123 abc ABC 456"

m1 = re.search("[aA]", s1)  # Searches for first occurrence of the pattern; search() return None if it can't find a match
print(m1)
print(m1.group(0))

m2 = re.match("[aA]", s1)  # Searches at the beginning of the text; match() return None if it can't find a match
print(m2)

c1: list = re.findall("[aA]", s1)  # Returns all occurrences as strings
print(c1)

def replacer(s):  # replacer() can be a function that accepts a match object and returns a string
    return chr(ord(s[0]) + 1)  # Next symbol in alphabet

s2 = re.sub("\w", replacer, s1)  # Substitutes all occurrences with 'replacer'
print(s2)

c2 = re.split("\d", s1)
print(c2)

iter = re.finditer("\D", s1)  # Returns all occurrences as match objects

for ch in iter:
    print(ch.group(0), end= "")
```

    <re.Match object; span=(4, 5), match='a'>
    a
    None
    ['a', 'A']
    234 bcd BCD 567
    ['', '', '', ' abc ABC ', '', '', '']
     abc ABC 

### Match Object


```python
import re

m3 = re.match(r"(\w+) (\w+)", "John Connor, leader of the Resistance")

s3: str = m3.group(0)  # Returns the whole match
s4: str = m3.group(1)  # Returns part in the first bracket
t1: tuple = m3.groups()  # Returns all bracketed parts
start: int = m3.start()  # Returns start index of the match
end: int = m3.end()  # Returns exclusive end index of the match
t2: tuple[int, int] = m3.span()  # Return the 2-tuple (start, end)

print (f"{s3}\n {s4}\n {t1}\n {start}\n {end}\n {t2}\n")
```

    John Connor
     John
     ('John', 'Connor')
     0
     11
     (0, 11)
    
    

### JSON

Human-readable text format to store and transmit data objects.


```python
import json

d: dict = {1: "Lemon", 2: "Apple", 3: "Banana!"}

object_as_string: str = json.dumps(d, indent=2)
print(object_as_string)

restored_object = json.loads(object_as_string)

# Write object to JSON file
with open("1.json", 'w', encoding='utf-8') as file:
    json.dump(d, file, indent=2)

# Read object from JSON file
with open("1.json", encoding='utf-8') as file:
    restored_from_file = json.load(file)
    
print(restored_from_file)

```

    {
      "1": "Lemon",
      "2": "Apple",
      "3": "Banana!"
    }
    {'1': 'Lemon', '2': 'Apple', '3': 'Banana!'}
    

### Pickle

Бинарный формат для хранения и транспортировки структур данных.


```python
import pickle

d: dict = {1: "Lemon", 2: "Apple", 3: "Banana!"}

# Запись объекта в бинарный файл
with open("1.bin", "wb") as file:
    pickle.dump(d, file)

# Чтение объекта из файла
with open("1.bin", "rb") as file:
    restored_from_file = pickle.load(file)

print(restored_from_file)
```

    {1: 'Lemon', 2: 'Apple', 3: 'Banana!'}
    

### Protocol Buffers!!!  
Если вы хотите передавать и хранить данные, используя универсальную структуру, одинаково хорошо понимаемую всеми языками программирования (как JSON) и занимающую мало места (как Pickle), то можно посмотреть в сторону Protocol Buffers ([Wikipedia](https://en.wikipedia.org/wiki/Protocol_Buffers), [примеры для Python](https://developers.google.com/protocol-buffers/docs/pythontutorial)). Есть еще альтернативы, например, [FlatBuffers](https://google.github.io/flatbuffers/), [Apache Avro](https://avro.apache.org/) или [Thrift](https://thrift.apache.org/).

### Bytes

Bytes object is an immutable sequence of single bytes. Mutable version is called bytearray.


```python

### Encode
b1 = bytes([1, 2, 3, 4])  # Ints must be in range from 0 to 255
b2 = "The String".encode('utf-8')
b3 = (-1024).to_bytes(4, byteorder='big', signed=True)  # byteorder="big"/"little"/"sys.byteorder", signed=False/True
b4 = bytes.fromhex('FEADCA')  # Hex pairs can be separated by spaces
b5 = bytes(range(10,30,2))

print(b1, b2, b3, b4, b5)

### Decode
c: list = list(b"\xfc\x00\x00\x00\x00\x01")  # Returns ints in range from 0 to 255
s: str = b'The String'.decode("utf-8")
b: int = int.from_bytes(b"\xfc\x00", byteorder='big', signed=False)  # byteorder="big"/"little"/"sys.byteorder", signed=False/True
s2: str = b"\xfc\x00\x00\x00\x00\x01".hex(" ")  # Returns a string of hexadecimal pairs, hex pairs can be separated by spaces

print(c, s, b, s2)

with open("1.bin", "wb") as file:  # Write bytes to file
    file.write(b1)

with open("1.bin", "rb") as file:  # Read bytes from file
    b6 = file.read()

print(b6)
```

    b'\x01\x02\x03\x04' b'The String' b'\xff\xff\xfc\x00' b'\xfe\xad\xca' b'\n\x0c\x0e\x10\x12\x14\x16\x18\x1a\x1c'
    [252, 0, 0, 0, 0, 1] The String 64512 fc 00 00 00 00 01
    b'\x01\x02\x03\x04'
    

### Struct

Module that performs conversions between a sequence of numbers and a bytes object. System’s type sizes and byte order are used by default.


```python
from struct import pack, unpack, iter_unpack

b = pack(">hhll", 1, 2, 3, 4)
print(b)

t = unpack(">hhll", b)
print(t)

i = pack("ii", 1, 2) * 5
print(i)

print(list(iter_unpack('ii', i)))
```

    b'\x00\x01\x00\x02\x00\x00\x00\x03\x00\x00\x00\x04'
    (1, 2, 3, 4)
    b'\x01\x00\x00\x00\x02\x00\x00\x00\x01\x00\x00\x00\x02\x00\x00\x00\x01\x00\x00\x00\x02\x00\x00\x00\x01\x00\x00\x00\x02\x00\x00\x00\x01\x00\x00\x00\x02\x00\x00\x00'
    [(1, 2), (1, 2), (1, 2), (1, 2), (1, 2)]
    

## Datetime

Module *datetime* provides *date*, *time*, *datetime* and *timedelta*. All are immutable and hashable

### Constructors


```python
from datetime import date, time, datetime, timedelta

d: date = date(year=1964, month=9, day=2)
t: time  = time(hour=12, minute=30, second=0, microsecond=0, tzinfo=None, fold=0)
dt: datetime = datetime(year=1964, month=9, day=2, hour=10, minute=30, second=0)
td: timedelta = timedelta(weeks=1, days=1, hours=12, minutes=13, seconds=14)

print (f"{d}\n {t}\n {dt}\n {td}")
```

    1964-09-02
     12:30:00
     1964-09-02 10:30:00
     8 days, 12:13:14
    

### Now


```python
from datetime import date, time, datetime
import pytz

d: date  = date.today()
dt1: datetime = datetime.today()
dt2: datetime = datetime.utcnow()
dt3: datetime = datetime.now(pytz.timezone('US/Pacific'))

print (f"{d}\n {dt1}\n {dt2}\n {dt3}")

```

    2022-08-20
     2022-08-20 16:02:24.484302
     2022-08-20 11:02:24.484301
     2022-08-20 04:02:24.484301-07:00
    

### Timezone


```python
from datetime import date, time, datetime, timedelta, tzinfo
from dateutil.tz import UTC, tzlocal, gettz, datetime_exists, resolve_imaginary

tz1: tzinfo = UTC  # UTC timezone

tz2: tzinfo = tzlocal()  # Local timezone
tz3: tzinfo = gettz()  # Local timezone

tz4: tzinfo = gettz("America/Chicago")  # "Asia/Kolkata" etc. See full list at en.wikipedia.org/wiki/List_of_tz_database_time_zones

local_dt = datetime.today()
utc_dt = local_dt.astimezone(UTC)  # Convert local datetime to UTC datetime

print (f"{tz1}\n {tz2}\n {tz3}\n {tz4}\n {local_dt}\n {utc_dt}")
```

    tzutc()
     tzlocal()
     tzlocal()
     tzfile('US/Central')
     2022-08-20 16:02:24.547197
     2022-08-20 11:02:24.547197+00:00
    

### Encode

Python uses the Unix Epoch: "1970-01-01 00:00 UTC"


```python
from datetime import datetime
from dateutil.tz import tzlocal

dt1: datetime = datetime.fromisoformat("2021-10-04 00:05:23.555+00:00")  # Raises ValueError
dt2: datetime = datetime.strptime("21/10/04 17:30", "%d/%m/%y %H:%M")   # Datetime from str, according to format (https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
dt3: datetime = datetime.fromordinal(100000)  # 100000th day after 1.1.0001
dt4: datetime = datetime.fromtimestamp(20_000_000.01)  # Local datetime from seconds since the Epoch

tz2: tzinfo = tzlocal()
dt5: datetime = datetime.fromtimestamp(300_000_000, tz2)  # Aware datetime from seconds since the Epoch

print (f"{dt1}\n {dt2}\n {dt3}\n {dt4}\n {dt5}")
```

    2021-10-04 00:05:23.555000+00:00
     2004-10-21 17:30:00
     0274-10-16 00:00:00
     1970-08-20 16:33:20.010000
     1979-07-05 10:20:00+05:00
    

### Decode


```python
from datetime import datetime

dt1: datetime = datetime.today()

s1: str = dt1.isoformat()
s2: str = dt1.strftime("%d/%m/%y %H:%M")  # Outputting datetime object to string (format: https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
i: int = dt1.toordinal()  # Days since Gregorian NYE 1, ignoring time and tz
a: float = dt1.timestamp()  # Seconds since the Epoch

print (f"{dt1}\n {s1}\n {s2}\n {i}\n {a}")
```

    2022-08-20 16:02:24.687670
     2022-08-20T16:02:24.687670
     20/08/22 16:02
     738387
     1660993344.68767
    

### Arithmetics


```python
from datetime import date, time, datetime, timedelta
from dateutil.tz import UTC, tzlocal, gettz, datetime_exists, resolve_imaginary

d: date  = date.today()
dt1: datetime = datetime.today()
dt2: datetime = datetime(year=1981, month=12, day=2)
td1: timedelta = timedelta(days=5)
td2: timedelta = timedelta(days=1)

d = d + td1  # date = date ± timedelta
dt3 = dt1 - td1  # datetime = datetime ± timedelta

td3 = dt1 - dt2  # timedelta = datetime - datetime

td4 = 10 * td1  # timedelta = const * timedelta
c: float = td1/td2  # timedelta/timedelta

print (f"{d}\n {dt3}\n {td3}\n {td4}\n {c}")
```

    2022-08-25
     2022-08-15 16:02:24.750712
     14871 days, 16:02:24.750712
     50 days, 0:00:00
     5.0
    

## File

### Open

Open the file and return a corresponding file object.


```python
f = open("f.txt", mode='r', encoding="utf-8", newline=None)

print(f.read())
```

    Hello from file!
    


*encoding=None* means that the default encoding is used, which is platform dependent. Best practice is to use *encoding="utf-8"* whenever possible.  
*newline=None* means all different end of line combinations are converted to '\n' on read, while on write all '\n' characters are converted to system's default line separator.  
*newline=""* means no conversions take place, but input is still broken into chunks by readline() and readlines() on every "\n", "\r" and "\r\n".  

### Modes

"r" - Read (default)  
"w" - Write (truncate)  
"x" - Write or fail if the file already exists  
"a" - Append  
"w+" - Read and write (truncate)  
"r+" - Read and write from the start  
"a+" - Read and write from the end  
"t" - Text mode (default)  
"b" - Binary mode (`'br'`, `'bw'`, `'bx'`, …)  

### Exceptions

*FileNotFoundError* can be raised when reading with "r" or "r+".  
*FileExistsError* can be raised when writing with "x".  
*IsADirectoryError* and *PermissionError* can be raised by any.  
*OSError* is the parent class of all listed exceptions.  

### Read from file


```python
with open("f.txt", encoding="utf-8") as f:
    chars = f.read(5)  # Reads chars/bytes or until EOF
    print(chars)

    f.seek(0)  # Moves to the start of the file. Also seek(offset) and seek(±offset, anchor), where anchor is 0 for start, 1 for current position and 2 for end

    lines: list[str] = f.readlines()  # Also readline()
    print(lines)
```

    Hello
    ['Hello from file!']
    

### Write to file


```python
with open("f.txt", "w", encoding="utf-8") as f:
    f.write("Hello from file!")  # Also f.writelines(<collection>)
    # f.flush() for flushes write buffer; runs every 4096/8192 B
```

## Paths


```python
from os import getcwd, path, listdir
from pathlib import Path

s1: str = getcwd()  # Returns the current working directory
print(s1)

s2: str = path.abspath("f.txt")  # Returns absolute path
print(s2)

s3: str = path.basename(s2)  # Returns final component of the path
s4: str = path.dirname(s2)  # Returns path without the final component
t1: tuple = path.splitext(s2)  # Splits on last period of the final component
print(s3, s4, t1)

p = Path(s2)
st = p.stat()
print(st)

b1: bool = p.exists()
b2: bool = p.is_file()
b3: bool = p.is_dir()
print(b1, b2, b3)

c: list = listdir(path=s1)  # Returns filenames located at path
print(c)

s5: str = p.stem  # Returns final component without extension
s6: str  = p.suffix  # Returns final component's extension
t2: tuple = p.parts  # Returns all components as strings
print(s5, s6, t2)
```

    c:\Works\amaargiru\ipycs
    c:\Works\amaargiru\ipycs\f.txt
    f.txt c:\Works\amaargiru\ipycs ('c:\\Works\\amaargiru\\ipycs\\f', '.txt')
    os.stat_result(st_mode=33206, st_ino=25051272927278718, st_dev=3628794147, st_nlink=1, st_uid=0, st_gid=0, st_size=16, st_atime=1658139122, st_mtime=1658139122, st_ctime=1654437943)
    True True False
    ['.git', '.gitignore', '1.bin', '1.json', 'convert_nb_to_md.bat', 'f.txt', 'LICENSE', 'pycallgraph3.png', 'PYCS.ipynb', 'README.md']
    f .txt ('c:\\', 'Works', 'amaargiru', 'ipycs', 'f.txt')
    

## Data querying

### Sum, Count, Min, Max


```python
a: list[int] = [1, 2, 3, 4, 5, 2, 2]

s = sum(a)
print(s)

c = a.count(2)  # Returns number of occurrences
print(c)

mn = min(a)
print(mn)

mx = max(a)
print(mx)
```

    19
    3
    1
    5
    

### List comprehension
An elegant approach to create a new list based on the values of an existing list.


```python
# new_list = [expression for member in iterable (if conditional)]

fruits: list = ["Lemon", "Apple", "Banana", "Kiwi", "Watermelon", "Pear"]

e_fruits = [fruit for fruit in fruits if "e" in fruit]
#                                     ☝ if conditional
print(e_fruits)

upper_fruits = [fruit.upper() for fruit in fruits]
#                     ☝ expression
print(upper_fruits)

# Split a list into equal sized chunks
chunk_len = 2
chunk_fruits = [fruits[i:i + chunk_len] for i in range(0, len(fruits), chunk_len)]
print(chunk_fruits)

```

    ['Lemon', 'Apple', 'Watermelon', 'Pear']
    ['LEMON', 'APPLE', 'BANANA', 'KIWI', 'WATERMELON', 'PEAR']
    [['Lemon', 'Apple'], ['Banana', 'Kiwi'], ['Watermelon', 'Pear']]
    

### Dictionary comprehension
Creating new dictionaries from existing dictionaries and iterables. A dictionary comprehension is very much like a list comprehension, but we get a dictionary at the end of it, so we need to be assigning key value pairs instead of only values.


```python
# new_dict = {expression for member in iterable (if conditional)}

d: dict[str, str] = {"Italy": "Pizza", "US": "Hot-Dog", "China": "Dim Sum", "South Korea": "Kimchi"}  # Create a dictionary

d2: dict[str, str] = {k: v for k, v in d.items() if "i" in v}  ## Select only elements that contain a letter "i" in value
print(d2)

```

    {'Italy': 'Pizza', 'China': 'Dim Sum', 'South Korea': 'Kimchi'}
    

### bisect и бинарный поиск


```python
import bisect

a: list[int] = [12, 6, 8, 19, 1, 33]

a.sort()
print(f"Sorted: {a}")

print(bisect.bisect(a, 19))  # Locate the insertion point for value in a list to maintain sorted order

bisect.insort(a, 15)  # Insert value in a list in sorted order
print(a)

# Binary search

from bisect import bisect_left

def binary_search(a, x, lo=0, hi=None):
    if hi is None:
        hi = len(a)

    pos = bisect_left(a, x, lo, hi)
    return pos if pos != hi and a[pos] == x else -1

print(binary_search(a, 15))
```

    Sorted: [1, 6, 8, 12, 19, 33]
    5
    [1, 6, 8, 12, 15, 19, 33]
    4
    

### Pairwise


```python
import itertools

a = [1, 2, 3, 4, 5]
p = itertools.pairwise(a)  # Returns successive overlapping pairs

print(list(p))
```

    [(1, 2), (2, 3), (3, 4), (4, 5)]
    

### Шифрование и дешифрование


```python
# pip install pycryptodomex
import hashlib

from Cryptodome import Random
from Cryptodome.Cipher import AES
from Cryptodome.Util.Padding import pad
from Cryptodome.Util.Padding import unpad

def encrypt_data(password: str, raw_data: bytes) -> bytes:
    res = bytes()
    try:
        key = hashlib.sha256(password.encode()).digest()
        align_raw = pad(raw_data, AES.block_size)
        iv = Random.new().read(AES.block_size)
        cipher = AES.new(key, AES.MODE_CBC, iv)
        ciphered_data = cipher.encrypt(align_raw)
        res = iv + ciphered_data
    except Exception as e:
        print(f"Encrypt error: {str(e)}")
    return res

def decrypt_data(password: str, encrypted_data: bytes) -> bytes:
    res = bytes()
    try:
        key = hashlib.sha256(password.encode()).digest()
        iv = encrypted_data[:AES.block_size]
        ciphered_data = encrypted_data[AES.block_size:]
        cipher = AES.new(key, AES.MODE_CBC, iv)
        decrypt_data = cipher.decrypt(ciphered_data)
        res = unpad(decrypt_data, AES.block_size)
    except Exception as e:
        print(f"Decrypt error: {str(e)}")
    return res

def encrypt_file(src_file: str, dst_file: str, password: str) -> bool:
    try:
        with open(src_file, "rb") as reader, open(dst_file, "wb") as writer:
            data = reader.read()
            data_enc = encrypt_data(password, data)
            writer.write(data_enc)
            writer.flush()
            print(f"{src_file} encrypted into {dst_file}")
        return True
    except Exception as e:
        print(f"Encrypt_file error: {str(e)}")
        return False

def decrypt_file(src_file: str, dst_file: str, password: str) -> bool:
    try:
        with open(src_file, "rb") as reader, open(dst_file, "wb") as writer:
            data = reader.read()
            data_decrypt = decrypt_data(password, data)
            writer.write(data_decrypt)
            writer.flush()
            print(f"{src_file} decrypted into {dst_file}")
        return True
    except Exception as e:
        print(f"Decrypt file error: {str(e)}")
        return False

if __name__ == '__main__':
    mes: bytes = bytes("A am the Message", "utf-8")
    passw: str = "h3AC3TsU8TECvyCqd5Q5WUag5uXLjct2"
    print(f"Original message: {mes}")

    # Encrypt message
    enc: bytes = encrypt_data(passw, mes)
    print(f"Encrypted message: {enc}")

    # Decrypt message
    dec: bytes = decrypt_data(passw, enc)
    print(f"Decrypted message: {dec}")

```

    Original message: b'A am the Message'
    Encrypted message: b'\xdf\xb9j:\xb8;%\xe9\xae\xfe\xd2 \x81w%"\x88[\x9e*\xd4\x8e\x1b\xa5K)\x19\xce]\xd7\x1e]\xb0\x10\x84\x18\x1fOn\xdd\xe3\xf9}\x92F\xc1DB'
    Decrypted message: b'A am the Message'
    

## Exceptions

### Catching exceptions

Basic Example


```python
a: float = 0
b: float = 0

try:
    b: float = 1/a
except ZeroDivisionError as e:
    print(f"Error: {e}")
```

    Error: division by zero
    

More complex example. Code inside the *else* block will only be executed if *try* block had no exceptions. Code inside the *finally* block will always be executed (unless a signal is received).


```python
import traceback

a: float = 0
b: float = 0

try:
    b: float = 1/a
except ZeroDivisionError as e:
    print(f"Error: {e}")
except ArithmeticError as e:
    print(f"We have a bit more complicated problem: {e}")
except Exception as serious_problem:  # Catch all exceptions
    print(f"I don't really know what is going on: {traceback.print_exception(serious_problem)}")
else:
    print("No errors!")
finally:
    print("This part is always called")
```

    Error: division by zero
    This part is always called
    

### Вызов исключений


```python
from decimal import *

def div(a: Decimal, b: Decimal) -> Decimal:
    if b == 0:
        raise ValueError("Second argument must be non-zero")
    return a/b


try:
    c: Decimal = div(1, 0)
except ValueError:
    print("We have ValueError, as a planned!")
    # raise # We can re-raise exception
```

    We have ValueError, as a planned!
    

### Встроенные исключения
```text
BaseException
 +-- SystemExit                   # Raised by the sys.exit() function
 +-- KeyboardInterrupt            # Raised when the user press the interrupt key (ctrl-c)
 +-- Exception                    # User-defined exceptions should be derived from this class
      +-- ArithmeticError         # Base class for arithmetic errors
      |    +-- ZeroDivisionError  # Dividing by zero
      +-- AttributeError          # Attribute is missing
      +-- EOFError                # Raised by input() when it hits end-of-file condition
      +-- LookupError             # Raised when a look-up on a collection fails
      |    +-- IndexError         # A sequence index is out of range
      |    +-- KeyError           # A dictionary key or set element is missing
      +-- NameError               # An object is missing
      +-- OSError                 # Errors such as “file not found”
      |    +-- FileNotFoundError  # File or directory is requested but doesn't exist
      +-- RuntimeError            # Error that don't fall into other categories
      |    +-- RecursionError     # Maximum recursion depth is exceeded
      +-- StopIteration           # Raised by next() when run on an empty iterator
      +-- TypeError               # An argument is of wrong type
      +-- ValueError              # When an argument is of right type but inappropriate value
           +-- UnicodeError       # Encoding/decoding strings to/from bytes fails
```

### Выход из программы при помощи вызова исключения SystemExit


```python
import sys

# sys.exit()  # Exits with exit code 0 (success)
# sys.exit(777)  # Exits with passed exit code
```

### Исключения, определяемые пользователем


```python
class MyException(Exception):
    pass

raise MyException("My car is broken")
```


    ---------------------------------------------------------------------------

    MyException                               Traceback (most recent call last)

    c:\Works\amaargiru\ipycs\PYCS.ipynb Ячейка 100 in <cell line: 4>()
          <a href='vscode-notebook-cell:/c%3A/Works/amaargiru/ipycs/PYCS.ipynb#Y166sZmlsZQ%3D%3D?line=0'>1</a> class MyException(Exception):
          <a href='vscode-notebook-cell:/c%3A/Works/amaargiru/ipycs/PYCS.ipynb#Y166sZmlsZQ%3D%3D?line=1'>2</a>     pass
    ----> <a href='vscode-notebook-cell:/c%3A/Works/amaargiru/ipycs/PYCS.ipynb#Y166sZmlsZQ%3D%3D?line=3'>4</a> raise MyException("My car is broken")
    

    MyException: My car is broken


### Exception Object

```python
arguments = <name>.args
exc_type = <name>.__class__
filename = <name>.__traceback__.tb_frame.f_code.co_filename
func_name = <name>.__traceback__.tb_frame.f_code.co_name
line = linecache.getline(filename, <name>.__traceback__.tb_lineno)
error_msg = ''.join(traceback.format_exception(exc_type, <name>, <name>.__traceback__))
```

## Математика

### Базовая математика


```python
from math import pi

a: float = pi ** 2  # Or pow(pi, 2)
print(f"Power: {a}")

b: float = round(pi, 2)
print(f"Round: {b}")

c: int = round(256, -2)
print(f"Int round: {c}")

d: float = abs(-pi)
print(f"Abs: {d}")

e: float = abs(10+10j)  # Or e: float = abs(complex(real=10, imag=10))
print(f"Complex abs: {e}")

```

    Power: 9.869604401089358
    Round: 3.14
    Int round: 300
    Abs: 3.141592653589793
    Complex abs: 14.142135623730951
    

### Побитовые операции


```python
a: int = 0b01010101
b: int = 0b10101010

print(f"And: 0b{a&b:08b}")
print(f"Or: 0b{a|b:08b}")
print(f"Xor: 0b{a^b:08b}")
print(f"Left shift: 0b{a << 4:08b}")
print(f"Right shift: 0b{b >> 4:08b}")
print(f"Not: 0b{~a:08b}")
```

    And: 0b00000000
    Or: 0b11111111
    Xor: 0b11111111
    Left shift: 0b10101010000
    Right shift: 0b00001010
    Not: 0b-1010110
    

### Подсчет битов


```python
a: int = 4242
print(f"{a} in binary format: 0b{a:b}")

c = a.bit_count()  # Returns the number of ones in the binary representation of the absolute value of the integer
print(f"Bit count: {c}")
```

    4242 in binary format: 0b1000010010010
    Bit count: 4
    

### Fractions


```python
from fractions import Fraction

f = Fraction("0.2").as_integer_ratio()

print(f)
```

    (1, 5)
    

### Euclidean distance between two points


```python
import math

p1 = (0.22, 1, 12)
p2 = (-0.12, 3, 7)

print(math.dist(p1, p2))
```

    5.39588732276722
    

## Random


```python
import random

rf: float = random.random()  # A float inside [0, 1)
print(f"Single float random: {rf}")

ri: int = random.randint(1, 10)  # An int inside [from, to]
print(f"Single int random: {ri}")

rb = random.randbytes(10)
print(f"Random bytes: {rb}")

rc: str = random.choice(["Alice", "Bob", "Maggie", "Madhuri Dixit"])
print(f"Random choice: {rc}")

rs: str = random.sample([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 5)
print(f"Random list without duplicates: {rs}")

a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"List before shuffle: {a}")
random.shuffle(a)
print(f"List after shuffle: {a}")

```

    Single float random: 0.9024807633898538
    Single int random: 7
    Random bytes: b'>\xe0^\x16PX\xf8E\xf8\x98'
    Random choice: Bob
    Random list without duplicates: [5, 10, 3, 6, 1]
    List before shuffle: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    List after shuffle: [10, 4, 6, 5, 1, 8, 3, 9, 7, 2]
    

## Profiling

### Stopwatch


```python
from time import time
start_time = time()

j: int = 0
for i in range(10_000_000):  # Long operation
    j = i ** 2

duration = time() - start_time
print(f"{duration} seconds")
```

    2.2923033237457275 seconds
    

### High performance


```python
from time import perf_counter
start_time = perf_counter()

j: int = 0
for i in range(10_000_000):  # Long operation
    j = i ** 2

duration = perf_counter() - start_time
print(f"{duration} seconds")
```

    2.3540456001646817 seconds
    

### timeit

Try to avoid a number of common traps for measuring execution times


```python
from timeit import timeit

def long_pow():
    j: int = 0
    for i in range(1000_000):  # Long operation
        j = i ** 2

timeit("long_pow()", number=10, globals=globals(), setup='pass')
```




    1.8552540000528097



### Call Graph

Generates a PNG image of the call graph with highlighted bottlenecks


```python
from pycallgraph3 import PyCallGraph
from pycallgraph3.output import GraphvizOutput

def long_pow():
    j: int = 0
    for i in range(1000_000):  # Long operation
        j = i ** 2

def short_pow():
    j: int = 0
    for i in range(1000):  # Short operation
        j = i ** 2

with PyCallGraph(output=GraphvizOutput()):
    # Code to be profiled
    long_pow()
    short_pow()
    # This will generate a file called pycallgraph3.png
```

<img src="pycallgraph3.png" style="height:400px">

## pytest!!!

## Декораторы!!!

!!!Написать параметризированный декоратор, который печатает время выполнения декорированной функции. Параметр декоратора — точность округления в миллисекундах

## asyncio!!!

## Сборщик мусора!!!

## Источники  
Официальная документация Python [docs.python.org](https://docs.python.org/), включающая [The Python Standard Library](https://docs.python.org/3/library/index.html).  
Весьма подробное руководство (совсем уж базовый синтаксис не включен): [Comprehensive Python Cheatsheet](https://github.com/gto76/python-cheatsheet).  
Руководство с включением базового синтаксиса: [Python Cheatsheet](https://github.com/wilfredinni/python-cheatsheet). Включает практические Jupiter [Notebooks](https://github.com/wilfredinni/python-cheatsheet/tree/master/jupyter_notebooks).  
Сипсок библиотек и фреймворков: [Awesome Python](https://github.com/vinta/awesome-python).  
Около-питоновские практические советы (pip, virtualenv, pyInstaller и т. д.): ["The Hitchhiker’s Guide to Python"](https://github.com/realpython/python-guide).  
Мануал для начинающих дата-сайентистов: [Joel Grus, "Data Science from Scratch"](https://github.com/joelgrus/data-science-from-scratch).  
Руководство для начинающих: ["Python Notes for Professionals"](https://goalkicker.com/PythonBook/).  
Руководство для опытных программистов: ["Python 3 Patterns, Recipes and Idioms"](https://python-3-patterns-idioms-test.readthedocs.io/en/latest/index.html).  

## **Postgre SQL**

Источники!!!

## **Архитектура**

### SOLID <a name="arcchsolid"></a>  

Использование принципов SOLID помогает создавать расширяемые и поддерживаемые системы. Принципы SOLID также можно использовать в качестве ориентиров в процессе рефакторинга кода.  

### SRP <a name="archsolidsrp"></a>  

Single-responsibility principle, принцип единственной ответственности. Предполагает проектирование классов, имеющих только одну причину для изменения, позволяет вести проектирование в направлении, противоположном созданию «[Божественных объектов](https://en.wikipedia.org/wiki/God_object)».  

### OCP <a name="archsolidocp"></a>  

Open–closed principle, принцип открытости/закрытости. Классы должны быть закрыты от изменения (чтобы код, опирающийся наэти классы, не нуждался в обновлении), но открыты для расширения (классу можно добавить новое поведение). Вкратце — хочешь изменить поведение класса — не трогай старый код (не считая рефакторинга, т. е. изменение программы без изменения внешнего поведения), добавь новый.  

### LSP <a name="archsolidlsp"></a>

Liskov Substitution Principle, принцип подстановки Барбары Лисков: поведение наследующих классов должно быть ожидаемым для кода, использующего переменную базового класса.  

### ISP <a name="archsolidisp"></a>  

Interface segregation principle, принцип разделения интерфейса. Клиент интерфейса не должен зависить от неиспользуемых методов. В соответствии с принципом ISP рекомендуется создвать минималистичные интерфейсы, содержащие минимальное количество специфичных методов.  

### DIP <a name="archsoliddip"></a>  

Dependency inversion principle, принцип инверсии зависимостей. Модули верхнего уровня не должны обращаться к модулям нижнего уровня напрямую, между ними должна быть «прокладка» из абстракций (т. е. интерфейсов). Причем абстракции не должны зависить от реализаций, реализации должны звисить от абстракций.  

### KISS <a name="archkiss"></a>  

Keep it simple, stupid — принцип проектирования ПО, в соотвтствии с которым простота системы деклариуется как одна из основополагающих ценностей (иногда даже простота объявляется более важной, чем любые другие свойства системы, см. [Worse is Better](https://en.wikipedia.org/wiki/Worse_is_better) Ричарда Гэбриела), одно из практических приложений «[Бритвы Оккама](https://en.wikipedia.org/wiki/Occam%27s_razor)» — не создавай новых сущностей без крайней необходимости.  

### DRY <a name="archdry"></a>  

Don’t repeat yourself (не повторяйся) — принцип, в соответствии с которым изменение любого элемента системы не требует внесения изменений в другие, логически не связанные элементы. Логически же связанные элементы изменяются предсказуемо и единообразно.  

### YAGNI <a name="archyagni"></a>  

You aren't gonna need it (вам это не понадобится) — если в определенном функционале нет потребности прямо здесь и прямо сейчас — не добавляй его. Этим ты не только отнимешь время, необходимое на разработку и тестирование действительного функционала, но и можешь подложить себе мину замедленного действия на будущее, когда контуры развития системы станут более четкими.  


Источники!!!

## **Алгоритмы**

### FizzBuzz <a name="simplefizzbuzz"></a>  

Почему нужно просить выполнить столь простое задание? Вот подробности — «[FizzBuzz, или почему программисты не умеют программировать](https://habr.com/ru/post/298134/)», если вкратце, то, к сожалению, можно сказать, что и профильное образование, и профильный опыт не уберегают от потери базовых навыков программирования.  

Задание: Напишите программу, которая выводит на экран числа от 1 до 100. При этом вместо чисел, кратных трем, программа должна выводить слово «Fizz», а вместо чисел, кратных пяти — слово «Buzz». Если число кратно и 3, и 5, то программа должна выводить слово «FizzBuzz».  

Самый простой вариант:  
```csharp
const int Max = 100;

for (var i = 1; i <= Max; i++)
{
   if ((i % 3 == 0) && (i % 5 == 0))
   {
      Console.WriteLine("FizzBuzz");
   }
   else if (i % 3 == 0)
   {
      Console.WriteLine("Fizz");
   }
   else if (i % 5 == 0)
   {
      Console.WriteLine("Buzz");
   }
   else
   {
      Console.WriteLine(i);
   }
}
```

или чуточку улучшенный вариант:  

```csharp
const int Max = 100;

for (var i = 1; i <= Max; i++)
{
   if (i % 3 == 0)
   {
      if (i % 5 == 0)
      {
         Console.WriteLine("FizzBuzz");
      }
      else
      {
         Console.WriteLine("Fizz");
      }
   }
   else if (i % 5 == 0)
   {
      Console.WriteLine("Buzz");
   }
   else
   {
      Console.WriteLine(i);
   }
}
```

Больше подробностей про оптимизацию задачи FizzBuzz — «[FizzBuzz по-сениорски](https://habr.com/ru/post/540136/)».  

### Пузырьковая сортировка (BubbleSort) <a name="bubblesort"></a>

Простейший алгоритм, состоит из повторяющихся проходов по сортируемому массиву. В процессе каждого прохода элементы мвссива сравниваются попарно; элементы, не удовлетворяющие условию сортировки, меняются местами.

```cs
internal static class Bubble
{
   internal static int[] Sort(int[] randomArray)
   {
      var arr = (int[])randomArray.Clone();
      var len = arr.Length;

      for (var i = 0; i < len - 1; i++)
      {
         for (var j = 0; j < len - i - 1; j++)
         {
            if (arr[j] > arr[j + 1])
            {
               (arr[j], arr[j + 1]) = (arr[j + 1], arr[j]);
            }
         }
      }

      return arr;
   }
}
```

### Быстрая сортировка (QuickSort) <a name="basicquicksort"></a>  

Идея алгоритма следующая:  
1. Выбирается опорный элемент, это в первом приближении может быть любой из элементов массива.
2. Все элементы массива сравниваются с опорным и переставляются так, чтобы образовать новый массив, состоящий из двух последовательных сегментов - элементы меньшие опорного, равные опорному + большие опорного.
3. Если длина сегментов больше 1, то рекурсивно выполнить сортировку и для них тоже.


```cs
internal static class Quick
{
   internal static int[] Sort(int[] randomArray)
   {
      var arr = (int[])randomArray.Clone();

      QuickSort(arr, 0, arr.Length - 1);

      return arr;
   }

   private static int[] QuickSort(int[] a, int i, int j)
   {
      if (i < j)
      {
         int q = Partition(a, i, j);
         a = QuickSort(a, i, q);
         a = QuickSort(a, q + 1, j);
      }
      return a;
   }

   private static int Partition(int[] a, int p, int r)
   {
      int x = a[p];
      int i = p - 1;
      int j = r + 1;
      while (true)
      {
         do
         {
            j--;
         }
         while (a[j] > x);
         do
         {
            i++;
         }
         while (a[i] < x);
         if (i < j)
         {
            int tmp = a[i];
            a[i] = a[j];
            a[j] = tmp;
         }
         else
         {
            return j;
         }
      }
   }
}
```

### Сортировка слиянием (MergeSort) <a name="basicmergesort"></a>  

Ключевым моментом сортировки слиянием является (как ни странно :) слияние двух массивов. При слиянии массивы сравниваются поэлементо и меньший элемент записывается в результирующий массив; после того, как достигнут конец одного из массивов, в результирующий массив переписывается "хвост" оставшегося массива.  
Совместно со слиянием двух массивов используется рекурсивное разбиение сортируемого массива на сегменты меньшего размера.

```cs
internal static class Merge
{
   internal static int[] Sort(int[] randomArray)
   {
      var sortedArray = (int[])randomArray.Clone();

      MergeSort(sortedArray);

      return sortedArray;
   }

   private static void MergeSort(int[] array)
   {
      var length = array.Length;

      if (length <= 1)
      {
         return;
      }

      var leftSize = length / 2;
      var rightSize = length - leftSize;
      var leftArray = new int[leftSize];
      var rightArray = new int[rightSize];

      Array.Copy(array, 0, leftArray, 0, leftSize);
      Array.Copy(array, leftSize, rightArray, 0, rightSize);

      MergeSort(leftArray);
      MergeSort(rightArray);

      Merges(array, leftArray, rightArray);
   }

   private static void Merges(int[] array, int[] leftArray, int[] rightArray)
   {
      int leftIndex = 0, rightIndex = 0, targetIndex = 0;

      var remaining = leftArray.Length + rightArray.Length;

      while (remaining > 0)
      {
         if (leftIndex >= leftArray.Length)
            array[targetIndex] = rightArray[rightIndex++];
         else if (rightIndex >= rightArray.Length)
            array[targetIndex] = leftArray[leftIndex++];
         else if (leftArray[leftIndex].CompareTo(rightArray[rightIndex]) < 0)
            array[targetIndex] = leftArray[leftIndex++];
         else
            array[targetIndex] = rightArray[rightIndex++];

         targetIndex++;
         remaining--;
      }
   }
}

```

### Пирамидальная сортировка (HeapSort) <a name="basicheapsort"></a>  

Сначала превращаем массив в двоичное дерево за О(n) операций.
Раз за разом преобразуя дерево, получим отсортированный массив.


```cs
internal static class Heap
{
   internal static int[] Sort(int[] randomArray)
   {
      var sortedArray = (int[])randomArray.Clone();

      int n = sortedArray.Length;

      // Build heap (rearrange array)
      for (int i = n / 2 - 1; i >= 0; i--)
         heapify(sortedArray, n, i);

      // One by one extract an element from heap
      for (int i = n - 1; i > 0; i--)
      {
         // Move current root to end
         int temp = sortedArray[0];
         sortedArray[0] = sortedArray[i];
         sortedArray[i] = temp;

         // call max heapify on the reduced heap
         heapify(sortedArray, i, 0);
      }

      return sortedArray;
   }

   private static void heapify(int[] arr, int n, int i)
   {
      int largest = i; // Initialize largest as root
      int l = 2 * i + 1; // left = 2*i + 1
      int r = 2 * i + 2; // right = 2*i + 2

      // If left child is larger than root
      if (l < n && arr[l] > arr[largest])
         largest = l;

      // If right child is larger than largest so far
      if (r < n && arr[r] > arr[largest])
         largest = r;

      // If largest is not root
      if (largest != i)
      {
         int swap = arr[i];
         arr[i] = arr[largest];
         arr[largest] = swap;

         // Recursively heapify the affected sub-tree
         heapify(arr, n, largest);
      }
   }
}
```

### Сортировка вставками (InsertionSort) <a name="basicinsertionsort"></a>  

Каждый новый элемент заносится в выходную последовательность "индивидуально", т. е. каждый раз для добавления нового элемента приходится сдвигать часть массива. Алгоритм медленный, для ускорения вставки можно использовать бинарный поиск.

```cs
internal static class Insertion
{
   internal static int[] Sort(int[] randomArray)
   {
      var sortedArray = (int[])randomArray.Clone();

      int n = sortedArray.Length;
      for (int i = 1; i < n; ++i)
      {
         int key = sortedArray[i];
         int j = i - 1;

         // Move elements of arr[0..i-1],
         // that are greater than key,
         // to one position ahead of
         // their current position
         while (j >= 0 && sortedArray[j] > key)
         {
            sortedArray[j + 1] = sortedArray[j];
            j = j - 1;
         }
         sortedArray[j + 1] = key;
      }

      return sortedArray;
   }
}
```

### Timsort <a name="basictimsort"></a>  

Комбинированный алгоритм сортировки, сочетающий сортировку вставками и сортировку слиянием. Стандарт для Python, Java, Swift

### Introsort <a name="basicintrosort"></a>  

Комбинированный алгоритм сортировки, использует быструю сортировку, плюс, при превышении глубины рекурсии некоторой величины (например, логарифма от числа сортируемых элементов), переключается на пирамидальную сортировку.

### Поразрядная сортировка (RadixSort) <a name="basicradixsort"></a>  

Сортирует только сущности, которые можно разбить на "разряды", имеющие разный вес. Это могут быть, например, целые числа или строки. Соответсвенно, элементы сортируются поразрядно, начиная с разряда, имеющего максимальный вес.

```cs
internal static class Radix
{
   internal static int[] Sort(int[] randomArray)
   {
      var sortedArray = (int[])randomArray.Clone();

      int i, j;
      int[] tmp = new int[sortedArray.Length];
      for (int shift = 31; shift > -1; --shift)
      {
         j = 0;
         for (i = 0; i < sortedArray.Length; ++i)
         {
            bool move = (sortedArray[i] << shift) >= 0;
            if (shift == 0 ? !move : move)
               sortedArray[i - j] = sortedArray[i];
            else
               tmp[j++] = sortedArray[i];
         }
         Array.Copy(tmp, 0, sortedArray, sortedArray.Length - j, j);
      }

      return sortedArray;
   }
}
```



### Таблица сравнения методов сортировки <a name="basicsortingcomparisontable"></a>  
  
<style>
table th:first-of-type {
    width: 35%;
}
table th:nth-of-type(2) {
    width: 35%;
}
table th:nth-of-type(3) {
    width: 5%;
}
table th:nth-of-type(4) {
    width: 5%;
}
table th:nth-of-type(5) {
    width: 5%;
}
table th:nth-of-type(6) {
    width: 5%;
}
table th:nth-of-type(7) {
    width: 5%;
}
table th:nth-of-type(8) {
    width: 5%;
}
</style>

| Сортировка | Преимущество | Best | Avg | Worst | Mem | Stable | Paral |
| :- | :- | :-: | :-: | :-: | :-: | :-: | :-: |
| Пузырьковая<br>(Bubble) | Простейшая реализация | n | n^2 | n^2 | 1 | + | + |
| Быстрая<br>(Quick) | Хорошее быстродействие в среднем случае | n*logn | n*logn | n^2 | logn | +/-<br>(depends) | + |
| Слиянием<br>(Merge) | Может работать со структурами, к которым возможен только последовательный доступ | n*logn | n*logn | n*logn | n<br>(depends) | + | + |
| Пирамидальная<br>(Heap) | Предсказуемая производительность в наихудшем случае, рекомедуется для почти отсортированных данных | n*logn | n*logn | n*logn | 1 | - | - |
| Вставками<br>(Insertion) | Рекомедуется для почти отсортированных данных или для малого количества элементов | n | n^2 | n^2 | 1 | + | - |
| Timsort | Комбинированный алгоритм. Стандарт для Python, Java, Swift | n*logn | n*logn | n*logn | logn | - | - |
| Introsort | Комбинированный алгоритм. Стандарт для .Net | n*logn | n*logn | n*logn | logn | - | - |
| Поразрядная<br>(Radix) | Быстрая сортировка для целых чисел и строк | n*w | n*w | n*w | n+w | +/-<br>(depends) | + |

### Линейный поиск <a name="basiclinearsearch"></a>  

Последовательный поиск элемента в неосортированном массиве

### Бинарный поиск <a name="basicbinarysearch"></a>  

Берется значение из середины отсортрованного массива и сравнивается с искомой величиной. В завистмости от сравнения дальнейший рекурсивный поиск продолжается в середине либо левого, либо правого подмассива.

### Поиск в глубину (DFS) <a name="basicdfs"></a>  

Метод обхода графа. Depth-first search (DFS) можно чуть точнее перевести как "поиск в первую очередь в глубину". Соответственно, рекурсивный алгоритм поиска идет «вглубь» графа, насколько это возможно. Есть нерекурсивные варианты алгоритма, разгружающие стек вызовов.

### Поиск в ширину (BFS) <a name="basicbfs"></a>  

В отличие от предыдущего варианта алгоритм Breadth-first search (BFS) перебирает в первую очередь вершины с одинаковым расстоянием от корня, и только потом идет «вглубь».

### Алгоритм Дейкстры <a name="basicdijkstras"></a>  

Находит кратчайшие пути от одной из вершин графа до всех остальных. Алгоритм работает только для графов без отрицательных рёбер.

### Алгоритм Беллмана-Форда <a name="basicbellmanford"></a>  

Как и алгоритм Дейкстры, находит кратчайшие пути от одной из вершин графа до всех остальных, но, в отличие от первого, позволяет работать с графами с ребрами, имеющими отрицательный вес.

### Таблица сравнения методов поиска <a name="basicfindingcomparisontable"></a>  

| Вид поиска | Структура данных | Avg | Worst | Mem |
| :- | :- | :-: | :-: | :-: |
| Линейный поиск | Массив | n | n | 1 |
| Бинарный поиск | Отсортированный массив | logn | n | 1 |
| Поиск в глубину (DFS) | Граф |  | V+E | V |
| Поиск в ширину (BFS) | Граф |  | V+E | V |
| Алгоритм Дейкстры | Граф | (V+E)logV | (V+E)logV | V |
| Алгоритм Беллмана-Форда | Граф | V*E | V*E | V |

### Матрица смежности <a name="basicgraphadjacencymatrix"></a>  

Квадратная целочисленная матрица размера V*V, в которой значение элемента a{i,j} равно числу рёбер из i-й вершины в j-ю вершину.  
Матрица смежности простого графа (не содержащего петель и кратных рёбер) является бинарной матрицей и содержит нули на главной диагонали.

### Матрица инцидентности <a name="basicgraphincidencematrix"></a>  

Способ представления графа, в которой указываются связи между инцидентными элементами графа (ребрами и вершинами). Столбцы матрицы соответствуют ребрам, строки — вершинам. Ненулевое значение в ячейке матрицы указывает связь между вершиной и ребром (их инцидентность). Если связи между вершиной и ребром нет, то в соответствующую ячейку ставится «0».  
В случае ориентированного графа каждой дуге ставится в соответствующем столбце: 1 в строке вершины x и -1 в строке вершины y.  

### Список смежности <a name="basicgraphadjacencylist"></a>  

Способ представления графа в виде коллекции списков вершин. Каждой вершине графа соответствует список, состоящий из «соседей» этой вершины.  
Варианты:  
• использование хеш-таблицы для ассоциации каждой вершины со списком смежных вершин;
• вершины представлены числовым индексом в массиве, каждая ячейка массива ссылается на однонаправленный связанный список соседних вершин;  
• специальные классы вершин и рёбер, каждый объект вершины содержит ссылку на коллекцию рёбер, каждый объект ребра содержит ссылки на исходящую и входящую вершины.

### Список инцидентности <a name="basicgraphincidencelist"></a>  

Список инцидентности похож на список смежности, только с той разницей, что в i-ой строке записываются номера ребер, инцидентных данной i-ой вершине.

### Сравнение структур представления графов <a name="basicgraphstructcomparison"></a>  

| Метод | Mem | Add V | Add E | Remove V | Remove E | Проверка смежн. V |
| :- | :-: | :-: | :-: | :-: | :-: | :-: |
| Матрица смежности<br>(Adjacency matrix) | V^2 | V^2 | 1 | V^2 | 1 | 1 |
| Матрица инцидентности<br>(Incidence matrix) | V*E | V*E | V*E | V*E | V*E | E |
| Список смежности<br>(Adjacency list) | V+E | 1 | 1 | V+E | E | V |
| Список инцидентности<br>(Incidence list) | V+E | 1 | 1 | E | E | E |

### О-о-о! Большое! <a name="basicbigo"></a>  

Нотация O - характеристика асимптотической сложности алгоритма без учета константы.  

n! >> 2^n >> n^3 >> n^2 >> nlogn >> n >> logn >> 1

### P vs NP <a name="advancedalgorithmspvsnp"></a>  

Задачи класса P — реально вычислимые задачи ([тезис Кобэма](https://en.wikipedia.org/wiki/Cobham%27s_thesis)), решаются за полиномиальное время.  
NP-полные задачи —  не разрешимы за полиномиальное время, но могут быть сведены к задачам разрешимости (да/нет), которые, в свою очередь, решаются за полиномиальное время.

Источники!!!

## **Администрирование/DevOps**

git

### Минимальный вариант <a name="gitflowminimum"></a>

git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"  

Создать новый репозитарий  
в папке git init  
добавить файлы  
git add --all  
git commit  
Добавляем в текстовом файле первой строкой англоязычный заголовок коммита, второй и далее строками можно добавить русскоязычное описание. Сохраняем, закрываем.  
git branch --list список веток  
git branch small-update создает новую ветку, переключение на ветку не выполняется  
git checkout small-update переключается на вновь созданную ветку  
Делаем дополнения файлов в новой ветке  
git checkout master переключаемся на ветку master  
git merge small-update сливаем ветки  
git log --graph --full-history --all --color --pretty=format:"%x1b[31m%h%x09%x1b[32m%d%x1b[0m%x20%s"  

Слияние коммитов:  
git rebase  
squash 

Источники!!!