Python training
==


vv


What is Python ?
--

* _Strongly typed_. You can't add or concat an integer and a string.
* _Dynamically and implicity typed_. Data type are set at runtime².
* _Object oriented_. Everything is an object.
* _Garbaged collected_.


* _Batteries included_, come with comprehensive standard library

* _Open-source software_, by non profit software generation.


vv


History
--
> - v1.0 released late 1980 by **Guido Van Rossum**
> - v2.0 released in Oct 2000, eol set to 2020
> - v3.0 released in Dec 2008, not backward compatible 

### Guido Van Rossum
Benevolent Dictator for Life (BDFL)

- Open source
- Hired by Google to work on Python
- Dropbox

Guido just announced his retreat as BDFL.


vv


What for
--
web
sysadmin
data analysis, statistics, maths
scripting


vv


Who ?
--
* Youtube, ...
* Games...
* GFX...
* Redhat...
* Blackhole...


vv


Why at Presto ?
--
* Easy to learn
* Large library set
* Used for production, automation, and gateway


vv


Why not at Presto ?
--
* Based on Cython (C-compiled)
* You can compile your script to C-executable or dll

>>

Tendance
==
pics...

tyobe...



>>

Ready ?
==


vv


Interactive Shell
--

``python`` with *no argument* is a **console** ...


vv


Code sample
--

```
#  this is a comment...
s = "a string"
i = 42  # the answer
f = 3.14
```

no ";" ;-)

no "{ }" either

> readability count


>>


Numbers
==

```
i = 42  # int
j = 1_456_789_000
b = 0b101010
c = 0b_11110000_00001111
h = 0x2a

p = 3.14  	# float
f = .1
g = 2.
h = 1e4
Decimal()	# fixed point

z = 2+3j	# complex

bfn = 123**465  # just try it !!
```

vv


### Conversions
```
>>>hex(42)
'0x2a'

>>>bin(42)
'0b101010'
 
>>>int('0xff')  # nop!
ValueError: invalid literal for int() with base 10: '0xff'

>>>int("0xff", 16)
255

>>>int("42", 8) 
34
```


>>


Operators
==
```
+ - / *   	    # really ?
2 ** 8 	        # exponent
3 / 2 		    # float divider
3 // 2 	        # int divider
4 % 2 		    # modulo
3 & 1 		    # binary
True or False 	# logic (see #Boolean) 
```


>>


Strings
==

### Multiple quote possibilities
```
s = 'single quoted'
s = "double quoted"
s = 'single can enclose a "double" quote'
s = "and vice n'versa"
s = """this is a loooooooooooooo...
...ooooooooooooo....
...oooooooooooooooooon string!!"""
s = "multi\nline"
s = 'if you don\'t like it you can escape!'
```

### More strings...
Specialized string
```
>>> raw = r"this is NOT a multi \n line string"		    # raw string
>>> fmt = f"{name}"		                                # advanced formatting
>>> unicode = u"I ❤️ python"                            # ok just kidding...it doesn't work in console
>>> ascii = b"plain ASCII literal chars"                # byte-array filled with char, but it's BYTES !!
```

byte-array (or bytes) are not string:
```
>>> this_will_fail = b"Pas de français!"
SyntaxError: bytes can only contain ASCII literal characters.
```
> remember that all python string are UNICODE by default, UTF-8 encoded.


vv


Just one more encoding/decoding for comprehension:
```
>>> s = "énorme"
>>> b = s.encode("utf-8")
>>> b
b'\xc3\xa9norme'
```

b is the binary representation of "énorme" using UTF-8 encoding.

Now try to decode it:
```
>>> b.decode("ascii")
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 0: ordinal not in range(128)

>>> b.decode("latin")
'Ã©norme'       #  here, why most of web site have encoding/decoding issues...

>>> b.decode("utf-8")
'énorme'

```


vv


String formatting
--
```
# %
print("This is so %d" % 2010)
print("%s %s" % ("Hello", "world !"))
#  not deprecated but discouraged...
#  ... but so usefulle for basic things !


#  with more options:
print("That might be a bit %d".format(2015))
print("{:>20d}".format(1234))

#  can do evaluation:
futur = 20
print(f"This is definitely {futur*101}")
```

vv


Common tool:
--
```
str.strip()
str.split()
str.join()
str.replace(old, new, )
str.index(sub_str)
str.isnumeric()
```


>>


