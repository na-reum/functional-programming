## 기존과 달라진 ES6에서의 리스트 순회
- for i++
- for of
  
<code>
    
    const list = [1,2,3];

    // ES5
    for(var i=0; i<list.length;i++>){
        console.log(list[i]);
    }
    // ES5 유사배열
    cost stt = "abc";
     for(var i=0; i<str.length;i++>){
        console.log(str[i]);
    }   

    //ES6
    for(const a of list){
        console.log(a);
    }
    for(const a of str){
        console.log(a);
    }
</code>

### Array를 통해 알아보기
키값으로 접근 가능
<code>

    const arr = [1,2,3];
    for(const a of arr){
        console.log(a);
    }

</code>

### Set을 통해 알아보기
키값으로 접근 불가능
<code>

    const set = new Set([1,2,3]);
    for(const a of set){
        console.log(a);
    }

</code>

### Map을 통해 알아보기
키값으로 접근 불가능

_.keys(),values(),entries()또한 이터레이터를 리턴한다
<code>

    const map = new Map([["a",1],["b",2],["c",3]]);
    for(const a of map){
        console.log(a);
    }

</code>

#### for of 문은 ES5의 순회와 다르다.
그 이유로는 Set과 Map은 키값으로 접근이 불가능한데, 하나씩 순회를 했기 때문이다. 
어떻게 다를까? 

<code>

    Symbol.iterator

</code>
라는 Symbol이 있다. Symbol은 어떤 객체의 키로 사용될 수 있다. 

<code>

    const arr = [1,2,3];

    console.log(arr[Symbol.iterator]); // 함수가 있다. 

    arr[Symbol.iterator] = null; // array에 키에 접근할 수 있는 함수를 비우면

    // 순회가 되지 않는다. arr is not iterable

    // array, set, map 동일
</code>

## 이터러블/이터레이터 프로토콜
- 이터러블 : 이터레이터를 리턴하는 [Symbol.iterator] ( )를 가진 값
- 이터레이터: { value, done } 객체를 리턴하는 next()를 가진 값

    <code>

        let iterator = arr[Symbol.iterator]();

        iterator.next(); // {value:1, done: false};
        iterator.next(); // {value:2, done: false};
        iterator.next(); // {value:3, done: false};
        iterator.next(); // {value:undefined, done: true};
    </code>
- 이터러블/이터레이터 프로토콜: 이터러블을 for...of, 전개 연산자 등과 함께 동작하도록 한 규약
- 즉 Array는 Syobol.iterator 메소드를 통해서 이터레이터를 리턴하기 때문에, for of문과 잘 동작하는 이터러블 객체이고, 그리고 for of 문을 통해서 순회할 수 있기 때문에 이터러블/이터레이터 프로토콜을 따른다. 

### 사용자 정의 이터러블을 통해 알아보기

<code>

    

</code>