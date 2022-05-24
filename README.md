# Higher-Level-TwinCAT-3-Library #HL3
Library should offer set of abstract objects such as Lists or Maps common in higher lever programming languages, i.e. it is meant to easily provide some modern tools to every TwinCAT developer.

I would like to thank [Jakob Sagatowsky](https://github.com/sagatowski) and [TcOpen](https://github.com/TcOpenGroup/TcOpen) for their opensource projects as I use them to gather knowledge and are inpiration for me. Thx!

---

## Current status
### Lists
- Dynamically allocated elements = list has variable length
- Does not support RETAIN
- Methods:
  - `Append(data)`
  - `Prepend(data)`
  - `Insert(int index, data)`
  - `Get(int index)`
  - `Remove(int index)`
  - `RemoveAll()`
  - `IsEmpty()`
- Supports negative indexing (Get(-1) returns last element)
- Methods can be chained (myList.Append(2).Append(3).Prepend(1))
- Project contains PRGs with example usages of methods
- ListOfINT can only carry INT data
- ⭐List⭐(of ANY)
  - Can carry ANY datatype you send in
  - Upon adding the first data to List it remembers its datatype. When adding another data to list it checks its datatype and if it is valid it continues by adding the data.
  - It can recognize primitive datatypes. ❗All structures and FBs are recognized as USERDEF datatypes and are only compared based on its byte size❗
  - Only variables can be passed as data. i.e. you cannot do ~~`Append(5)`~~, you can only `Append(myVariable)`
  - When retrieving data from List using `Get(int index, ANY destinationVariable)` function you also pass the variable you want to write data to. The variable is checked on its compatibility and if datatype is valid then data are written into the variable.
  - ❗When adding or retrieving data from List the datatype is checked. If the datatype is not valid it will RETURN without doing anything❗
### QuickSort
- Function to sort ARRAY OF REAL using QuickSort algorithm
- Also contains function for easy swap of two REAL variable values

---

## What's ahead. Only future will show which of these are actually possible in Tc
- ListOf\<some more types>
- List.Contains(value) : int index
- List.Sort()
- Map<Key : String, Value : ANY> based on List
- List, Map.JSON() - you could possibly backup data to file when you cannot make this retain over restart
- Strigifier - convert anything to string including fb properties. This could also contain JSONizer.
- ? Some sort of variable logger? Example: Logger.Log(__VARINFO). Using __VARINFO we can get variable name in addition to its value.