List []
==
Simple arrays with any values type, can be mixed:
```
anything = [1, 2.0, "three", obj]
```
Slicing:
 
``list[i:j:step]`` : from i (included) to j (excluded)

Works also with negative index (from end)


vv


Quiz
--
```
numbers = [4, 8, 15, 16, 23, 42]
# QUIZ !
l[0] ?
l[-1] ?
l[2:3] ?
l[1:] ?
l[:5] ?
l[4:4] ?
```


vv


Common tool:
--

```
#  filling
my_list.append(elem)
my_list.insert(i, elem)

#  consuming
i = my_list.index(elem)
elem = my_list.pop(i)   # .pop() pop the last elem
my_list.remove(elem)

#  tooling
my_list.sort()
my_list.reverse()
my_list = sorted(<collection>)
<iter> = reversed(my_list)
my_list.clear()

#  aggregation
my_list.extend(<collection>)
tuple_list = zip(my_list, other_list)

```


vv


List comprehension
--
List comprehension is a dedicated syntax to return a new list
```
under_10 = [ n for n in numbers if n <= 10 ]  
```


vv


Exo
--

```
#  initial conditions
numbers = [8, 4, 16, 42, 23, 15]
letters = ['a', 'b', 'c', 'd', 'e']
names = ['valerie', 'ben', 'brice', 'olivier', 'christelle']
genres= ['f', 'm', 'm', 'm', 'm', 'f']
```

* list all even element ?
* highest element ?
* list all women


vv


SOLUCE
--

* list all even element ?
```
[ n for n in numbers if not n % 2 ]
```

* highest element ?
```
sorted(numbers, reverse=True)[0]    # ok...
max(numbers)                        # better :)
```

* list all women
```
[e[0] for e in zip(names, genres) if e[1] == 'f']
```


>>


Dictionary {}
==
Store pair of any types as key:value
```
A key must be hashable
empty_dict = {}  # or dict()
my_dict = {'A': 1, 'B': 2, 'C': 3}
other_dict = {
      'one': 1,
      2: 'two',
      3.14: math.pi,
      4: [1, 2, 3]
    }

my_dict[A] 		# 1
'B' in my_dict 	# Does the key exists ? True.
3 in my_dict 		# You cannot check a value here.
my_dict['D'] = 4	# Added a new pair.
my_dict['B'] = 5	# Updated

t = 3.14

```


vv


### Common tool
```
#  access
value = my_dict.get(key, default=None)  # with a default value you'll get no KeyError
value = my_dict.pop(key)    # remove elem

# decompose dictionary
my_dict.keys()  # list of keys
my_dict.values()  # list of values
my_dict.items()  # list of tuple (key, value)
```


vv


### Dict comprehension
```
  #  similar to list comprehension, but with a pair:
  {k: v for k, v in my_dict.items() if ...} 
 # build a dict from lists:
```


vv


EXO
--
Build a dict from previous both list names and genres 


vv


SOLUCE
--
>Using list comprehension:
>```
> {e[0]:e[1] for e in zip(names, genres)}
>```


>Better with constructor:
>```
> people = dict(zip(names, genres))
>```


vv


EXO
--
Return all men from the previous results


vv


SOLUCE
--
```
[name for name, genre in people.items() if genre == 'm']
```


vv


More tools
--
```
>>> from collections import Counter
>>> Counter(genre)
{'f': 2, 'm': 4}

```


>>


Tuple {v, ...}
==
A couple (or more) of any values.

A tuple is not mutable.

```
t = {4, 2}  # remember, this is not a dictionnary...
```
 
Can be exploded:
```
a, b = t
```

Easy swap:
```
a, b = b, a
```

Similar to a list, but a tuple is immutable, so you can't change it.
```
t.pop()  # will fail
```


>>


Set ()
==
All elements in a set are _unique_
```
my_set = set()
other_set = set(<collection>)

set(genres)  # will return {'f', 'm'}
```


vv


### Common
```
# getters

my_set.add(elem)
my_set.update(<collection>)


#  comparaison
<set>  = <set>.union(<coll.>)                 # Or: <set> | <set>
<set>  = <set>.intersection(<coll.>)          # Or: <set> & <set>
<set>  = <set>.difference(<coll.>)            # Or: <set> - <set>
<set>  = <set>.symmetric_difference(<coll.>)  # Or: <set> ^ <set>
<bool> = <set>.issubset(<coll.>)              # Or: <set> <= <set>
<bool> = <set>.issuperset(<coll.>)            # Or: <set> >= <set>

```


