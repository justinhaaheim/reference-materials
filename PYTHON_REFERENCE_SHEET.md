Python Reference Sheet
======================
by Justin Haaheim

# Google's naming conventions:

module_name, package_name, ClassName, method_name, ExceptionName, function_name, GLOBAL_CONSTANT_NAME, global_var_name, instance_var_name, function_parameter_name, local_var_name.

Use CapWords for class names, but lower_with_under.py for module names.

from wikipedia:
For clarity, this article calls the two alternatives upper camel case (initial upper case letter, also known as Pascal Case) and lower camel case (initial lower case letter).


# Data types

## Numbers

```python
# Absolute value
abs(-10)  # Result: 10

# Int rounds to floor
int(2.5)  # Result: 2

# Bear in mind this common mixup:
>>> a = 5  # 5 is an int type
>>> a / 2  # 2 is an int type
2          # the result is an int, and is rounded down
>>> b = 5.0  # 5.0 specifies a float
>>> b / 2
2.5

>>> type(5.0)  
<type 'float'>   # see! float!


import math
math.floor
math.ceil(2.5)  # 3
```

## Types


Best way to check for types is isinstance() because it can handle inheritance
```python
import types

isinstance(True, types.BooleanType)  # True

isinstance("Sandwich", types.IntType)  # False
```

## Booleans

```python
not a == b
# is the same as
not (a == b)
```

## Sequence types (str, list, tuple)

```python
"hi" in "abchid"  # True

"hi" not in "abcdef"  # True

"yo" in ["hi", "there"]  # False
"hi" in ["hi", "there"]  # True

"11122".count("1")  # 3
[1, 1, 1, 2, 2].count(1)  # 3

thistuple = (12, 89, 'a')
```

## Lists

```python
b = ['a', 'b', 'c', 'd']
b[1:3] = 'z'
b  # ['a', 'z', 'd']

words = ['this', 'is', 'a', 'list', 'of', 'strings']
''.join(words)  # 'thisisalistofstrings'

c = ['a', 'b', 'c', 'd', 'e']
c[-1]  # 'e'
c[1:-1]  # ['b', 'c', 'd']
c[2:1000]  # ['c', 'd', 'e']
c[::2]  # ['a', 'c', 'e']
c[1::2]  # ['b', 'd']

d = ['a', 'b', 'c', 'd', 'e']
d.pop()  # 'e'
d  # ['a', 'b', 'c', 'd']

e = ['a', 'b', 'c', 'd', 'e']
e.insert(1, 'monkey')
e  # ['a', 'monkey', 'b', 'c', 'd', 'e']
e.insert(-1, 'monkey')
e  # ['a', 'monkey', 'b', 'c', 'd', 'monkey', 'e']
e.remove('monkey')  # Removes the first occurrence of the thing
e  # ['a', 'b', 'c', 'd', 'monkey', 'e']
e.remove('monkey')
e  # ['a', 'b', 'c', 'd', 'e']
del e[1]
e  # ['a', 'c', 'd', 'e']
```

Append concatenates a single element. Extend concatenates another list:

```python
>>> a = [1, 2, 3]
>>> a.append(4)
>>> a
[1, 2, 3, 4]
>>> a.extend([5, 6, 7])
>>> a
[1, 2, 3, 4, 5, 6, 7]
```

## Strings

```python
"hi" in "abchid"  # True

"hi" not in "abcdef"  # True

"abcdef" [1:5]  # 'bcde'

s = "Hello World!"
s.split(" ")  # ['Hello', 'World!']

'   spacious   '.lstrip()  # 'spacious   '
'www.example.com'.lstrip('cmowz.')  # 'example.com'

'i like fish. fish!'.replace('fish', 'chipotle')  # 'i like chipotle. chipotle!'

'This is SO GREAT'.lower()  # 'this is so great'
'This is SO GREAT'.upper()  # 'THIS IS SO GREAT'

'ABCD'.isupper()  # True
'ABCD123'.isupper()  # True
'123'.isupper()  # False

'  '.isspace()  # True
'a  '.isspace()  # False

'abc'.isalpha()  # True
'abc1'.isalpha()  # False
'123'.isdigit()  # True

'abcdef'.find('de')  # 3
'abcdef'.find('potato')  # -1

'abcdef'.index('de')  # 3
'abcdef'.index('potato')  # ValueError: substring not found

'''This
is
multiple
lines'''.splitlines()  # ['This', 'is', 'multiple', 'lines']

'''This
is
multiple
lines'''.splitlines(True)  # ['This\n', 'is\n', 'multiple\n', 'lines']

'abcdef'.startswith('ab')  # True
'abcdef'.endswith('ef')  # True
```

### python string library functions

