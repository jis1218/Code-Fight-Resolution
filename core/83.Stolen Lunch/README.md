When you recently visited your little nephew, he told you a sad story: there's a bully at school who steals his lunch every day, and locks it away in his locker. He also leaves a note with a strange, coded message. Your nephew gave you one of the notes in hope that you can decipher it for him. And you did: it looks like all the digits in it are replaced with letters and vice versa. Digit 0 is replaced with 'a', 1 is replaced with 'b' and so on, with digit 9 replaced by 'j'.
The note is different every day, so you decide to write a function that will decipher it for your nephew on an ongoing basis.
Example
For note = "you'll n4v4r 6u4ss 8t: cdja", the output should be
stolenLunch(note) = "you'll never guess it: 2390".
```java
String stolenLunch(String note) {
    String result = "";
    
    for(int i=0; i<note.length(); i++){
        if(note.charAt(i)>='0' && note.charAt(i)<='9'){
           result = result.concat(String.valueOf((char)(note.charAt(i)-'0'+'a')));
        }else if(note.charAt(i)>='a' && note.charAt(i)<='j'){
            result = result.concat(String.valueOf((char)(note.charAt(i)-'a'+'0')));
        }else{
            result = result.concat(String.valueOf(note.charAt(i)));
        }
    }    
    return result;
}
```