>>


Booleans
==
Everything can be evaluated as a boolean

Just try it:

```
# numbers
bool(0) # ZERO is False
bool(3) # Everything else is True

# strings
bool("") # EMPTY strings are False
bool("blah") # True

# any containers
bool([]) # Empty list are False
bool({}) # Empty dict are False

# None
bool(None)  # False

```

vv


common boolean tool
--

```
all(<iterable>)
```

```
any(<iterable>)
```


vv


If clauses
--
```
if <condition>:
    <clause>
elif <condition>:
    <clause>
else:
    <condition>
```

Don't:
```
if len(my_string) > 0:
    ...
```
 
Do:
```
if my_string:
    ...    
```


vv


EXO
--
gived the following number input list,
```
numbers = [1, 5, 0, None, 8]
```

display the string representation, comma separated, with a default "nop" for 0 or null values.


vv


SOLUCE
--

bad:
```
s = ''
for n in numbers:
    s += str(n) if n else 'nop'
    s += ','
```
    
better:   
```
",".join([str(n) if n else 'nop' for n in numbers])
```


vv


Tip
--

usefull to set a default value
```
>>> [n or 0 for n in numbers]
[1, 5, 0, 0, 8]
```

usefull to override a value
```
>>> [n and 1 for n in numbers]
[1, 1, 0, None, 1]
```

best:
```
>>> ["yes" if n else "no" for n in numbers]
```

```
>>> [n and "yes" or "no" for n in numbers]
```


vv


Loops
--
```
while <condition>:
    <code>
```

```
for <statement>:
    <code>
    
for i in range(10):
    print(i)
    
for elem in [2, 3, 5, 7, 9, 11]:
    print(elem)      
```


vv


``for`` has also an ``else`` clause:

```
all_rings = ['narya', 'nenya', 'vivya', 'sauron']
for ring in all_rings:
    if ring == "sauron":
        print("my precious...")
        break
else:
    # the ring has not been found
    print("Hobbits win...")        
          
```


>>


Functions
==
Standard arguments
```
#  basic function:
def my_func():
    <code>
     

#  add some parameters
def get_username(first_name, last_name):
    return first_name[0] + last_name    # will fail if no first_name!
```
    

vv

    
Arguments with default values:
```
#  add default values
def get_email(first_name, last_name, domain="presto-eng.com"):
    return f"{first_name[0]}.{last_name}@{domain}"
     
>>> get_email("darth", "vader", domain="empire.com")   
'd.vader@empire.com'
```


vv

Lambda, aka anonymous functions
--
As Voldemort, you can't name it...

### Restriction in Python
Keep it simple:
- only one line
- only one instruction

### syntax
```
lambda <params> : <expression>
```
it would be equivalent to this function:
```
def <lambda>(<params>):
    return <expression>
```

Then,
```
def first_letter(name):
    return name[0] if name else '-'
```
is equivalent to 
```
lambda name: name[0] if name else '-'
```

and you can assign it, or use it directly:

```
>>> f = lambda name: name[0] if name else '-'
>>> f("Scarlett")
S
>>> f("")
-
>>>f(None)
-
```

### usage
lambda are used for transformation, sorting, ...


vv


EXO
--

```
# TODO: get a list of 100 random integers  
...

# TODO: use the filter build-in function and a lambda to keep only < 10 elements
>>> help(filter) 

# TODO: use the sorted build-in function and a labmda to sort numbers by unit
>>> help(sorted) 
```
 
 
vv
 
 
SOLUCE
--
```
# get a list of random integers  
>>> a = [random.randint(1, 100) for n in range(100)]

# use the filter build-in function and a lambd to keep only < 10 elements
>>> list(filter(lambda v:v < 10, v))

# use the sorted build-in function and a labmda to sort numbers by unit
sorted(a, key=lambda v:v % 10)
```


vv


Partial functions
--
TODO


>>


Splat operator * **
==

```
*           # splat operator
**          # splatty-splat operator
```

Unpacking data
--

automatic unpacking:
```
it_guys = ["olivier", "david", "ahmed", "louis", "aurelien"]    # famous team :)
o, d, a, l, r = it_guys    # auto unpacked
```


use splat operator (*) to specify how to unpack list:

```
manager, *peons = it_guys  # use splat operator
manager, *others, missing = it_guys  # works also in the middle...
```


EXO
--

