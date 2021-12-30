# 함수를 사용하자
## 함수 생성
```kotlin
fun sayHi() = "Hello" // 또는 fun sayHi() :String = "hello
print ln(sayHi())
```
- `fun` 키워드로 함수 정의
- 리턴타입을 지정하지 않았지만 타입추론으로 타입이 지정됨
```kotlin
fun sayHello() {
    return "hello"
}
// 컴파일 에러 !! : Kotlin: Type mismatch: inferred type is String but Unit was expected 
```
- 블록바디 `{ }` 가 없는 경우만 타입추론이 가능함 (단일 표현식)

## Unit 타입

```kotlin
fun sayHello() {
    println("hello")
}
val result = sayHello()
println(result::class)
println(result)
// 결과
// hello
// class kotlin.Unit
// kotlin.Unit
```
- 자바의 void와 대응되는 `Unit`이라는 타입을 지원함
- `Unit`타입 내부에 `toString()`, `equals()`, `hascode()`메소드를 가지고 있음 
- 모든 함수가 적어도 `Unit`을 리턴해주므로 모든 함수가 표현식으로 취급될 수 있다

```java
/// 자바코드
public class Main {

    public static void main(String[] args) {
	    var result = sayHello();
    }

    private static void sayHello()
    {
        System.out.println("Hello Buddy");
    }
}
// 결과
//java: cannot infer type for local variable result
//  (variable initializer is 'void')
```

### 파라미터 정의
```kotlin
fun getName(firstName: String, secondName: String) = firstName + secondName
println(getName("사쿠라", "미코"))
```
- `candiate : Type`형태로 정의
- 모든 파라미터는 `이뮤터블`함
```kotlin
fun addPrefix(prefix: String, words: String)
{
    words = prefix + words;
}
// 컴파일 에러 Kotlin: Val cannot be reassigned
```

### 기본 인자와 명시적 인자
```kotlin
fun addPrefix(words: String, prefix: String = "this is"): String {
    return prefix + words
}
```
- 위 형태로 기본 인자를 지정 할 수 있음
- 기본인자는 리터럴 뿐만 아니라 표현식도 사용 가능함
```kotlin
fun addPrefix(words: String, prefix: String = "${words.lowercase()}"): String {
    return prefix + words
}
println(addPrefix("WOW"))

/// 결과 : wowWOW
```
```kotlin
fun addPrefix(words: String, prefix: String = "this is"): String {
    return prefix + words
}

addPrefix("test", prefix = "wow")
addPrefix(prefix = "wow", words = "test")
addPrefix(prefix = "wow", "bbb") // 컴파일 에러
````
- 매개변수의 이름을 직접 지정하여 호출 할 수 있다. (명시적 인자)
- 단 위치가 다른 경우 모든 인자를 명시적 인자로 사용 

### 다중 인자
```kotlin
fun sum(vararg numbers: Int): Int
{
    var sum :Int = 0
    numbers.forEach { num -> sum += num }
    return sum
}

println(sum(1, 2, 3))
// 실행 결과 : 6
```
- vararg로 다중 인자를 한번에 처리 할 수 있다.

#### 스프레드 연산자
- 이미 넘겨야 할 인자가 `Array`인 경우 스프레드 연산자를 이용 할 수 있다
```kotlin
fun sum(vararg numbers: Int): Int
{
    var sum :Int = 0
    numbers.forEach { num -> sum += num }
    return sum
}

var numbers = intArrayOf(1, 2, 3)
println(sum(*numbers))
// 실행 결과 6
```
