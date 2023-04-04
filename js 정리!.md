# JavaScript 완전 정리(미완, 직접 씀)

## **Array Method**

- **Array.prototype[@@iterator]()**
    
    **`@@iterator`** 속성의 초기 값은 `[values()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/values)`속성의 초기 값과 같은 함수 객체입니다.
    
    ```jsx
    arr[Symbol.iterator]()
    ```
    
    예는 몰?루
    

- **Array.prototype.at() = 지정위치 인덱스의 값 반환**
    
    `at()`메서드는 정수 값을 받아, 배열에서 해당 값에 해당하는 인덱스의 요소를 반환합니다. 양수와 음수 모두 지정할 수 있고, 음수 값의 경우 배열의 뒤에서부터 인덱스를 셉니다.
    
    ```jsx
    at(index)
    ```
    
    ```jsx
    const arrat1 = [5, 12, 8, 130, 44];
    let index = 2;
    
    console.log(Using an index of ${index} the item returned is ${array1.at(index)});
    //출력되는 것 : "Using an index of 2 the item returned is 8"
    
    index = -2;
    
    console.log(Using an index of ${index} the item returned is ${array1.at(index)});
    //출력되는 것 : "Using an index of -2 item returned is 130"
    ```
    
    주어진 인덱스가 배열에 없으면 `[undefined](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/undefined)`를 반환합니다.
    
    ```jsx
    // 대상 배열
    const cart = ['사과', '바나나', '배'];
    
    // 주어진 배열의 마지막 요소를 반환하는 함수
    function returnLast(arr) {
      return arr.at(-1);
    }
    
    // 위의 배열 'cart'에서 마지막 요소를 가져옴
    const item1 = returnLast(cart);
    console.log(item1); // '배'출력
    
    // 위의 배열 'cart'에 요소를 추가함
    cart.push('오렌지'); // 제일 뒤 쪽에 추가됨
    const item2 = returnLast(cart);
    console.log(item2); // '오렌지' 출력
    ```
    

- **Array.prototype.concat() = 배열 합성(둘 이상의 배열을 합쳐 새 배열을 반환)**
    
    **`concat()`**메서드는 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환합니다.(기존배열을 변경하지 않고, 추가된 세로운 배열을 반환한다)
    
    ```jsx
    array.concat([value1[, value2[, ...[, valueN]]]])
    ```
    
    ```jsx
    const array1 = ['a', 'b', 'c'];
    const array2 = ['d', 'e', 'f'];
    const array3 = array1.concat(array2);
    console.log(array3);
    //출력되는 거 : Array["a", "b", "c", "d", "e", "f"]
    ```
    
    ```jsx
    const num1 = [1, 2, 3];
    const num2 = [4, 5, 6];
    const num3 = [7, 8, 9];
    
    num1.concat(num2, num3);
    // 출력되는 거 : [1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```
    
    <aside>
    ⚠️ **참고:**
     배열이나 값을 이어붙여도 원본은 변하지 않으며, 새로운 배열이나 원본 배열을 조작해도 서로 영향을 받지 않습니다.
    
    </aside>
    

