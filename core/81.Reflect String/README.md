Define an alphabet reflection as follows: a turns into z, b turns into y, c turns into x, ..., n turns into m, m turns into n, ..., z turns into a.
Define a string reflection as the result of applying the alphabet reflection to each of its characters.
Reflect the given string.
Example
For inputString = "name", the output should be
reflectString(inputString) = "mznv".
```java
String reflectString(String inputString) {
    String result = "";
     char c;    
    for(int i=0; i<inputString.length(); i++){        
        c = (char)('z'-inputString.charAt(i)+'a');        
        result = result.concat(String.valueOf(c)); 
    }
    return result;
}
```