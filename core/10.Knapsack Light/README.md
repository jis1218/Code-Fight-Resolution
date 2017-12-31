You found two items in a treasure chest! The first item weighs weight1 and is worth value1, and the second item weighs weight2 and is worth value2. What is the total maximum value of the items you can take with you, assuming that your max weight capacity is maxW and you can't come back for the items later?
Note that there are only two items and you can't bring more than one item of each type, i.e. you can't take two first items or two second items.
Example
For value1 = 10, weight1 = 5, value2 = 6, weight2 = 4 and maxW = 8, the output should be
knapsackLight(value1, weight1, value2, weight2, maxW) = 10.
You can only carry the first item.
For value1 = 10, weight1 = 5, value2 = 6, weight2 = 4 and maxW = 9, the output should be
knapsackLight(value1, weight1, value2, weight2, maxW) = 16.
You're strong enough to take both of the items with you.
For value1 = 5, weight1 = 3, value2 = 7, weight2 = 4 and maxW = 6, the output should be
knapsackLight(value1, weight1, value2, weight2, maxW) = 7.
You can't take both items, but you can take any of them.

```java
/**
* 경우의 수가 5가지가 나오는데 그것을 다 고려해준다.
**/
int knapsackLight(int value1, int weight1, int value2, int weight2, int maxW) {
    if(weight1+weight2<=maxW){
        return value1+value2;
    }else{
        if(weight1>maxW && weight2>maxW){
            return 0;
        }else if(weight1>maxW){
            return value2;
        }else if(weight2>maxW){
            return value1;
        }else{
            return max(value1, value2);
        }
    }
}

int max(int a, int b){
    if(a>=b){
        return a;
    }else{
        return b;
    }
}
```

##### 가장 득표수를 많이 받은 풀이
```java
int knapsackLight(int value1, int weight1, int value2, int weight2, int maxW) {
    int val = 0;

    if (weight1 + weight2 <= maxW) return value1 + value2;

    if (weight1 <= maxW) {val = value1;}

    if (weight2 <= maxW && value2 > val) val = value2;

    return val;

}
```

##### 아름다운 풀이다.