- **Array.prototype.copyWithin() = 인덱스 복사(복사 후 지정 위치에 덮어씀)**
    
    **`copyWithin()`**메서드는 배열의 일부를 얕게 복사한 뒤, 동일한 배열의 다른 위치에 덮어쓰고 그 배열을 반환합니다. 이 때, 크기(배열의 길이)를 수정하지 않고 반환합니다.
    
    ```jsx
    arr.copyWithin(target[, start[, end]])
    ```
    
    ```jsx
    const array1 = ['a', 'b', 'c', 'd', 'e'];
    
    // index 3에 있는 요소를 index 0로 복사한다
    console.log(array1.copyWithin(0, 3, 4));
    // 출력되는 거 : Array ["d", "b", "c", "d", "e"]
    
    // index 3부터 끝까지 모든 요소를 index 1로 복사한다.
    console.log(array1.copyWithin(1, 3));
    // 출력되는 거 : Array ["d", "d", "e", "d", "e"]
    ```
    
    - `target`
        
        복사한 시퀀스(값)를 넣을 위치를 가리키는 0 기반 인덱스. 음수를 지정하면 인덱스를 배열의 끝에서부터 계산합니다.
        
        `target`이 `arr.length`보다 크거나 같으면 아무것도 복사하지 않습니다. `target`이 `start` 이후라면 복사한 시퀀스를 `arr.length`에 맞춰 자릅니다.
        
    - `start` Optional
        
        복사를 시작할 위치를 가리키는 0 기반 인덱스. 음수를 지정하면 인덱스를 배열의 끝에서부터 계산합니다.
        
        기본값은 0으로, `start`를 지정하지 않으면 배열의 처음부터 복사합니다.
        
    - `end` Optional
        
        복사를 끝낼 위치를 가리키는 0 기반 인덱스. `copyWithin`은 `end` 인덱스 이전까지 복사하므로 `end` 인덱스가 가리키는 요소는 제외합니다. 음수를 지정하면 인덱스를 배열의 끝에서부터 계산합니다.
        
        기본값은 `arr.length`로, `end`를 지정하지 않으면 배열의 끝까지 복사합니다.
        
    
    Ex
    
    ```jsx
    [1, 2, 3, 4, 5].copyWithin(-2);
    // [1, 2, 3, 1, 2]
    
    [1, 2, 3, 4, 5].copyWithin(0, 3);
    // [4, 5, 3, 4, 5]
    
    [1, 2, 3, 4, 5].copyWithin(0, 3, 4);
    // [4, 2, 3, 4, 5]
    
    [1, 2, 3, 4, 5].copyWithin(-2, -3, -1);
    // [1, 2, 3, 3, 4]
    
    [].copyWithin.call({length: 5, 3: 1}, 0, 3);
    // {0: 1, 3: 1, length: 5}
    
    // ES2015 TypedArray는 Array의 하위 클래스
    var i32a = new Int32Array([1, 2, 3, 4, 5]);
    
    i32a.copyWithin(0, 2);
    // Int32Array [3, 4, 5, 4, 5]
    
    // 아직 ES2015를 사용할 수 없는 환경에서
    [].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
    // Int32Array [4, 2, 3, 4, 5]
    ```
    

- **Array.prototype.entries() = 약간 이해 부족**
    
    **`entries()`**메서드는 배열의 각 인덱스에 대한 키/값 쌍을 가지는 새로운 **`Array Iterator`** 객체를 반환합니다.
    
    ```jsx
    entries()
    ```
    
    ```jsx
    const array1 = ['a', 'b', 'c'];
    
    const iterator1 = array1.entries();
    
    console.log(iterator1.next().value);
    // 출력되는 거 : Array [0, "a"]
    
    console.log(iterator1.next().value);
    // 출력되는 거 : Array [1, "b"]
    ```
    
    ```jsx
    const array = ["a", "b", "c"];
    const arrayEntries = array.entries();
    
    for (const element of arrayEntries) {
      console.log(element);
    }
    // [0, 'a']
    // [1, 'b']
    // [2, 'c']
    ```
    
    ```jsx
    for (const element of [, "a"].entries()) {
      console.log(element);
    }
    // [0, undefined]
    // [1, 'a']
    ```
    
    아마 배열의 인덱스와 그 값을 반환하는 것 같다.
    

