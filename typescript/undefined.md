# 기본 타입

[이전 글](typescript-type.md)에서 TypeScript에서 타입이란 수학에서 말하는 집합이라고 하였다. 앞으로도 이 관점에서 계속 설명하도록 하겠다. 
또한 타입과 집합은 같은 의미로 혼용하여 사용하겠다. 별다른 언급이 없으면 두 가지를 동일한 것으로 보아도 좋다.

프로그래밍에서 `x는 number 타입이다.`라는 식의 표현이 있다. 
이 말을 타입은 집합이다라는 관점에서 더욱 정확히 표현하면 `x는 number 타입의 원소이다.`가 된다.
여기서는 용어를 엄밀히 사용하기 위해서 후자의 표현을 쓰도록 하겠다.


## Boolean
Boolean 타입은 오직 `true`와 `false`, 두 개의 원소를 갖는 집합이다.

```text
boolean = { true, false }
```

실제 코드에서는 아래와 같이 사용하면 된다.

```typescript
let isRight: boolean = true;
```

위 코드에서 `isRight` 변수는 boolean 타입으로 선언되었다. 그 의미는 `isRight` 변수에는 boolean 타입의 원소들 밖에는 할당할 수 없다는 뜻이다.
아래와 같이 boolean 타입의 원소가 아닌 다른 값을 입력하면 오류가 발생한다.

```typescript
isRight = 7; // 7은 boolean 타입의 원소가 아니기 때문에 오류 발생
```

## Number
TypeScript에서 숫자를 나타내는 타입은 number이다.
(물론 숫자를 나타내는 타입으로는 bigint 타입도 있다. bigint 타입은 number 타입으로 정확히 나타낼 수 없는 2^53-1보다 큰 정수들을 나타내기 위해 쓰인다.)

```typescript
let val: number = 7;
```

>boolean 타입은 원소 나열법으로 완전하게 나타낼 수 있다. 하지만 number 타입은 원소 나열법이나 조건 제시법으로 완전히 나타내기가 힘들다.
이 부분에서는 대충 각자의 경험으로 number 타입의 원소가 무엇인지 느끼도록 하자. 
JavaScript에서의 number에 대해서는 JavaScript에 대한 글에서 자세히 다루도록 하겠다.

## String
string 타입의 원소는 흔히 말하는 문자열이다.
큰 따옴표(")나 작은 따옴표(') 사이에 표현하는 데이터들이다. 백틱(`)을 양 끝에 두고 표현할 수도 있다.

```typescript
let name: string = "Hong, Gil-Dong";
let name2: string = 'Lee, Su-Yung';
let name3: string = `I-U`;
```

## Array
배열은 순서가 있는 원소들의 모임이다. 이때 원소는 아무 타입의 원소나 될 수 있다. 
즉, TypeScript에서 표현할 수 있는 어떤 타입(집합)의 원소이든 배열의 원소가 될 수 있다.

대부분의 경우에 Array의 원소들은 한가지 타입인 경우가 많다. 예를들어 각 원소가 number 타입인 경우 아래와 표현한다.

```typescript
let arr: number[] = [1,2,3];
```

`number[]`은 `Array<number>`와 완전히 동일한 의미를 같는다. 즉, 같은 타입을 의미한다.

```typescript
let arr: Array<number> = [1,2,3];
``` 

## Tuple
원래 JavaScript에는 Tuple이라는 개념이 없다. TypeScript에서만 있는 가상적인 타입이다.
Tuple 타입은 Array 타입의 subtype이다. 즉, 부분 집합이다.

Tuple은 원소수가 한정된 Array라고 볼 수 있다. 아래와 같이 타입을 정의한다.

```typescript
let tup: [number, string] = [0, "zero"];
```
위 코드블럭에서 `tup` 변수는 Tuple 타입이다. 길이가 2인 배열이고 첫 번째 원소는 number 타입에 속하고 두 번째 원소는 string 타입에 속한다.
`tup` 변수에는 항상 길이 2인 배열만 할당해야 한다. 또한 배열의 첫 번째 원소는 number, 두 번째 원소는 string이어야 한다.

```typescript
tup = ["zero", true]; // 오류 발생
```
위와 같이 `[number, string]` 타입이 아닌 값을 할당하면 오류가 발생한다. 