Anyone for a pizza ?
```
#  here a standard function with named arguments and default values set to None.
def make_pizza(elem1, elem2=None, elem3=None):
    print("Let's cook...")
    print(elem1)    # mandatory ingredient
    print(elem2)    # optionnal 1
    print(elem3)    # optionnal 2

ingredients = ("cheeze", "tomatoes", "chorizo")
make_pizza(ingredients)  
>>> Let's cook...
>>> ('cheeze', 'tomatoes', 'chorizo')
>>> None
>>> None
```

We need to unpack ingredients first:
```
make_pizza(*ingredients)    # need to force unpacking
>>> Let's cook...
>>> cheeze
>>> tomatoes
>>> chorizo
```


vv


splat operator in function declaration
--

```
def list_ingredients(*ingredients):
    for ingredient in ingredients:
        print(f"+ {ingredient}")
        
list_ingredients(*ingredients)
>>> + cheeze
>>> + tomatoes
>>> + chorizo        
```


vv


### using dictionary and splatty-splat operator
```
#  reuse previous get_email() function

luke = {"first_name": "luke", "last_name" : "skywalker"}
get_email(**luke, domain="rebels.org")   
>>> 'l.skywalker@rebels.org'
```


vv


EXO:
--
please improve make_pizza function to allow any optional ingredients


vv


SOLUCE
-- 
```
def make_pizza(base_item, *optionnal_items):
    print("let's cook")
    print(f"first add base_item")
    for item in optionnal_items:
        print(f", add some {item}")
        
make_pizza(*ingredients)

# list are no more mandatory:  
make_pizza("tomate", "ananas", "banana", "chocolate")      
```


>>

functions
==

complete function definition
it's possible to combine all kind of arguments, but the order is mandatory
* mandatory arguments (arg)
* optionnal arguments (arg=default)
* dynamic arguments (*args)
* named dynamic arguments (**kwargs)
```
def define_team(team_name, manager_name=None, *users, **kwargs):
    pass
    #  you'll need to unpack users
    #  kwargs are key-word arguments, ie a dictionary
    
```

It's possible to specify keyword parameters only:
```
def define_team(team_name, manager_name=None, *users, site_name, ):
    # site_name is mandatory and should be call with a named position
    print(team_name)
    print(manager_name)
    print(users)
    print(site_name)
    
define_team('IT', 'olivier', 'ahmed', 'david', site_name='MPH')  # good
define_team('IT', 'olivier', 'ahmed', 'david', 'MPH')            # is an error

   
```


>>


Iterator
==
In python prefer use ``for`` than ``while``
That's why there is many iterator tools:
```
from itertools import count, repeat, cycle, chain, islice
```

```
production_support_duty = cycle(["vince", "ben", "val", "brice"])
next(production_support_duty)
next(production_support_duty)
next(production_support_duty)
next(production_support_duty)
next(production_support_duty)
next(production_support_duty)
```


>>


Generator
==
It looks like a function, but it's not !
``yield`` keyword replace ``return``
But you can continue to use return if you want to end the generator
```
def my_odd_generator():
    value = 1
    while True:
        yield value
        #  the generator execution will continue from HERE on next call !
        value += 2
```


It can looks like list comprehension, but it's not !
my_even_generator = (x for x in range(10) if not x % 2)

A generator is LAZY, computed one item at a time:
- low memory usage
- small computation at a time


vv


EXO
--
Build a traffic lights generator green->orange->red->...


vv


SOLUCE
--
```
def traffic_light():
    while True:
        yield "green"
        yield "orange"
        yield "red"
```


>>


Exceptions
==
> fail first !
```
try:
    <do some code>
    
    if <condition>:
        raise ValueError("Can't do that...")

except:
    <catch exception>

finally:
    <always executed>
```

Main exceptions:
* IndexError (list access)
* KeyError (dictionary access)
* ValueError (numeric error, or type error, ...)
* IOError (files)


>>


Regex
==
> Do you regex ?
```

```


vv


Exo
--


named regex explode, 

see exo3-binning


vv


real code sample
--

search in gateway
part number decoding

see delphi, search 


>>


Files
==

Navigation
--

```
import os
filename = os.path.join("here", "we, "go.txt")  # will work windows AND unix
os.listdir()
os.rename(filename, "blah.txt") # TODO : check destination...
os.mkdir(dirname)
os.mkdirs(f'logs/{product}/{lot}/{probe}')

```

https://realpython.com/working-with-files-in-python/


vv


Searching a filename

