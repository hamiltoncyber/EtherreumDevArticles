## How to Check Wether a Struct, String, Array or Mapping is Empty

There is no such concept of NULL in solidity. Then how can we check that a struct, string, array or mapping is empty? 
Normally, empty in solidtiy can be explained or understood, and treated as zero-value of each type, e.g. zero of unit type is 0.

# String
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
empty
```



