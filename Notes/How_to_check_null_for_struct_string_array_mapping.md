## Empty of Struct, String, Array or Mapping

There is no concept of NULL in solidity. Empty of a struct, string, array or mapping in solidtiy is treated as zero-value of each type, e.g. zero of unit type is 0.

# string
Normally, a empty string means its length is 0. But unfortunately, string in solidity has no attribute or function to retrieve its length. Two following ways can be used to accomplish this:
```
string x;
if(bytes(x).legth == 0) {......}
// is empty
```
or 
```
string x; 
if (sha3(x) != sha3("")) {......}
// is not empty
```

# struct
In solidity, a struct does not need to be new'ed for its members to be accecible, where all the members are empty.
```
struct Transaction {
  address to;
  unit256 value;
  bytes data;
}
Transaction private tx;
```
Members of tx can be accessable even tx has been assigned a value. tx.to has its zero-value: 0.

# array and mapping
Array and mapping are accessable immediately after declaration.
```
mapping(string =>Transaction ) txMapping;
...
if （txMapping["xx"].value == 0） ｛......｝
```
Although the Transaction struct object txMapping[“xx”] has not been assigned, the 'value' member of this 'virtual' object can be accessed directly.


