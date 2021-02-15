# TypeScript, 왜 써야 하나?

## 동적 타입 언어인 JavaScript

JavaScript는 대표적인 동적 타입\(Dynamic typed language\) 언이다. C계열 언어와는 다르게 변수 선언시 type을 지정할 필요가 없다. 

```javascript
let myName = "Hong, Gil-Dong"
```

위 코드블럭에서 myName이라는 변수를 선언하고 "Hong, Gil-Dong"이라는 값으로 초기화를 했는데 myName이라는 변수의 타입이 무엇인지는 지정할 필요도 지정할 수도 없다. 

아래와 같이 myName에 number 값을 입력해도 아무런 문제가 되지 않는다.

```javascript
myName = 4
```

C계열 언어에서는 변수 생성시 항상 타입을 명시하기 때문에 위와 같은 코딩이 불가능하다. 하자만 JavaScript는 동적 타입 언어이기 때문에 변수에 어떠한 타입의 값이든 넣을 수 있다.

### 동적 타입 언어의 단점

동적 타입 언어도 나름 장점이 있겠지만 단점도 만만치 않다. 사실 프로그래밍을 할 때, 어떤 변수에 가끔은 문자열 값을 넣고, 또 가끔은 숫자 값을 넣을 일은 별로 없다. 특히 우리나라에서는 거의 모두 C계열 언어를 먼저 배우고 JavaScript를 배우기 때문에 변수의 타입을 한정하여 생각하는 것이 내재화 되어 있다. 

변수의 타입에 제한이 없이 아무 값이나 할당할 수 있는 성질 때문에 골치 아픈 일이 많이 생긴다. 예를 들어 배열 값만을 가져야 하는 변수에 실수로 숫자 값이나 문자열을 넣을 수도 있다. JavaScript에서는 언어의 생리상 이것이 전혀 문제 될 것이 없기 때문에 실제로 돌려보기 전에는 개발자에게 어떠한 경고를 하지 않는다. 예를 들어 아래와 같이 코딩했다고 해보자.

```javascript
let names = ["철수", "영이", "영수"]

names = "길동" // 실수로 배열 값을 가지도록 의도한 names 변수에 문자열을 할당

names.forEach( name => 
        {
                console.log(name)
        }
    ) 
    // names가 배열이 아니기 때문에 실행시에 오류가 발생 할 것이지만 
    // 실제 돌려보기 전에 개발자는 어떠한 경고도 받지 못한다.
```

개인 프로젝트에서도 위와 같은 오류는 셀 수 없이 많이 발생할 수 있다. 하지만 개발자는 직접 돌려보기 전에는 intelliJ나 VS code와 같은 IDE로부터 어떠한 경고도 받을 수 없다. 

동적 타입언어는 다른 사람이 써 놓은 코드를 읽는 것도 더 어렵게 만든다. 변수의 타입은 지정한다는 것은 코드 자체에 엄청난 정보를 심어 놓는 것이다. 타입에 대한 정보가 없다는 것은 그만큼 많은 정보가 코드에서 빠져 있다는 뜻이다. 예를 들어 아래와 같은 function이 있다고 해보자.

```javascript
function someFunc(input) {
    // some logics
    // .
    // .
    return output
}
```

간단하게 input을 넣고 output을 리턴하는 function이다. 하지만 input과 output의 타입이 정의되어 있지 않으니 실제 로직을 살펴 보기 전에는 이 function이 무슨 일을 하는 것인지 전혀 알 수가 없다. 만약 이 function이 동료 개발자가 만든 것이고 나는 가져다 쓰는 입장이라면 더 난감할 것이다. 

### TypeScript의 이점

이제 TypeScript에서 타입을 지정하는 방식을 이용하여 input과 output의 타입을 명시해 보자.

```typescript
function someFunc(input: string):number {
    // some logics
    // .
    // .
    return output
}
```

TypeScript의  타입 표기법을 이용하여 input의 타입은 string, return 값의 타입은 number로 지정하였다. 이제 function의 파라미터 타입과 리턴 값의 타입만 보고도 다음과 같이 추론할 수 있다.

> 이 함수는 input 값을 넣어서 number를 리턴해주는 함수구나. input의 길이를 리턴해주는 함수일까? 아니면 input 안에 들어 있는 특정 캐릭터의 갯수를 세는 문자일까?

타입을 명시할 수 있다는 것은 단순히 function에 대한 많은 정보를 주는 것 뿐만 아니라 아래와 같은 코딩시의 실수도 줄일 수 있다.

```typescript
let input = 7
let inputLength = someFunc(input) // 오류 발생 
```

someFunc 함수는 string 타입의 변수만 파라미터로 받기 때문에 위와 같이 코딩하면 IDE에서 오류를 미리 알려 준다. 만일 TypeScript를 쓰지 않았다면 직접 돌려보기 전에는 오류가 있는지 알 수 없다.

 이렇게 TypeScript를 쓰게 되면 개발시에 발생할 수 있는 수 많은 오류들을 미리 차단할 수 있고 프로그램의 구조에 대해서 더 잘 이해할 수 있다.

TypeScript의 공식 홈페이지에 가면 `Typed JavaScript at any scale`이라는 문구가 있다. 즉, 어느 규모의 프로젝트에서 사용 가능한 언어라는 뜻이다. 기존의 JavaScript만 가지고는 대규모 프로젝트를 진행하는 것이 매우 힘들었을 것이다.\(나도 경험해본 적은 없다.\)

### TypeScript 배울까 말까?

Node.js, Express.js NestJs 등으로 인해서 JavaScript의 영역이 Backend까지 확대 되었고 이제는 명실공히 Java와 어깨를 나란히 할 만한 언어이다. 하지만 JavaScript는 대규모 프로젝트에는 적합하지 않다고 보는 시각이 있다. TypeScript를 사용한다면 대규모 프로젝트도 무리없다. 

언젠가 한번은 어느 외국 블로그에서 굳이 왜 TypeScript를 써야 하는지 모르겠고 너무 불편하다고 토로하는 글을 본 적이 있다. 물론 TypeScript를 쓰게 되면 타입에 대한 정보를 입력해야 하므로 작업량이 늘어 난다. Type을 정의하기 위해서 들어가는 노력은 IDE의 자동 완성 기능이 주는 유용함으로 상쇄된다. 대규모 프로젝트에서는 필수적이며, 소규모 개인 프로젝트에서도 이왕이면 쓰는 것이 훨씬 좋다. 

