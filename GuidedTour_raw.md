# Swift 견학(A Swift Tour)

<!-- Tradition suggests that the first program in a new language should print the words “Hello, world!” on the screen. -->
전통적으로 새로운 컴퓨터 연어의 첫 번째 프로그램은 화면에 “Hello, world”라는 두 단어를 인쇄하는 것입니다.
In Swift, this can be done in a single line:
Swift에서는, 이를 코드 단 한 줄로 구현할 수 있습니다:

``` swift
print("Hello, world!")
```

<!-- If you have written code in C or Objective-C, this syntax looks familiar to you—in Swift, this line of code is a complete program. -->
만약 여러분이 C나 Objective-C으로 코드를 작성해본 적이 있다면, 여러분에게 이 문법(syntax)은 친숙하게 보일 겁니다 -  Swift에서, 이 코드 (한) 줄은 완전한 프로그램입니다.
<!-- You don’t need to import a separate library for functionality like input/output or string handling. -->
입/출력 또는 문자열을 다루는 것과 같은 ‘컴퓨터의 모든 기능(functionality)’을 위하여 개별적인(separate) 라이브러리를 임포트(import)할 필요는 없습니다.
<!-- Code written at global scope is used as the entry point for the program, so you don’t need a main() function. -->
전역 범위(Global scope)로 쓰여진 코드는 그 프로그램을 위한  진입점(entry point)로 사용되므로, 여러분은  main() 함수를 사용할 필요가 없습니다.
<!-- You also don’t need to write semicolons at the end of every statement. -->
또한 모든 문장 끝에 세미콜론(즉 ;)을 쓸 필요도 없습니다.

<!-- This tour gives you enough information to start writing code in Swift by showing you how to accomplish a variety of programming tasks. -->
이 견학(tour)은 여러분에게 다양한 ‘프로그램을 짤 과제(programming task)’들을 수행하는 방법을 보여줌으로써 Swift으로 코드 작성을 시작하기 위한 충분한 정보를 제공하고자 합니다.
<!-- Don’t worry if you don’t understand something—everything introduced in this tour is explained in detail in the rest of this book. -->
이해하지 못 하는 것이 있다고 해서 걱정하지 마세요—이 견학에서 소개하는 모든 것들은 이 책의 나머지 부분에서 자세히 설명할 것입니다.

<!-- NOTE -- >
> 주의(NOTE):
<!-- For the best experience, open this chapter as a playground in Xcode. Playgrounds allow you to edit the code listings and see the result immediately. --> 
> 가장 좋은 경험을 하기 위해서는, Xcode 안에 있는 Playground으로 이 장을 열어보세요. Playground는 여러분들에게 코드를 수정하는 즉시 그 결과를 볼 수 있게 해줄 것입니다.
> <a href="https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.playground.zip">Playground 다운 받기</a>


## 간단한 값들(Simple Values)

<!-- Use let to make a constant and var to make a variable. -->
‘let’을 사용해서 상수(constant)를 만들고 `var`을 사용하여 변수를 만듭니다.
<!-- The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once. -->
상수의 값은 컴파일 할 때에 알 필요가 없지만, 그러나 여러분은 정확하게 한번만 그 값을 부여(assign)해야 합니다.
<!-- This means you can use constants to name a value that you determine once but use in many places. -->
이는 특정 값에 이름 붙이기 위하여 한번 상수를 사용할 수 있지만, 여러 곳에서 이를 사용할 수 있다는 것을 의미합니다.

``` swift
var myVariable = 42
myVariable = 50
let myConstant = 42
```

<!-- A constant or variable must have the same type as the value you want to assign to it. -->
상수나 변수는 여러분이 그것들에게 부여하기 원하는 값과 같은 타입(type)을 가져야 합니다.
<!-- However, you don’t always have to write the type explicitly. -->
그러나, 그 타입을 항상 명시적으로 작성할 필요는 없습니다.
<!-- Providing a value when you create a constant or variable lets the compiler infer its type. -->
상수나 변수를 여러분이 상수나 변수를 만들 때 할당한 값을 통해 컴파일러는 해당 값의 타입을 추측합니다. 
<!-- In the example above, the compiler infers that ‘myVariable’ is an integer because its initial value is an integer. -->
위의 예에서, `myVariable`은 처음 값이 정수였기 때문에 컴파일러는 그것을 정수라고 추론합니다(infers).

<!-- If the initial value doesn’t provide enough information (or if there is no initial value), specify the type by writing it after the variable, separated by a colon. -->
만약 그 처음 값이 충분한 정보를 제공하지 못 한다면(또는 처음 값이 존재하지 않는다면), 그 변수 뒤에, 콜론으로 분리하여, 그 타임을 써줘야 합니다.

``` swift
let inplicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double  = 70
```

> 실험(EXPERIMENT):
<!-- Create a constant with an explicit type of Float and a value of 4. -->
> 명확한(explicit) `Float` 타입이면서 4라는 값을 가진 상수를 창조해 보세요.

<!-- Values are never implicitly converted to another type. -->
값들을 결코 절대적으로 다른 타입으로 바꿀 수 없다.
<!-- If you need to convert a value to a different type, explicitly make an instance of the desired type. -->
만약 여러분들이 특정값을 다른 타입으로 바꿀 필요가 있다면, 명확하게 의도한 타입의 인스턴스(instance)를 만들어야 합니다.

``` swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
```
> 실험(EXPERIMENT):
<!-- Try removing the conversion to `String` from the last line. What error do you get? -->
> 마지막 줄에서 `String` 타입으로 변환하는 부분을 제거해보자. 어떤 에러가 발생하는가?

