# Python Built-in Collections

## Collection Classifications

Python Collections can be classified as follows based on mutability:

- Mutable : Can be updated after creation
- Immutable : Cannot be updated after creation

Python Collections can be classified as follows based on ordering of elements:

- Ordered : order of input elements is maintained
- Unordered : order of input elements is not maintained

A sequence or collection can therofore be classified on basis of mutability and orderedness.

---

## Common Sequence Operations

Immutable Sequences implement most of the Common Sequence Operations.

The operations in the following table are supported by most sequence types, both mutable and immutable. The [collections.abc.Sequence](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence) ABC is provided to make it easier to correctly implement these operations on custom sequence types.

This table lists the sequence operations sorted in ascending priority. In the table, `s` and `t` are sequences of the same type, `n`, `i`, `j` and `k` are integers and `x` is an arbitrary object that meets any type and value restrictions imposed by `s`.

| Operation              | Result                                                                                   | Notes  |
| ---------------------- | ---------------------------------------------------------------------------------------- | ------ |
| `x in s`               | `True` if an item of _s_ is equal to _x_, else `False`                                   | (1)    |
| `x not in s`           | `False` if an item of _s_ is equal to _x_, else `True`                                   | (1)    |
| `s + t`                | the concatenation of _s_ and _t_                                                         | (6)(7) |
| `s * n` or `n * s`     | equivalent to adding _s_ to itself _n_ times                                             | (2)(7) |
| `s[i]`                 | _i_th item of _s_, origin 0                                                              | (3)(9) |
| `s[i:j]`               | slice of _s_ from _i_ to _j_                                                             | (3)(4) |
| `s[i:j:k]`             | slice of _s_ from _i_ to _j_ with step _k_                                               | (3)(5) |
| `len(s)`               | length of _s_                                                                            |        |
| `min(s)`               | smallest item of _s_                                                                     |        |
| `max(s)`               | largest item of _s_                                                                      |        |
| `s.index(x[, i[, j]])` | index of the first occurrence of _x_ in _s_ (at or after index _i_ and before index _j_) | (8)    |
| `s.count(x)`           | total number of occurrences of _x_ in _s_                                                |        |

Notes:

1. If `k` is not equal to 1, `t` must have the same length as the slice it is replacing.
2. The optional argument `i` defaults to -1, so that by default the last item is removed and returned.
3. `remove()` raises ValueError when x is not found in s.
4. The `reverse()` method modifies the sequence in place for economy of space when reversing a large sequence. To remind users that it operates by side effect, it does not return the reversed sequence.
5. `clear()` and `copy()` are included for consistency with the interfaces of mutable containers that don’t support slicing operations (such as dict and set). `copy()` is not part of the collections.abc.MutableSequence ABC, but most concrete mutable sequence classes provide it.
6. The value `n` is an integer, or an object implementing `__index__()`. Zero and negative values of n clear the sequence. Items in the sequence are not copied; they are referenced multiple times, as explained for s * n under Common Sequence Operations.

The `in` and `not in` operations have the same priorities as the comparison operations. The `+` (concatenation) and `*` (repetition) operations have the same priority as the corresponding numeric operations.

Sequences of the same type support comparisons. In particular, tuples and lists are compared lexicographically by comparing corresponding elements. This means that to compare equal, every element must compare equal and the two sequences must be of the same type and have the same length. (For full details see Comparisons in the language reference.)

### Mutable Sequence Operations

The operations in the following table are defined on mutable sequence types. The collections.abc.MutableSequence ABC is provided to make it easier to correctly implement these operations on custom sequence types.

In the table `s` is an instance of a mutable sequence type, `t` is any iterable object and `x` is an arbitrary object that meets any type and value restrictions imposed by `s` (for example, bytearray only accepts integers that meet the value restriction 0 <= x <= 255).

