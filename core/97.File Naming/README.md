You are given an array of desired filenames in the order of their creation. Since two files cannot have equal names, the one which comes later will have an addition to its name in a form of (k), where k is the smallest positive integer such that the obtained name is not used yet.
Return an array of names that will be given to the files.
Example
For names = ["doc", "doc", "image", "doc(1)", "doc"], the output should be
fileNaming(names) = ["doc", "doc(1)", "image", "doc(1)(1)", "doc(2)"].

##### 다른 풀이를 봐도 내 풀이가 가장 깔끔하고 군더더기가 없다.
```java
String[] fileNaming(String[] names) {
    for(int i=1; i<names.length; i++){
        String temp = "";
        int num = 1; 
        for(int j=0; j<i; j++){                       
            if((names[i].concat(temp)).equals(names[j])){
                temp = "(" + num + ")";
                num++;
                j=-1; //j를 -1로 해줘야 다음에 0이 된다.
            }                      
        }
        names[i] += temp;
    }    
    return names;
}
```

##### 예전에 푼거... 접근 방식은 거의 비슷하다.
```java
String[] fileNaming(String[] names) {

    String temp = "";
    boolean tag = true;
    boolean anotag = false;

    for(int i=1; i<names.length; i++){
        tag = true;
        int num = 1;
        temp = names[i];
        while(tag){
            anotag = false;
            for(int j=0; j<i; j++){
                if(temp.equals(names[j])){
                    temp = names[i] + "("+ num + ")";
                    num++;
                    anotag = true;
                }
            }
            /**
            * 파일 이름이 같은 것이 없을 때 while 문을 그만 돌게 한다.
            * 같은 것이 있으면 처음부터 다시 찾는다.
            **/
            if(!anotag) tag = false;
        }
            names[i] = temp;
    }
    return names;    
}
```