<!-- There’s an even simpler way to include values in strings: Write the value in parentheses, and write a backslash (\) before the parentheses. For example: -->
문자열 안에 값들을 포함하는 더 쉬운 방법이 있습니다: 괄호 안에 그 값을 쓰고 그 괄호 앞에 백슬래시(\)를 쓰면 됩니다. 예를 들면 다음과 같습니다:

``` swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```

> 실험(EXPERIMENT):
<!-- Use `\()` to include a floating-point calculation in a string and to include someone’s name in a greeting. -->
> `\()` 를 이용해 문자열 안에 ‘실수형(floating-point)’ 계산을 포함하도록 해보고, 인사말 안에 누군가의 이름을 넣어보자.

<!-- Create arrays and dictionaries using brackets ([]), and access their elements by writing the index or key in brackets. -->
배열(array)과 딕셔너리(dictionary)는 대괄호([])를 이용해 창조하고, 그리고 대괄호 안에 인덱스(index)나 키(key)를 써서 (배열과 딕셔너리의) 각 요소을 입출력한다.
<!-- A comma is allowed after the last element. -->
콤마(즉 ,)은 맨 마지막 요소뒤에 허락된다.

``` swift
var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"
 
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
```

<!-- To create an empty array or dictionary, use the initializer syntax. -->
빈 배열이나 빈 딕셔너리를 창조하려면, (다음과 같이) 초기화(initializer) 문법를 사용하면 됩니다.

``` swift
let emptyArray = [String]()
let emptyDictionary = [String: Float]()
```

<!-- If type information can be inferred, you can write an empty array as [] and an empty dictionary as [:]—for example, when you set a new value for a variable or pass an argument to a function. -->
만약 타입 정보를 추론할 수 없다면, 여러분들은 빈 배열을 []로 빈 딕셔너리을 [:]로 표기할 수 있습니다—예를 들어, 변수에 새로운 값을 할당하거나 또는 함수에 인자(argument)로 전달할 때 다음과 같이 한다.

``` swift
shoppingList = []
occupations = [:]
```
## 흐름 제어(Control Flow)
<!-- Use `if` and `switch` to make conditionals, and use `for-in`, `for`, `while`, and `repeat-while` to make loops. -->
`if`와 `switch`를 사용해서 조건문을 만들 수 있고, `for-in`, `for`, `while`, `repeat-while`을 사용해서 반복문(loops)을 만들 수 있습니다.
<!-- Parentheses around the condition or loop variable are optional. -->
조건문과 반복문을 괄호로 감싸는 것은 선택사항(optional)입니다.
<!-- Braces around the body are required. -->
중괄호({,})로 (조건문과 반복문의) 본체(body)를 감싸는 것은 필수입니다.

``` swift
let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore)
```
In an `if` statement, the conditional must be a Boolean expression—this means that code such as `if score { ... }` is an error, not an implicit comparison to zero.
`if`문장 안에서, 조건문은 꼭 불리언(Boolean) 표현이어야 합니다— 이는 `if score {...}`와 같은 코드가 에러라는 라고 표현하면 0과의 비교를 암시하지 않기 때문에 에러가 발생합니다.

You can use `if` and `let` together to work with values that might be missing.
여러분들은 `if` 그리고 `let`
<!-- These values are represented as optionals. -->
이러한 값들은 옵션널(optionals)이라고 표현됩니다.
<!-- An optional value either contains a value or contains `nil` to indicate that a value is missing. -->
옵션널한 값은 어떤 값을 가지거나, 또는 값이 빠졌다고 지시하기 위하여 `nil`을 가지거나 둘 중 하나 입니다.
<!-- Write a question mark (?) after the type of a value to mark the value as optional. -->
그 값이 옵션널하다고 표시하기 위해 어떤 값의 타입 뒤에 물음표(`?`)를 씁니다.

``` swift
var optionalString: String? = "Hello"
print(optionalString == nil)
 
var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
```

> 실험(EXPERIMENT):
<!-- Change `optionalName` to `nil`. What greeting do you get? Add an `else` clause that sets a different greeting if `optionalName` is `nil`. -->
> `optionalName`의 값을 `nil`로 바꾸자. 여러분은 어떤 인사말(greeting)을 얻을 수 있습니까? 만약 `optionalName`이 `nil`이라면 다른 인사말을 설정하는 `else` 절을 추가해보자.

<!-- If the `optional` value is `nil`, the conditional is `false` and the code in braces is skipped. -->
만약 옵션널(optional) 값이 `nil`이라면, 그 조건문은 `false`(즉 거짓)이 되고 중괄호 안에 있는 코드를 건너뛰게 됩니다. 
<!-- Otherwise, the optional value is unwrapped and assigned to the constant after `let`, which makes the unwrapped value available inside the block of code. -->
다른 방법으로, 옵션널(optional) 값이 풀어져 `let` 뒤에 상수로 할당되면, 풀어진 값은 코드의 블록 안에서 유용하게 된다.

Another way to handle optional values is to provide a default value using the `??` operator.
옵션널(optional) 값을 다루는 다른 방법은 `??`라는 연산자를 사용하여 디폴트(default) 값을 제공하는 것이다.
If the optional value is missing, the default value is used instead.
옵션널(optional) 값이 빠졌다면, 이 디폴트(default) 값을 대신 사용할 것이다.

``` swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```

Switches support any kind of data and a wide variety of comparison operations—they aren’t limited to integers and tests for equality.
switch문에는 정수 타입 값이나 동등 비교연산 뿐만 아니라 어떤 종류의 데이터든 사용할 수 있고 다양한 비교 연산자들을 사용할 수 있습니다.
test
