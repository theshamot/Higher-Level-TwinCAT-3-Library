# Higher-Level-TwinCAT-3-Library #HL3
Library should offer set of abstract objects such as Lists or Maps common in higher lever programming languages, i.e. it is meant to easily provide some modern tools to every TwinCAT developer. It is not complex framework like [TcOpen](https://github.com/TcOpenGroup/TcOpen), although some parts of code are inspired by it 😇.

## Current status
### ListOfINT
- For now the only thing in this project
- Can only carry INT data
- Dynamically allocated elements = list has variable length
- Does not support RETAIN
- Working methods:
  - Append(int data)
  - Prepend(int data)
  - Insert(int index, int data)
  - Remove(int index)
  - Get(int index)
  - IsEmpty()
- Supports negative indexing (Get(-1) returns last element)
- Methods can be chained (myList.Append(2).Append(3).Prepend(1))
### QuickSort
- function to sort ARRAY OF REAL using QuickSort algorithm
- also contains function for easy swap of two REAL variable values

## What's ahead. Future will show which of these are actually possible in Tc
- Somehow clean, unify, correct the way ListOfINT methods are using indexes. This object will then be used as reference to develop other List objects
- List (= ListOfANY)
- ListOf\<some more types>
- List.Contains(value) : bool
- Map<Key : String, Value : ANY> based on List
- Strigifier - convert anything to string including fb properties. This could also contain JSONizer.
- ? Some sort of variable logger? Example: Logger.Log(__VARINFO). Using __VARINFO we can get variable name in addition to its value.