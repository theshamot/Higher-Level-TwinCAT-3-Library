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
  - WIP wrapper example for List of Custom datatype. You can access object properties using dot notation `myList.Get(0).VarBOOL`.
### Sort
- Sorts array of anything using quicksort algorythm.
- Array can be sorted by ascending or descending order.
- It is designed to be able sort by nested element. That means you can sort array of structures/fbs by its member variable (e.g. You have struct describing product. Let's say one of structures variables is time it was produced. You can sort the array by this time.)
- Syntax: `Sort(array, firtElementOfArray, sortByVariable, order)`. `firstElementOfArray` points to arrays first index, `sortByVariable` points to variable you want to sort by as refered to variable from first index of array. It can be same variable as provided in `firstElementOfArray` or member of this variable. `order` is self-explanatory.
- Example syntax: Sort(sort_array, `Sort(sort_array, sort_array[0], sort_array[0].by_this.nested_variable, E_Order.ASCENDING)`

### Comparisons
- Compare functions for variables passed by __SYSTEM.AnyType description.
- Can compare numbers, times, strings and some other datatypes.

### Others
- Conversion of __SYSTEM.AnyType to String or WString
- Swap to swap byte content of any two variables with matching size
- Some general usage enumerators

---

## What's ahead. Only future will show which of these are actually possible in Tc
- ListOf\<some more types>
- List.Contains(value) : int index
- List.Sort()
- Map<Key : String, Value : ANY> based on List
- List, Map.JSON() - you could possibly backup data to file when you cannot make this retain over restart
- Strigifier - convert anything to string including fb properties. This could also contain JSONizer.
- ? Some sort of variable logger? Example: Logger.Log(__VARINFO). Using __VARINFO we can get variable name in addition to its value.