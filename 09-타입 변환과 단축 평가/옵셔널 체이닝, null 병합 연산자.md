# 옵셔널 체이닝 연산자 (?.)

- ES11(2020)에서 도입
- 좌항 피연산자가 null 또는 undefined인 경우 → undefined 반환
- 그렇지 않으면 우항의 프로퍼티 참조 이어감

```js
var elem = null;
var value = elem?.value;
console.log(value); // undefined
```

## 기존 방식(논리곱 &&)

```js
var elem = null;
var value = elem && elem.value;
console.log(value); // null
```

## 주의할 점

- ?.는 **Falsy 값(0, ‘’, NaN, false 등)**일 때는 무시하지 않고,
- **오직 null과 undefined**만 체크한다.

```js
var str = "";
var length = str && str.length; // ''
console.log(length); // ''
```

```js
var str = "";
var length = str?.length;
console.log(length); // 0
```

# null 병합 연산자 (??)

- ES11(2020)에서 도입
- 좌항 피연산자가 null 또는 undefined → 우항 값 반환
- 그 외 값(0, ‘’, false 등)은 그대로 반환

## 예제
```js
var foo = null ?? "default string";
console.log(foo); // "default string"
```

```js
var foo = "" || "default string";
console.log(foo); // "default string"
```

문제: '', 0, false도 Falsy로 처리되어 원치 않게 기본값으로 대체됨

```js
var foo = "" ?? "default string";
console.log(foo); // ''
```

null과 undefined만 걸러내고, 나머지는 그대로 유지

## 정리

- `obj?.prop → obj`가 `null/undefined면 undefined` 반환
- 다른 Falsy 값(0, '', NaN)은 정상적으로 평가
- null 병합 사용법 (??)
- `value ?? default → value`가 null/undefined면 default 반환
- 0, '', false 같은 값은 기본값으로 대체되지 않음
