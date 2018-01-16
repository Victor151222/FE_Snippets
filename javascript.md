#### ES7中判断一个数组是否包含另一个数组

```js
function isContain(arr1,arr2){  
    for (var i = arr2.length - 1; i >= 0; i--) {  
        if(!arr1.includes(arr2[i])){  
            return false;  
        }  
    }  
    return true;  
} 
```

