# JS String

https://tc39.es/ecma262/#sec-string-objects


```js
// 전역 함수
String();

// 생성자
new String();


var str1 = String('');
var str2 = new String('');

(typeof str1 === 'string') == true
(typeof str2 === 'object') == true


var str = 'string';
var obj = new String('string');

str.key = 'value';
obj.key = 'value';

(str.key === undefined) == true
(obj.key === 'value') == true
```


프로퍼티 | 설명
---|---
length      | 문자열의 길이 반환


**메소드**
- [String.fromCharCode()](#stringfromcharcode)
- [String.fromCodePoint()](#stringfromcodepoint)
- [String.raw()](#stringraw)
- [String.prototype.charAt()](#stringprototypecharat)
- [String.prototype.charCodeAt()](#stringprototypecharcodeat)
- [String.prototype.codePointAt()](#stringprototypecodepointat)
- [String.prototype.concat()](#stringprototypeconcat)
- [String.prototype.endsWith()](#stringprototypeendwith)
- [String.prototype.includes()](#stringprototypeincludes)
- [String.prototype.indexOf()](#stringprototypeindexof)
- [String.prototype.lastIndexOf()](#stringprototypelastindexof)
- [String.prototype.localeCompare()](#stringprototypelocalecompare)
- [String.prototype.match()](#stringprototypematch)
- [String.prototype.matchAll()](#stringprototypematchall)
- [String.prototype.normalize()](#stringprototypenormalize)
- [String.prototype.padEnd()](#stringprototypepadend)
- [String.prototype.padStart()](#stringprototypepadstart)
- [String.prototype.repeat()](#stringprototyperepeat)
- [String.prototype.replace()](#stringprototypereplace)
- String.prototype.replaceAll()
- [String.prototype.search()](#stringprototypesearch)
- [String.prototype.slice()](#stringprototypeslice)
- [String.prototype.split()](#stringprototypesplit)
- [String.prototype.startsWith()](#stringprototypestartswith)
- [String.prototype.substring()](#stringprototypesubstring)
- [String.prototype.toLocaleLowerCase()](#stringprototypetolocalelowercase)
- [String.prototype.toLocaleUpperCase()](#stringprototypetolocaleuppercase)
- [String.prototype.toLowerCase()](#stringprototypetolowercase)
- String.prototype.toString()
- [String.prototype.toUpperCase()](#stringprototypetouppercase)
- [String.prototype.trim()](#stringprototypetrim)
- String.prototype.trimEnd()
- String.prototype.trimStart()
- String.prototype.valueOf()



## String.fromCharCode()

> String.fromCharCode(...codeUnit)

```js
(String.fromCharCode(48) === '0') == true
```



## String.fromCodePoint()

> String.fromCodePoint(...codePoints)

```js
(String.fromCodePoint(48) === '0') == true
```



## String.raw()

>  String.raw(template, ...substitutions)



## String.prototype.charAt()
: 문자열에서 주어진 인덱스에 위치하는 문자 반환    
: 인덱스 범위를 벗어날 경우 빈 문자열 반환

```js
var str = 'string';
(str.charAt(0) === 's') == true
(str.charAt(10) === '') == true
```



## String.prototype.charCodeAt()
: 문자열에서 주어진 인덱스에 위치하는 문자의 유니코드 반환    
: 인덱스 범위를 벗어날 경우 NaN 반환   

```js
var str = 'string';
(str.charCodeAt(0) === 115) == true
```



## String.prototype.codePointAt()
: 문자열에서 주어진 인덱스에 해당하는 문자의 코드 포인트 반환   
: 인덱스 범위를 벗어날 경우 undefined 반환   
! charCodeAt() 메소드와 동일한 기능이나 호출 형태가 다름   

```js
var str = 'string';
(str.codePointAt(0) === 115) == true
```



## String.prototype.concat()
: 문자열에 전달된 문자열을 연결한 새 문자열 반환     
: + 연산자와 동일한 기능      

> ''.concat(...args)

```js
var str = 'str'.concat('ing');
(str === 'string') == true


var a = 'a';
var b = 'b';
var c = 'c';

var str = a.concat(',', b, ',', c);
(str === 'a,b,c') == true
```



## String.prototype.endsWith()
: 문자열의 마지막 문자(열)와 주어진 문자(열)를 비교해 참이나 거짓 반환  

> ''.endsWith(searchString [, endPosition ])

```js
var str = 'string';
str.endsWith('string') == true
str.endsWith('g') == true


var str = 'st ri ng';
str.endsWith('ng') == true
str.endsWith('g') == true


var str = 's t r i n g';
str.endsWith('g') == true
```



## String.prototype.includes()
: 문자열에 주어진 문자가 포함되었는지 여부 반환

> ''.include(searchString [, position])

```js
var str = 'string';
str.includes('r') == true
str.includes('r', 3) == false
```



## String.prototype.indexOf()
: 문자열에 주어진 문자와 처음으로 일치하는 요소의 인덱스 반환  
: 해당 문자가 문자열에 없을 경우 -1 반환   

> ''.indexOf(searchString [, position])

```js
var str = 'abcabc';
(str.indexOf('a') === 0 ) == true
```



## String.prototype.lastIndexOf()
: 문자열에 주어진 문자를 뒤에서 부터 찾아 처음으로 일치하는 요소의 인덱스 반환   
: 해당 문자가 문자열에 없을 경우 -1 반환    

> ''.lastIndexOf(searchString [, position])

```js
var str = 'abcabc';
(str.lastIndexOf('a') === 3) == true
```



## String.prototype.localeCompare()
: 문자열 비교해 숫자 리터럴 반환    
: 해당 문자열이 주어진 문자열보다 앞이면 -1을 반환   
: 해당 문자열과 주어진 문자열이 같으면 0을 반환    
: 해당 문자열이 주어진 문자열보다 뒤면 1을 반환   

> ''.localeCompare(that [, reserved1 [, reserved2]])

```js
('a'.localeCompare('b') === -1) == true
('a'.localeCompare('a') === 0) == true
('b'.localeCompare('a') === 1) == true

'a'.localeCompare('b', 'en', { sensitivity: 'base' })
```



## String.prototype.match()
: 문자열에 주어진 정규식으로 검색해 일치하는 문자를 배열로 반환   

```js
var str = 'string STRIGN string';
var result = str.match(/[A-Z]/g);
(result.toString() === 'S,T,R,I,G,N') == true
```



## String.prototype.matchAll()
: 문자열에 주어진 정규식으로 검색해 일치하는 문자를 iterator로 반환   



## String.prototype.normalize()
: 문자열을 유니코드 정규화 방식에 따라 정규화하여 반환  

> ''.normalize([form])

- NFC 정규형 정준 결합 (Normalization Form Canonical Composition) -- windows, linux
- NFD 정규형 정준 분해 (Normalization Form Canonical Decomposition) -- mac
- NFKC 정규형 호환성 결합 (Normalization Form Compatibility Composition)
- NFKD 정규형 호환성 분해 (Normalization Form Compatibility Decomposition)


```js
var nfc = '\uAC01';
var nfd = '\u1100\u1161\u11A8';

(nfc.normalize('NFC') === '각') == true
(nfc.normalize('NFD') === nfd) == true

(nfc.normalize('NFD') === '각') == false
(nfc.normalize('NFD') === nfd.normalize('NFC')) == false   
```



## String.prototype.padEnd()
: 문자열에 주어진 문자를 우측 기준으로 주어진 인덱스만큼 채워 새 문자열 반환

> ''.padEnd(maxLength [, fillString])

```js
var str = '';
(str.padEnd(3, 'abc') === 'abc') == true
(str.padEnd(6, 'abc') === 'abcabc') == true

var str = 'abc';
(str.padEnd(6, '123') === 'abc123') == true
```



## String.prototype.padStart()
: 문자열에 주어진 문자를 좌측 기준으로 주어진 인덱스만큼 채워 새 문자열 반환

> ''.padStart(maxLength [, fillString])

```js
var str = '';
(str.padStart(3, 'abc') === 'abc') == true

var str = 'abc';
(str.padStart(6, '123') === '123abc') == true
```



## String.prototype.repeat()
: 문자열에 주어진 횟수만큼 문자열을 반복한 새 문자열 반환  

```js
var str = 'a';
(str.repeat(5) === 'aaaaa') == true
```



## String.prototype.replace()
: 문자열에 주어진 문자를 검색해 일치하는 처음 문자를 교체한 새 문자열 반환    
: 패턴이나 정규식 검색 가능   

```js
var str = 'string';
(str.replace('s', 'S') === 'String') == true

var str = 'string';
var result = '';

result = str.replace(/[a-z]/g , (str) => str.toUpperCase() );
result = str.replace(/[a-z]/g , String.call.bind(str.toUpperCase) );
(result === 'STRING') == true
```



## String.prototype.search()
: 문자열에 주어진 문자와 처음으로 일치하는 요소의 인덱스 반환    
: 정규식 사용 가능   

```js
var str = 'string'
(str.search('ing') === 3) == true
(str.search(/[ing]/) === 3) == true
```



## String.prototype.slice()
: 문자열에 주어진 시작 인덱스부터 종료 인덱스에 해당하는 문자열 반환    
: 음수를 사용할 경우 문자열 뒤에서 부터 시작   

> ''.slice(start, end)

```js
var str = 'string';
(str.slice(3, 6) === 'ing') == true
```



## String.prototype.split()
: 지정한 구분자를 이용해 문자열을 분리해 배열로 반환  

> ''.split(separator, limit)

```js
var str = 's t r i n g';
var result = str.split(' ');

(result.toString() === 's,t,r,i,n,g') == true
```



## String.prototype.startsWith()
: 문자열에 주어진 문자와 인덱스가 일치하면 참 반환  

> ''.startsWith(searchString [, position])

```js
var str = 'string';

str.startsWith('s', 0) == true
str.startsWith('st', 0) == true
str.startsWith('i', 3) == true
```



## String.prototype.substring()
: 문자열에 주어진 시작 인덱스부터 종료 인덱스까지 부분 문자열 반환   

> ''.substring(start, end)

```js
var str = 'string';
(str.substring(3) === 'ing') == true
(str.substring(3, 6) === 'ing') == true
```


**substring() vs slice()**
```js
var str = 'string';

(str.substring(-3) === 'string') == true
(str.slice(-3) === 'ing') == true

(str.substring(0, -3) === '') == true
(str.slice(0, -3) === 'str') == true
```



## String.prototype.toLocaleLowerCase()

> ''.toLowerCase([reserved1 [, reserved2 ]])

```js
```



## String.prototype.toLocaleUpperCase()

> ''.toLocaleUpperCase([reserved1 [, reserved2 ]])

```js
```



## String.prototype.toLowerCase()
: 문자열을 소문자로 바꾸고 반환

```js
var str = 'ABC';
(str.toLowerCase() === 'abc') == true
```


## String.prototype.toUpperCase()
: 문자열을 대문자로 바꾸고 반환  

```js
var str = 'abc'
(str.toUpperCase() === 'ABC') == true
```



## String.prototype.trim()
: 문자열의 양끝 공백을 제거한 새 문자열 반환

```js
var str = '   string   ';
(str.trim() === 'string') == true


var str = '   s t r i n g   ';
(str.trim() === 's t r i n g') == true
```



[top](#)
