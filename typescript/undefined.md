# 기본 타입

[이전 글](typescript-type.md)에서 TypeScript에서 타입이란 수학에서 말하는 집합이라고 하였다. 앞으로도 이 관점에서 계속 설명하도록 하겠다. 
또한 타입과 집합은 같은 의미로 혼용하여 사용하겠다. 별다른 언급이 없는 한 두 가지를 동일한 것으로 보아도 좋다.

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
즉, 아래와 같이 boolean 타입의 원소가 아닌 다른 값을 입력하면 오류가 발생한다.

```typescript
isRight = 7; // 7은 boolean 타입의 원소가 아니기 때문에 오류 발생
```