- **Array.prototype.every() = 조건에 맞으면 ture, 하나라도 다르면 전부 false (every인 이유)**
    
    **`every()`**메서드는 배열 안의 모든 요소가 주어진 판별 함수를 통과하는지 테스트합니다. Boolean 값을 반환합니다.
    
    ```jsx
    // 화살표 함수
    every((element) => { ... } )
    every((element, index) => { ... } )
    every((element, index, array) => { ... } )
    
    // 콜백 함수
    every(callbackFn)
    every(callbackFn, thisArg)
    
    // 인라인 콜백 함수
    every(function callbackFn(element) { ... })
    every(function callbackFn(element, index) { ... })
    every(function callbackFn(element, index, array){ ... })
    every(function callbackFn(element, index, array) { ... }, thisArg)
    ```
    
    ```jsx
    const isBelowThreshold = (currentValue) => currentValue < 40;
    
    const array1 = [1, 30, 39, 29, 10, 13];
    
    console.log(array1.every(isBelowThreshold));
    // 출력되는 거 : true
    ```
    

- **Array.prototype.fill() = 배열의 지정한 범위까지 지정받은 값으로 체우기**
    
    **`fill()`**메서드는 배열의 시작 인덱스부터 끝 인덱스의 이전까지 정적인 값 하나로 채웁니다.
    
    ```jsx
    arr.fill(value[, start[, end]])
    ```
    
    ```jsx
    const array1 = [1, 2, 3, 4];
    
    // 배열의 2부터 4까지 0으로 체운다
    console.log(array1.fill(0, 2, 4));
    // 출력되는 거 : Array [1, 2, 0, 0]
    
    // 배열 1부터 5로 체우기(1 ~ 끝)
    console.log(array1.fill(5, 1));
    // 출력되는 거 : Array [1, 5, 5, 5]
    
    console.log(array1.fill(6));
    // 출력되는 거 : Array [6, 6, 6, 6]
    ```
    
    <aside>
    ⚠️ **참고** : 
    시작부분 뒷 부분 부터 시작(즉, 2부터 시작했다면 3부터 숫자가 채워짐)
    
    </aside>
    
    ```jsx
    [1, 2, 3].fill(4);               // [4, 4, 4]
    [1, 2, 3].fill(4, 1);            // [1, 4, 4]
    [1, 2, 3].fill(4, 1, 2);         // [1, 4, 3]
    [1, 2, 3].fill(4, 1, 1);         // [1, 2, 3]
    [1, 2, 3].fill(4, 3, 3);         // [1, 2, 3]
    [1, 2, 3].fill(4, -3, -2);       // [4, 2, 3]
    [1, 2, 3].fill(4, NaN, NaN);     // [1, 2, 3]
    [1, 2, 3].fill(4, 3, 5);         // [1, 2, 3]
    Array(3).fill(4);                // [4, 4, 4]
    [].fill.call({ length: 3 }, 4);  // {0: 4, 1: 4, 2: 4, length: 3}
    
    // 참조에 의한 객체
    var arr = Array(3).fill({}); // [{}, {}, {}]
    arr[0].hi = "hi"; // [{ hi: "hi" }, { hi: "hi" }, { hi: "hi" }]
    ```
    

- **Array.prototype.filter() = 조건에 맞는 것만 반환**
    
    **`filter()`**메서드는 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환합니다.
    
    ```jsx
    arr.filter(callback(element[, index[, array]])[, thisArg])
    ```
    
    <aside>
    ✨ callback
    각 요소를 시험할 함수. true를 반환하면 요소를 유지하고, false를 반환하면 버립니다. 다음 세 가지 매개변수를 받습니다.
    
    element
    처리할 현재 요소.
    
    index Optional
    처리할 현재 요소의 인덱스.
    
    array Optional
    filter를 호출한 배열.
    
    thisArg Optional
    callback을 실행할 때 this로 사용하는 값.
    
    </aside>
    
    ```jsx
    const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
    
    const result = words.filter(word => word.length > 6);
    
    console.log(result);
    // 출력되는 거 : Array ["exuberant", "destruction", "present"]
    ```
    
    프로그래머스에서 사용한적 있음.
    

- **Array.prototype.find()**
    
    **`find()`**메서드는 주어진 판별 함수를 만족하는 **첫 번째 요소** 의 **값**을 반환합니다. 그런 요소가 없다면 `[undefined](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/undefined)`를 반환합니다.