```
import fnmatch

def get_history_files():
    """ search for PIMS PID history files """
    for root, dirnames, filenames in os.walk(HISTORY):
        for filename in fnmatch.filter(filenames, 'PIDUpdatesFollowUp_*.log'):
            yield os.path.join(root, filename)


```


```
import shutil
shutil.rmtree(dirname)
shutil.mkdirs() # TODO:check ?
```

```
import glob
for file in glob.glob('**/*.csv', recursive=True):   # recursive
    print(file)

```


vv


Text files
--
``obj = open(filename, mode)``

> not very good:
```
f = open(filename, 'r')
f.readline()
close(f)
```

> at least it's safe:
```
f = open(filename, 'r')
try:
    f.readline()
finally:    
    close(f)
```

> pythonic: using context manager (with):
```
with open(filename, 'r') as file:
    for line in file:
        print(line)
```


vv


Common
--

https://www.pythonforbeginners.com/cheatsheet/python-file-handling
https://realpython.com/working-with-files-in-python/

```
file.write()
file.append()
file.read()
file.readline()
file.readlines()
file.writelines()
```


vv


Csv files
--
Load CSV file
```
import csv
Read Rows from CSV File
def read_csv_file(filename):
    with open(filename, encoding='utf-8') as file:
        return csv.reader(file, delimiter=';')
```
        
Write Rows to CSV file
```
def write_to_csv_file(filename, rows):
    with open(filename, 'w', encoding='utf-8') as file:
        writer = csv.writer(file, delimiter=';')
        writer.writerows(rows)
```
        

vv


Excel files
--

http://sametmax.com/lire-et-ecrire-dans-un-fichier-xls/

or you can also use `panda package`


vv


Binaries files
--
https://gto76.github.io/python-cheatsheet/#struct

Struct
Module that performs conversions between Python values and a C struct, represented as a Python bytes object.
Machine’s native type sizes and byte order are used by default.
```
from struct import pack, unpack, iter_unpack, calcsize
<bytes>  = pack('<format>', <value_1> [, <value_2>, ...])
<tuple>  = unpack('<format>', <bytes>)
<tuples> = iter_unpack('<format>', <bytes>)
Example
>>> pack('>hhl', 1, 2, 3)
b'\x00\x01\x00\x02\x00\x00\x00\x03'
>>> unpack('>hhl', b'\x00\x01\x00\x02\x00\x00\x00\x03')
(1, 2, 3)
>>> calcsize('>hhl')
8
```


vv


Exo
--

TODO:exo-struct

Real code sample
--
stdf output
nxp input


>>


Class
==
finally we're talking OOP!

> Everything is object...

Introspection
--

you can directly read information or request help in your code:
```
>>> import struct


# will display all function list:
>>> dir(struct)

['Struct', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', '_clearcache', 'calcsize', 'error', 'iter_unpack', 'pack', 'pack_into', 'unpack', 'unpack_from']

# display a full help
>>> help(struct)
Help on module struct:

NAME
    struct

DESCRIPTION
    Functions to convert between Python values and C structs.
    Python bytes objects are used to hold the data representing the C struct
    and also as format strings (explained below) to describe the layout of data
    in the C struct.

    The optional first format char indicates byte order, size and alignment:
      @: native order, size & alignment (default)
      =: native order, std. size & alignment
      <: little-endian, std. size & alignment
      >: big-endian, std. size & alignment
      !: same as >
    ...
```

vv


class structure
--

Let's create a simple PASS/FAIL die result
```
class DieResult(object):
    """ simple container to know if a die is pass or fail"""
    def __init__(self):
        """ here the constructor"""
        #  define here all member method
        self.good = False 
        
        
#  Usage:
die = DieResult(True)   # a good die        
```


vv


Now we want to extend it to have its position on a wafer:
```
class WaferDieResult(DieResult):
    """ extended container to have the wafer position """
    def __init__(self, x, y, good):
        """ here the extended constructor"""
        #  call the inherited constructor first
        super().__init__(good)
        #  add new members
        self.x = x
        self.y = y
        
        
#  Usage:
>>> die = WaferDieResult(30, 40, True)  # another good die
>>> die.x
30
>>> die.good
True
```


vv


```
>>> die
<__main__.WaferDieResult object at 0x0000023F2BFB4080>       
```
not very friendly...
lets improve the string representation.

