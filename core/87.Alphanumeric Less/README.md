An alphanumeric ordering of strings is defined as follows: each string is considered as a sequence of tokens, where each token is a letter or a number (as opposed to an isolated digit, as is the case of lexicographic ordering). For example, the tokens of a string "ab01c004" are [a, b, 01, c, 004]. In order to compare two strings, you break them down into tokens and compare corresponding pairs of tokens with each other (i.e. first token of the first string, with the first token of the second string etc).
Here is how tokens are compared:
If a letter is compared with another letter, the usual order applies.
A number is always less than a letter.
When two numbers are compared, their values are compared. Leading zeros, if any, are ignored.
If at some point one string has no more tokens left while the other one still does, the one with fewer tokens is considered smaller.
If the two strings s1 and s2 appear to be equal, consider the smallest index i such that tokens(s1)[i] and tokens(s2)[i] (where tokens(s)[i] is the ith token of string s) differ only by the number of leading zeros. If no such i exists, the strings are indeed equal. Otherwise, the string whose ith token has more leading zeros is considered less.
Here are some examples of comparing strings using alphanumeric ordering.
"a" < "a1" < "ab"
"ab42" < "ab000144" < "ab00144" < "ab144" < "ab000144x"
"x11y012" < "x011y13"
```java
boolean alphanumericLess(String s1, String s2) {
    String f1 = s1.replace("0", "");
    String f2 = s2.replace("0", "");
    
    return f1.compareTo(f2)>0?false:f1.compareTo(f2)==0&&s1.length()<=s2.length()?false:true;
}
```