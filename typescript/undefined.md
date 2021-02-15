# 기본 타입

[이전 글](typescript-type.md)에서 TypeScript에서 타입이란 수학에서 말하는 집합이라고 하였다. 앞으로도 이 관점에서 계속 설명하도록 하겠다. 
또한 타입과 집합은 같은 의미로 혼용하여 사용하겠다. 별다른 언급이 없으면 두 가지를 동일한 것으로 보아도 좋다.

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