```
class WaferDieResult(DieResult):
    ...
    def __str__(self)__:
        s = "PASS" if self.good else "FAIL"
        return f"{s} at ({x}, {y})"
        
>>> die = WaferDieResult(30, 40, True)  # another good die
>>> die
PASS at (30, 40)        
```


vv


dunder method
--
dunder stands for double-underscore,
all dunder methods are python internals and standard method,
you can override it when needed
```
    def __init__(self, x, y, good):
        """constructor"""

    def __str__(self):
        """ string representation"""

    def __lt__(self, other):
        """ comparator """
```


vv


dynamic members
--

```
class Person(object):
    """ here an empty class """
    pass
    
p = Person()
p.name = "Vince"
p.age = 42
dir(p)

# new attributes are displayed.
```


vv


private and protected convention
--

> "We are all consenting adults"

Everything is public, but there is convention to avoid naming collision:

```
class Person(object):
    def __init__(self, name):
        self.__internal_value = None    # This value is private
        self._option = None             # This value is protected
        self.name = name                # This value is public 
        
        
    def __private_method(self):
        # this method is private
        # note this is not a dunder method :no __name__(), only __name()
        pass
        
    def _protected_method(self):
        # this method is protected (or friend)
        
```
 
 
vv


Don't do a class for everything...
--

> ### Just do it when:
> if you have members
> if you need inheritance
> if you need to override a behavior
> context manager (see next slide)

> ### No you wont when:
> keep it simple !
> no member, no inheritance : a package (file) is enough
> most transformation script don't need it (extract, transform, load)


http://introtopython.org/classes.html


>>


Context Manager
==
A context manager is an object which can be used to simplify tidy up of object.
It's used with `with` keyword
```
with MyContextManager as cm:
    ... # do your code here
``` 

and is similar to
    
```
cm = MyContextManager()
try: 
    cm.__enter__()
    ... # do your code here
except:
    cm.__exit__()
    raise 
``` 


vv


Exo
--
See exo-struct,
 
improve binary file reader/writer.    
    
    
>>


Enum
==
This is done by a class
```
from enum import Enum


class PrestoServices(Enum):
    pe = 'Product Engi'
    te = 'Test Engi'
    tl = 'Tools'
    it = 'IT'


ps = PrestoServices  # just an alias
```

directly access a enum item
```
print(ps.pe)
print(ps.pe.name)
print(ps.pe.value)
```

get an enum item by its value
```
tools = ps('Tools')
print(tools)
print(tools.name)
print(tools.value)

```


>>


Dataclass
==
Need python >= 3.7

https://realpython.com/python-data-classes/


```
import dataclasses

@dataclasses
class Lot:
    number: str
    prodid: str
    prodconf: str
    waf_list : list[int]
```

Usage:
```
qt1234 = Lot("QT1234", "AB001", "ABACAD", [1,2,3,4,5])

```


>>


Typing
==
> You're missing some type information ?

Sometimes it can be usefull...
(python > 3.5)

https://docs.python.org/3/library/typing.html
```
def hello(name : str) -> str:
    return f"Hello {name}"

```


>>


Logging
==
TODO
```
import logging
```


>>


Unit tests
==
TODO


>>


Decorators
==
TODO


>>


DuctTyping
==
TODO
If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck.

http://sametmax.com/quest-ce-que-le-duck-typing-et-a-quoi-ca-sert/


>>


ArgParse
==
TODO


>>


Application
==
Build a desktop application with WxPython
https://wxpython.org/


>>


funny stuff
==

star war api
--

https://swapi.co/api/people/?format=api
API to list all SW people 
https://github.com/phalt/swapi-python


>>


links
==
https://docs.python.org --
https://realpython.com/ --
https://legacy.python.org/dev/peps/pep-0008/ --
https://google.github.io/styleguide/pyguide.html -- 
https://docs.python-guide.org/ --
https://gto76.github.io/python-cheatsheet/ --
https://www.youtube.com/channel/UC-QDfvrRIDB6F0bIO4I4HkQ/videos --
https://regex101.com/ --
https://www.pythoncentral.io/category/python-tips-tricks-hacks-idioms/ --
https://python-guide-chinese.readthedocs.io/zh_CN/latest/writing/style.html --
https://2.python-requests.org//en/master/ --
https://www.pythoncentral.io/ --
http://sametmax.com/ (NSFW!) --
https://en.wikipedia.org/wiki/Python_(programming_language) --
https://fr.wikipedia.org/wiki/Guido_van_Rossum --
http://introtopython.org/classes.html --