| Operation                 | Result                                                                                      | Notes |
| ------------------------- | ------------------------------------------------------------------------------------------- | ----- |
| `s[i] = x`                | item _i_ of _s_ is replaced by _x_                                                          |       |
| `del s[i]`                | removes item _i_ of _s_                                                                     |       |
| `s[i:j] = t`              | slice of _s_ from _i_ to _j_ is replaced by the contents of the iterable _t_                |       |
| `del s[i:j]`              | same as `s[i:j] = []`                                                                       |       |
| `s[i:j:k] = t`            | the elements of `s[i:j:k]` are replaced by those of _t_                                     | (1)   |
| `del s[i:j:k]`            | removes the elements of `s[i:j:k]` from the list                                            |       |
| `s.append(x)`             | appends _x_ to the end of the sequence (same as `s[len(s):len(s)] = [x]`)                   |       |
| `s.clear()`               | removes all items from _s_ (same as `del s[:]`)                                             | (5)   |
| `s.copy()`                | creates a shallow copy of _s_ (same as `s[:]`)                                              | (5)   |
| `s.extend(t)` or `s += t` | extends _s_ with the contents of _t_ (for the most part the same as `s[len(s):len(s)] = t`) |       |
| `s *= n`                  | updates _s_ with its contents repeated _n_ times                                            | (6)   |
| `s.insert(i, x)`          | inserts _x_ into _s_ at the index given by _i_ (same as `s[i:i] = [x]`)                     |       |
| `s.pop()` or `s.pop(i)`   | retrieves the item at _i_ and also removes it from _s_                                      | (2)   |
| `s.remove(x)`             | removes the first item from _s_ where `s[i]` is equal to _x_                                | (3)   |
| `s.reverse()`             | reverses the items of _s_ in place                                                          | (4)   |

---
---

## Built-ins library Collections

### Built-ins library Immutable Collections

#### `tuple`

`tuple` is an immutable ordered sequence of heterogenous elements.

`tuple()` constructor can take a tuple, list or range as input to construct a tuple.
Tuples can be given as input iterators to `list()` constructor to construct a list.

Empty parenthesis`()` without arguments or the `tuple()` constructor without arguments initialise an empty tuple.

#### `string`

Strings are immutable sequences of Unicode code points.
Single quoted and Double quoted strings can span only single lines.
Triple quoted strings may span multiple lines - all associated whitespace will be included in the string literal.

String literals that are part of a single expression and have only whitespace between them will be implicitly converted to a single string literal. That is, `("spam " "eggs")` == `"spam eggs"`.

Strings implement all of the common sequence operations, along with additional methods of String class.

Empty quotes of any type, `''`, `""` or `""""""` , or `str()` constructor without arguments initialise an empty string.

#### `range`

`range` is an immutable ordered sequence of numbers.

Ranges implement all of the common sequence operations except concatenation and repetition (due to the fact that range objects can only represent sequences that follow a strict pattern and repetition and concatenation will usually violate that pattern).

#### `frozenset`

`frozenset` is immutable and hashable — its contents cannot be altered after it is created; it can therefore be used as a dictionary key or as an element of another set.

To represent sets of sets, the inner sets must be frozenset objects. If iterable is not specified, a new empty set is returned.

### Built-ins library Mutable Collections

#### `list`

`list` is a mutable ordered sequence of heterogenous elements.

`list()` constructor can take a tuple, list or range as input to construct a list.
Lists can be given as input iterators to `tuple()` constructor to construct a tuple.

Brackets without arguments i.e. `[]` initialise an empty list.

#### `set`

`set` is a mutable unordered collection of distinct elements.
Since it is mutable, it has no hash value and cannot be used as either a dictionary key or as an element of another set.

Non-empty sets can be created by placing a comma-separated list of elements within braces, for example: `{'abc', 'def'}`.
`set()` constructor can take a tuple, list or range as input to create a set.
However, empty braces `{}` intialise a dictionary and not a set.

#### `dict`

`dict` (dictionary) is a mutable unordered mapping object.

A dictionary’s keys are almost arbitrary values. Values that are not hashable, that is, values containing lists, dictionaries or other mutable types (that are compared by value rather than by object identity) may not be used as keys. Values that compare equal (such as 1, 1.0, and True) can be used interchangeably to index the same dictionary entry.

Curly braces without any argument inside i.e. `{}` initialise an empty dictionary rather than an empty set.

---

## Collections library Collections

Built-in `collections` library implements specialized container datatypes providing alternatives to Python’s general purpose built-in containers list, tuple, set, and dict.

