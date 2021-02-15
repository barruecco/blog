# TypeScript에서 Type이란?

## Type이란?

프로그래밍 언어에 대해서 이야기할 때 Type이라는 개념은 자주 등장한다. 개발자라면 익숙한 개념이다.  
하지만 Type이 무엇인에 대해서 숙고해 본 적은 드물 것이다. 이 글에서는 TypeScript에서 Type이 무언인지에 대해서 다루어 보겠다.

### Type은 집합이다.

Type은 수학에서 말하는 집합\(set\)이라고 볼 수 있다. [위키피디아](https://ko.wikipedia.org/wiki/%EC%A7%91%ED%95%A9)에 나와있는 수학에서의 집합에 대한 정의는 다음과 같다.

> 집합\(set\)은 특정한 조건에 맞는 원소들의 모임이며, 명확한 기준에 의하여 주어진 서로 다른 대상들이 모여 이루는 새로운 대상이다.

위 정의에서 `특정한 조건에 맞는` 이라는 문구는 빼야 한다. 또한 `명확한 기준에 의하여 주어진`이라는 표현도 맞지 않다. 명확한 기준 없이 아무거나 가져다 놓아도 집합이다.

[브리타니카](https://www.britannica.com/topic/set-mathematics-and-logic)의 아래 정의가 더 정확한 표현이다.

> Set, In [mathematics](https://www.britannica.com/science/mathematics) and logic, any collection of objects \(elements\), which may be mathematical \(e.g., numbers, [functions](https://www.britannica.com/science/function-mathematics)\) or not.

즉, 집합이란 원소들의 모임이다. 이 때 원소는 무엇이든 될 수 있다. \(위 문구에서 objects는 TypeScript나 JavaScript에서 말하는 objects가 아님에 유의하자.\)

### 수학적 집합

아래와 같이 MyFavoriteThings이라는 수학적 집합을 정의해 보자.

```text
MyFavoriteThings = { "TypeScript", "Java", "C++", "C#", "C" }
```

위와 같이 정의하면 MyFavoriteThings는 수학에서 말하는 집합의 정의에 부합한다. MyFavoriteThings는 원소로써 "TypeScript", "Java", "C++", "C\#", "C"를 갖는다.

{% hint style="info" %}
모든 수학적 집합을 TypeScript에서 표현할 수 있는 것은 아니다. TypeScript에서 표현할 수 있는 집합은 프로그램적으로 의미있는 집합들 뿐이다.
{% endhint %}

### TypeScript에서의 집합

그렇다면 MyFavoriteThings이라는 집합을 TypeScript 내에서는 어떻게 정의할 수 있을까?

아래와 같이 하면 된다.

```typescript
type MyFavoriteThings = "TypeScript" | "Java" | "C++" | "C#" | "C"
```

TypeScript에서 `type`이라는 키워드는 type\(혹은 집합\)을 정의할 때 쓰는 키워드이다. `type` 키워드는 TypeScript의 매력 포인트 중에 하나이다. TypeScript에서는 `type` 키워드를 이용하여 type 자체를 정의하거나 다룰 수 있는데 다른 프로그래밍 언어에서는 보기 드문 특성이다.

위 코드블럭에서 `|` 는 마치 수학의 집합에서 사용하는 합집합 기호와 같은 역할을 한다.

수학에서 집합 **A**와 집합 **B**과 있을 때, 이 둘의 합집합은 아래와 같이 나타낸다.

$$
A \cup B
$$

위 코드블럭에서의 MyFavoriteThigs이라는 type은 각각 원소수가 각각 1개인, 다섯 집합의 합집합이다.

자, 그럼 이제 우리가 정의한 MyFavoriteThings라는 type이 어떻게 사용되는지 보자.

### type의 사용

TypeScript에서는 변수를 선언할 때, 아래와 같이 변수의 이름 뒤에 콜론과 함께 type을 적는다.

```typescript
let thing: MyFavoriteThings
```

위와 같이 변수의 type을 선언함으로써 변수가 가질 수 있는 값을 MyFavoriteThings의 원소로 한정할 수 있다. 즉, thing에는 "TypeScript", "Java", "C++", "C\#", "C" 다섯가지만 할당이 가능하다.

예를 들어 아래와 같이  변수 thing에 "Python"을 할당하게 되면 TypeScript의 컴파일러는 컴파일시에 오류를 뱉는다. "Python"은 MyFavoriteThings의 원소가 아니기 때문이다.

```typescript
thing = "Python" // 컴파일 에러
```

컴파일 오류는 아래와 같다.

```text
Type '"Python"' is not assignable to type 'MyFavoriteThings'.
```

### type a = "TypeScript" 와 let b = "TypeScript"의 차이 

```typescript
type a = "TypeScript"
let b = "TypeScript"
```

TypeScript에서의 Type을 잘 이해하려면 위의 코드블럭에서 1번 줄과 2번줄의 차이를 명확히 구분할 수 있어야 한다. 

1번 줄에서는 오직 "TypeScript"만을 원소로 갖는 집합 a를 선언한 것이다.  2번 줄에서는 변수  b를 선언하고 그 값으로 "TypeScript"를 넣어 주었다.  

아래와 같이 b를 선언할 때 a 타입으로 선언할 수도 있다.

```typescript
type a = "TypeScript"
let b:a = "TypeScript"
```

어떤 변수를 a 타입으로 선언하고 "TypeScript" 이외의 값을 할당한다면 컴파일 오류가 발생한다.

```typescript
let c:a = "JavaScript" // 컴파일 에러
```

### 정리

* TypeScript에서의 type은 수학에서의 집합으로 바라볼 수 있다.
* TypeScript에서 변수의 type을 지정한다는 것은 그 변수가 갖을 수 있는 값을 해당 type의 원소로 한정한다는 뜻이다.

다음 글에서는 TypeScript에서 `type` 키워드를 이용하여 다양하게 집합을 정의하는 방법에 대해서 다루어 보겠다.