```python
import string

string.ascii_letters
# The concatenation of the ascii_lowercase and ascii_uppercase constants described below. This value is not locale-dependent.

string.ascii_lowercase
# The lowercase letters 'abcdefghijklmnopqrstuvwxyz'. This value is not locale-dependent and will not change.

string.ascii_uppercase
# The uppercase letters 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'. This value is not locale-dependent and will not change.

string.digits
# The string '0123456789'.

string.hexdigits
# The string '0123456789abcdefABCDEF'.

string.letters
# The concatenation of the strings lowercase and uppercase described below. The specific value is locale-dependent, and will be updated when locale.setlocale() is called.

string.lowercase
# A string containing all the characters that are considered lowercase letters. On most systems this is the string 'abcdefghijklmnopqrstuvwxyz'. The specific value is locale-dependent, and will be updated when locale.setlocale() is called.

string.octdigits
# The string '01234567'.

string.punctuation
# String of ASCII characters which are considered punctuation characters in the C locale.

string.printable
# String of characters which are considered printable. This is a combination of digits, letters, punctuation, and whitespace.

string.uppercase
# A string containing all the characters that are considered uppercase letters. On most systems this is the string 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'. The specific value is locale-dependent, and will be updated when locale.setlocale() is called.

string.whitespace
# A string containing all characters that are considered whitespace. On most systems this includes the characters space, tab, linefeed, return, formfeed, and vertical tab.
```

## Dictionaries (Hashtables)

Note that in general the time complexity of hashtables is:

