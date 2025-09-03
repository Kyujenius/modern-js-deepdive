# ES5 vs ES6: var / let / const 비교

## 1. var 키워드의 한계 (ES5)
- `var`는 **함수 스코프**만 지원하고, **블록 스코프**를 지원하지 않는다.
- 이로 인해 의도치 않게 전역 변수가 생기거나, 스코프 관리가 어려워 부작용이 발생한다.
- 또한 호이스팅 시 초기값이 `undefined`로 세팅되어 예측하기 힘든 코드가 만들어질 수 있다.

---

## 2. let / const 도입 (ES6)
- `let`과 `const`는 `var`의 단점을 보완하기 위해 ES6에서 도입되었다.
- **블록 스코프**를 지원하여 더 안전하고 예측 가능한 코드 작성이 가능하다.
- ES6 이후에도 `var`는 폐기(deprecated)된 것은 아니며, 기존 코드 호환성을 위해 남아 있지만 **새로운 코드에서는 권장되지 않는다**.

---

## 3. var / let / const 비교 표

| 구분 | `var` (ES5) | `let` (ES6) | `const` (ES6) |
|---|---|---|---|
| **스코프** | 함수 스코프 | 블록 스코프 | 블록 스코프 |
| **재선언** | 가능 | 불가 | 불가 |
| **재할당** | 가능 | 가능 | 불가 |
| **호이스팅** | 선언+초기화, `undefined` 할당 | 선언만, TDZ 존재 | 선언만, TDZ 존재 |
| **전역 바인딩** | 전역 객체에 바인딩됨 (`window.varName`) | 바인딩 안 됨 | 바인딩 안 됨 |

---

## 4. 특징별 상세 설명

### 블록 스코프
```js
if (true) {
  var a = 1;
  let b = 2;
}
console.log(a); // 1
console.log(b); // ReferenceError
```

- var는 블록을 무시하고 함수 전체에 퍼짐.
- let/const는 블록 안에만 존재.

### TDZ (Temporal Dead Zone)
```js
console.log(x); // undefined
var x = 10;

console.log(y); // ReferenceError
let y = 10;

	•	var는 호이스팅되어 undefined로 초기화.
	•	let/const는 선언은 호이스팅되지만 초기화 전 접근 불가 → ReferenceError 발생.
```

### 루프 클로저 문제
```js
// var: 모두 5 출력
for (var i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 0);
}
// 5 5 5 5 5

// let: 각기 다른 값 출력
for (let i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 0);
}
// 0 1 2 3 4
```


### 전역 오염
```js
var a = 1;
console.log(window.a); // 1

let b = 2;
console.log(window.b); // undefined

	•	var는 전역 객체에 붙음 → 전역 오염 위험.
	•	let/const는 전역 객체에 바인딩되지 않음.
```


### const의 불변성
```js
const user = { name: "Lee" };
user.name = "Kim"; // OK (내부 변경 가능)
user = {};         // Error (재할당 불가)

	•	const는 재할당만 금지.
	•	객체나 배열 내부 변경은 가능 → 진짜 불변을 원하면 Object.freeze 등을 사용해야 함.
```

## 5. ES5와 ES6의 관계
- ES6는 ES5의 상위 집합(superset).
- ES6 엔진은 ES5 코드를 모두 정상 실행할 수 있다.
- ES6는 ES5의 호환성을 유지하면서 새로운 기능을 추가한 버전이다.