| `collections` library class | Description |
| --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [`namedtuple()`](https://docs.python.org/3/library/collections.html#collections.namedtuple "collections.namedtuple")  | factory function for creating tuple subclasses with named fields                                     |
| [`deque`](https://docs.python.org/3/library/collections.html#collections.deque "collections.deque")                   | list-like container with fast appends and pops on either end                                         |
| [`ChainMap`](https://docs.python.org/3/library/collections.html#collections.ChainMap "collections.ChainMap")          | dict-like class for creating a single view of multiple mappings                                      |
| [`Counter`](https://docs.python.org/3/library/collections.html#collections.Counter "collections.Counter")             | dict subclass for counting [hashable](https://docs.python.org/3/glossary.html#term-hashable) objects |
| [`OrderedDict`](https://docs.python.org/3/library/collections.html#collections.OrderedDict "collections.OrderedDict") | dict subclass that remembers the order entries were added                                            |
| [`defaultdict`](https://docs.python.org/3/library/collections.html#collections.defaultdict "collections.defaultdict") | dict subclass that calls a factory function to supply missing values                                 |
| [`UserDict`](https://docs.python.org/3/library/collections.html#collections.UserDict "collections.UserDict")          | wrapper around dictionary objects for easier dict subclassing                                        |
| [`UserList`](https://docs.python.org/3/library/collections.html#collections.UserList "collections.UserList")          | wrapper around list objects for easier list subclassing                                              |
| [`UserString`](https://docs.python.org/3/library/collections.html#collections.UserString "collections.UserString")    | wrapper around string objects for easier string subclassing                                          |

### Collections library List subclasses

#### `collections.deque([iterable[, maxlen]])`

`deque` (Doubly-Ended Queue, pronounced 'Deck') supports thread-safe, memory efficient appends and pops from either side of the deque with approximately the same O(1) performance in either direction.

It can be used to implement other similar data structures like stacks and single-ended queues.

- If `maxlen` argument is not specified or is `None`, deques may grow to an arbitrary length. Otherwise, the deque is bounded to the specified maximum length. Once a bounded length deque is full, when new items are added, a corresponding number of items are discarded from the opposite end. Bounded length deques provide functionality similar to the tail filter in Unix. They are also useful for tracking transactions and other pools of data where only the most recent activity is of interest.

#### `collections.UserList([input_list])`

`UserList` is used when a user wants to create their own list with some modified or new functionality.

Its attribute `data` is a real list used to store the contents of the UserList class. The instance’s contents are initially set to a copy of `input_list`, defaulting to the empty list `[]`. `input_list` can be any iterable, like a list or another UserList object.

### Collections library Tuple subclasses

#### `collections.namedtuple(typename, field_names, *, rename=False, defaults=None, module=None)`

`namedtuple` returns a new tuple subclass named typename. The new subclass is used to create tuple-like objects that have fields accessible by attribute lookup as well as being indexable and iterable. Instances of the subclass also have a helpful docstring (with typename and field_names) and a helpful `__repr__()` method which lists the tuple contents in a `name=value` format.

- `field_names` can be sequence of strings such as `['x', 'y']`. Alternatively, `field_names` can be a single string with each fieldname separated by whitespace and/or commas, like `'x y'` or `'x, y'`. Any valid Python identifier may be used for a fieldname except for names starting with an underscore. Valid identifiers consist of letters, digits, and underscores but do not start with a digit or underscore and cannot be a keyword such as class, for, return, global, pass, or raise.

- If `rename` is true, invalid fieldnames are automatically replaced with positional names. For example, `['abc', 'def', 'ghi', 'abc']` is converted to `['abc', '_1', 'ghi', '_3']`, eliminating the keyword `def` and the duplicate fieldname `abc`.

- `defaults` can be `None` or an iterable of default values. Since fields with a default value must come after any fields without a default, the defaults are applied to the rightmost parameters. For example, if the fieldnames are `['x', 'y', 'z']` and the defaults are (1, 2), then x will be a required argument, y will default to 1, and z will default to 2.

- If `module` is defined, `__module__` attribute of the named tuple is set to that value.

Named tuple instances do not have per-instance dictionaries, so they are lightweight and require no more memory than regular tuples.

### Collections library String subclasses

#### `collections.UserString(input_sequence)`

`UserString` is used when a user wants to create their own string with some modified or new functionality.

ts attribute `data` is a real string used to store the contents of the UserString class. The instance’s contents are initially set to a copy of `input_sequence`. `input_sequence` argument can be any object which can be converted into a string using the built-in `str()` function.

### Collections library Dict Subclasses

#### `collections.ChainMap(*maps)`

`ChainMap` groups multiple dicts or other mappings together to create a single, updateable view. If no maps are specified, a single empty dictionary is provided so that a new chain always has at least one mapping.

- The underlying mappings are stored in a list. That list is public and can be accessed or updated using the maps attribute. There is no other state.

- Lookups search the underlying mappings successively until a key is found. In contrast, writes, updates, and deletions only operate on the first mapping.

- A ChainMap incorporates the underlying mappings by reference. So, if one of the underlying mappings gets updated, those changes will be reflected in ChainMap.

- All of the usual dictionary methods are supported. In addition, there is a `maps` attribute, a method for creating new subcontexts, and a property for accessing all but the first mapping:

#### `collections.Counter([iterable-or-mapping])`

`Counter` is a dict subclass for counting hashable objects. It is a collection where elements are stored as dictionary keys and their counts are stored as dictionary values. Counts are allowed to be any integer value including zero or negative counts.

Counter class is similar to bags or multisets in other languages.

#### `collections.defaultdict(default_factory=None, /[, ...])`

If `defauly_factory` argument is not `None`, `defaultdict` is used to provide some default values for the key that does not exist and never raises a `KeyError`. However, if `defauly_factory` argument is `None`,  it behaves like a standard dictionary and raises a KeyError exception with the key as argument. The behavior for missing keys is defined by the method `__missing__(key)`.

Regular dictionaries can be used to implement same kind of functionality using `dict.get(key, [default])` function. If a default value is given, and the input key does not exist, then the default value is retured.

#### `collections.OrderedDict([items])`

`OrderedDict` has methods specialized for rearranging dictionary order.

- If a new entry overwrites an existing entry, the original insertion position is changed and moved to the end.

- Along with usual mapping methods provided by dictionaries, ordered dictionaries support reverse iteration using `reversed()`.

- Equality tests between OrderedDict objects are order-sensitive and are roughly equivalent to `list(od1.items())==list(od2.items())`.

- Equality tests between OrderedDict objects and other Mapping objects are order-insensitive like regular dictionaries. This allows OrderedDict objects to be substituted in place of a regular dictionaries.

#### `collections.UserDict([initialdata])`

`UserDict` is used when a user wants to create their own dictionary with some modified or new functionality.

Its attribute `data` is a real dictionary used to store the contents of the UserDict class. If `initialdata` is provided, data is initialized with its contents; reference to initialdata is not kept, allowing it to be used for other purposes.

---

## Built-in Array library Sequences

### `array.array(typecode[, initializer])`

`array` objects are type constrained sequences, and the type is specified at object creation time by using a type code, which is a single character.

The following type codes are defined, and are available via `array.typecodes`:

| Type code | C Type             | Python Type       | Minimum size in bytes | Notes |
| --------- | ------------------ | ----------------- | --------------------- | ----- |
| `'b'`     | signed char        | int               | 1                     |       |
| `'B'`     | unsigned char      | int               | 1                     |       |
| `'w'`     | Py_UCS4            | Unicode character | 4                     |       |
| `'h'`     | signed short       | int               | 2                     |       |
| `'H'`     | unsigned short     | int               | 2                     |       |
| `'i'`     | signed int         | int               | 2                     |       |
| `'I'`     | unsigned int       | int               | 2                     |       |
| `'l'`     | signed long        | int               | 4                     |       |
| `'L'`     | unsigned long      | int               | 4                     |       |
| `'q'`     | signed long long   | int               | 8                     |       |
| `'Q'`     | unsigned long long | int               | 8                     |       |
| `'f'`     | float              | float             | 4                     |       |
| `'d'`     | double             | float             | 8                     |       |

---

## Built-in `heapq` library and Heap implementation

### `heapq` library

`heapq` library allows implementation of heap queue or priority queue algoritshm via creation of Heaps, which are binary trees for which every parent node has a value less than or equal to any of its children -- this condition is called "<font color="#061537ff">heap invariant</font>".

Heap can be created by modifying an existing list via function `heapq.heapify(x)`.

Python Heap implementation differs from textbook heap algorithms in two aspects:

- (a) Python uses zero-based indexing. This makes the relationship between the index for a node and the indexes for its children slightly less obvious, but is more suitable since Python uses zero-based indexing.
- (b) Python Heap Queue pop method returns the smallest item, not the largest (called a “min heap” in textbooks; a “max heap” is more common in texts because of its suitability for in-place sorting).

--> These two make it possible to view the heap as a regular Python list without surprises: `heap[0]` is the smallest item, and `heap.sort()` maintains the heap invariant.

---
---