access: N/A  (there's no real concept of direct access)
search: O(1), worst case O(n)
insert: O(1), worst case O(n)
delete: O(1), worst case O(n)

space complexity: O(n)

```python
emptyDict = {}
thisdict = {'a': 1, 'b': 23, 'c': "eggs"}

thisdict.keys()  # ['a', 'c', 'b']

thisdict.items()  # [('a', 1), ('c', 'eggs'), ('b', 23)]

'c' in thisdict  # True

'e' in thisdict  # False

# # Deprecated:
# thisdict.has_key('e')  # False

23 in thisdict  # False -- `is` checks keys, not values
```

# Sets

```python
a = set([1, 2, 5, 6, 7])
len(a)  # 5
2 in a  # True

a.isdisjoint([11, 12, 13])  # True
a.isdisjoint([2])  # False

set([1]).issubset(set([1, 2, 3]))  # True

set([1, 2, 3]).issuperset(set([1]))  # True

set([1, 2]) | set([2, 3])  # set([1, 2, 3])
set([1, 2]).union(set([2, 3]))  # set([1, 2, 3])
```

## Stacks

Just use a list!

## Queues

To implement a queue, use `collections.deque` which was designed to have fast appends and pops from both ends. For example:

```python
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```

## Other data types

One simple way to create a simple data type with no methods is:

```python
>>> import collections
>>> Node = collections.namedtuple('Node', 'val left right')
>>> Node
<class '__main__.Node'>
>>> a = Node(10, 0, 1)
>>> a
Node(val=10, left=0, right=1)
```

# Exceptions

```python
try:
    'abcdef'[100]
except IndexError as err:  # This is the python3 way, also works in python2
    print(err)  # string index out of range

# try:
#     'abcdef'[100]
# except IndexError, err:
#     print(err)

try:
    'abcdef'[100]
except (IndexError, ValueError) as err:
    print(err)  # string index out of range

raise Exception("Error Message")
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# Exception: Error Message
```

## Regular Expressions

```python
import re

r = re.compile(r"[a-z]+")  # matches groups that contain at least one letter a to z
m = r.match("")
m  # None

m = r.match("tempo")
m.group()  # 'tempo'
m.span()  # (0, 5)

m = r.match("  tempo .")
m  # None

m = r.search("  tempo .")
m.group()  # 'tempo'
m.span()  # (2, 7)

m = r.findall("regexes are super great")
# Returns a list
m  # ['regexes', 'are', 'super', 'great']

# You don't need to separately compile a regex -- you can access it directly:
m = re.match(r"[0-9]")

m = re.match(r"((\(\d{3}\) ?)|(\d{3}-))?\d{3}-\d{4}", "(123) 456-7890")
m.group()  # '(123) 456-7890'

# search_string = '''(123) 456-7890
# hello fred
# my number is 555-555-1234
# '''
# m = re.findall(r"((\(\d{3}\) ?)|(\d{3}-))?\d{3}-\d{4}", search_string)
```


. (dot)
any character except a newline
‘a.c’ matches ‘abc’,
but not ‘bbc’.

^
the start of the string
‘^abc’ matches ‘abcd’,
but not ‘dabc’.

$
the end of the string
‘abc$’ matches ‘dabc’,
but not ‘abcd’.

*
0 or more repetitions of preceding RE
‘a*’ matches ‘a’, ‘aa’, ‘aaa’,
and also ‘b’ (zero ‘a’).

+
1 or more repetitions of preceding RE
‘a+’ matches ‘a’, ‘aa’, ‘aaa’,
but not ‘b’ (zero ‘a’).

?
0 or 1 repetition of preceding RE
‘a?’ matches 0 or more ‘a’s,
but returns at most 1 ‘a’.

{ m }
m repetitions of preceding RE
‘a{3}’ matches ‘aaa’, ‘baaa’,
but not ‘aa’, ‘baab’.

{ m , n }
m to n repetitions of preceding RE
‘a{2,3}’ matches ‘aa’, ‘aaa’,
but not ‘a’, ‘bab’.

[ ]
a set of characters between [ and ]
‘[abcd]’ matches string containing any of ‘a’, ‘b’, ‘c’, and ‘d’.
[1]
A | B	A or B where A and B are arbitrary REs
‘ab|cd’ matches string containing ‘ab’ and/or ‘cd’.

\d
any decimal digit 0 to 9
‘\d’ matches ‘a1b’,
but not ‘ab’.

\w
any alphanumeric character and underscore i.e. a-zA-Z0-9_
‘\w’ matches ‘a1B’,
but not ‘%#!’.

( ... )
any RE inside parentheses, and indicates the start and end of a group. \ number can be used to match the same group later in the string.
r’(\d)(\d)\2’ matches ‘122’
but not ‘112’.

# Functional programming

```python
>>> def f(x): return x % 3 == 0 or x % 5 == 0
...
>>> filter(f, range(2, 25))
[3, 5, 6, 9, 10, 12, 15, 18, 20, 21, 24]


>>>
>>> def cube(x): return x*x*x
...
>>> map(cube, range(1, 11))
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]

>>>
>>> seq = range(8)
>>> def add(x, y): return x+y
...
>>> map(add, seq, seq)
[0, 2, 4, 6, 8, 10, 12, 14]


>>>
>>> def add(x,y): return x+y
...
>>> reduce(add, range(1, 11))
55
```

# Testing and Debugging

## Logging

```python
import logging

logging.basicConfig(
    # level=logging.DEBUG,  
    # level=logging.INFO,  
    level=logging.WARNING,
    format='%(asctime)s - %(levelname)s - %(message)s')

logging.debug("Here is a debug message.")
logging.info("Here is an info message.")
```

## doctest

## unittest

```python
import unittest2

class TestScrabble(unittest2.TestCase):

    # This is the test fixture, used primarily for opening up files,
    # connections, etc
    def setUp(self):
        self.widget = Widget('The widget')

    def tearDown(self):
        self.widget.dispose()

    @classmethod
    def setUpClass(cls):
        cls.thing_to_test = "This is "

    # This is a test case
    def descriptive_test_name(self):
        self.assertEqual(True, True)
        self.assertEqual(True, True)


class TestServerHandling(unittest2.TestCase):

    def descriptive_test_name(self):
        # These tests should be bundled together in one function like this
        # because each one depends on the results of the previous. If we were
        # to do more tests that do not depend on these results, we would create
        # a new function
        tracker = ServerHandling()
        self.assertTrue(tracker.allocate("apibox") == "apibox1")
        self.assertTrue(tracker.allocate("apibox") == "apibox2")
        self.assertTrue(tracker.deallocate("apibox1") == None)
        self.assertTrue(tracker.allocate("apibox") == "apibox1")
        self.assertTrue(tracker.allocate("sitebox") == "sitebox1")


if __name__ == '__main__':
    # This is the test runner
    unittest2.main()

```

You can place the definitions of test cases and test suites in the same modules as the code they are to test (such as widget.py), but there are several advantages to placing the test code in a separate module, such as test_widget.py:

The test module can be run standalone from the command line.
The test code can more easily be separated from shipped code.
There is less temptation to change test code to fit the code it tests without a good reason.
Test code should be modified much less frequently than the code it tests.
Tested code can be refactored more easily.
Tests for modules written in C must be in separate modules anyway, so why not be consistent?
If the testing strategy changes, there is no need to change the source code.


# Language features

## Keyword arguments

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print "-- This parrot wouldn't", action,
    print "if you put", voltage, "volts through it."
    print "-- Lovely plumage, the", type
    print "-- It's", state, "!"
```

accepts one required argument (voltage) and three optional arguments (state, action, and type). This function can be called in any of the following ways:

```python
parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
```

NOTE: all the following calls would be **invalid**:

```python
parrot()                     # required argument missing
parrot(voltage=5.0, 'dead')  # non-keyword argument after a keyword argument
parrot(110, voltage=220)     # duplicate value for the same argument
parrot(actor='John Cleese')  # unknown keyword argument
```
