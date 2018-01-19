# 数组

#### ES7 中判断一个数组是否包含另一个数组

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

# cookie

####原生JavaScript的cookie操作

> 来自《JavaScript高级程序设计》第三版，Page 631。

```js
var CookieUtil = {
  
	// 读取
    get: function (name){
        var cookieName = encodeURIComponent(name) + "=",
            cookieStart = document.cookie.indexOf(cookieName),
            cookieValue = null,
            cookieEnd;
            
        if (cookieStart > -1){
            cookieEnd = document.cookie.indexOf(";", cookieStart);
            if (cookieEnd == -1){
                cookieEnd = document.cookie.length;
            }
            cookieValue = decodeURIComponent(document.cookie.substring(cookieStart + cookieName.length, cookieEnd));
        } 

        return cookieValue;
    },
  
    // 写入
    set: function (name, value, expires, path, domain, secure) {
        var cookieText = encodeURIComponent(name) + "=" + encodeURIComponent(value);
    
        if (expires instanceof Date) {
            cookieText += "; expires=" + expires.toGMTString();
        }
    
        if (path) {
            cookieText += "; path=" + path;
        }
    
        if (domain) {
            cookieText += "; domain=" + domain;
        }
    
        if (secure) {
            cookieText += "; secure";
        }
    
        document.cookie = cookieText;
    },
  
    // 删除
    unset: function (name, path, domain, secure){
        this.set(name, "", new Date(0), path, domain, secure);
    }

};
```

#### jquery-cookie

> 来自:  https://github.com/carhartl/jquery-cookie

```js
// Create session cookie:

$.cookie('name', 'value');

// Create expiring cookie, 7 days from then:

$.cookie('name', 'value', { expires: 7 });

// Create expiring cookie, valid across entire site:

$.cookie('name', 'value', { expires: 7, path: '/' });

// Read cookie:

$.cookie('name'); // => "value"
$.cookie('nothing'); // => undefined

// Read all available cookies:

$.cookie(); // => { "name": "value" }

// Delete cookie:

// Returns true when cookie was successfully deleted, otherwise false
$.removeCookie('name'); // => true
$.removeCookie('nothing'); // => false

// Need to use the same attributes (path, domain) as what the cookie was written with
$.cookie('name', 'value', { path: '/' });
// This won't work!
$.removeCookie('name'); // => false
// This will work!
$.removeCookie('name', { path: '/' }); // => true
```

