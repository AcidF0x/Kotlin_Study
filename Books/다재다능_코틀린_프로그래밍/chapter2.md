# Java 개발자를 위한 코틀린 필수 사항

## Less Typing
### 세미콜론 생략 가능
### 변수 타입 생략 가능
```kotlin
var string = "this is string"
println(string)
println(string::class)
println(string::javaClass)
```
```
this is string
class kotlin.String
val T.javaClass: java.lang.Class<T>
```
- 타입이 명확한 경우 타입을 생략 가능
- 함수나 메서드의 경우 리턴타입 생략 가능 파라메터 타입은 명시 해야함

### 클래스나 함수 생략 가능
```kotlin
//kotlin-test.kts
fun test() {
    println("this is test function")
    throw Exception("exception")
}

try {
    test()
} catch (exception: Exception) {
    exception.printStackTrace()
}
```
```
$ kotlinc-jvm -script kotlin-test.kts
this is test function
java.lang.Exception: exception
        at Kotlin_test.test(kotlin-test.kts:3)
        at Kotlin_test.<init>(kotlin-test.kts:7)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
        at kotlin.script.experimental.jvm.BasicJvmScriptEvaluator.evalWithConfigAndOtherScriptsResults(BasicJvmScriptEvaluator.kt:96)
        at kotlin.script.experimental.jvm.BasicJvmScriptEvaluator.invoke$suspendImpl(BasicJvmScriptEvaluator.kt:41)
        at kotlin.script.experimental.jvm.BasicJvmScriptEvaluator.invoke(BasicJvmScriptEvaluator.kt)
////////////// 후략 /////////////////////////
```
- 클래스를 사용하지 않은 스크립트 파일이지만 파일명을 베이스한 클래스의 메소드로 자동으로 생성

### try - catch를 강제 하지 않음
- Exception이 예상되는 함수/메서드를 호출시 Try-Catch를 문이 없어도 컴파일이 영향을 주지 않음

### var vs val
```kotlin
val num = 100 // immutable
num = 40 // 컴파일 오류

var score = 10 // mutable
score = 50 
```

### 향상된 동일성 체크
1. Java equlas() / Kotlin == 연산자 - 값비교
- 자바와 다르게 코틀린은 null값도 안전하게 처리 할수 있다
2. Java == 연산자 / Kotin === 연산자 - 참조대상 비교


### 문자열 템플릿
```Kotlin
val thisYear = 2021
val birthYear = 2020
var name = "Jone Doe"

var output = "Name -> $name"
var output2 = "Age -> ${thisYear - birthYear}"

println(output) // Name -> Jone Doe
println(output2) // Age -> 1
```

### Raw 문자열
```kotlin
var test1 = """
이제 "를 이스케이프 없이
사용가능합니다
"""

var test2 = """indent가
    있는경우는 조금 이상 합니다"""
    
var test3 = """indent가
    |있다면 줄 바꿈 기호와 trimMargin()을 사용하세요"""

println(test1)
println(test2)
println(test3.trimMargin())
    
```
```
//결과
이제 "를 이스케이프 없이
사용가능합니다

indent가
    있는경우는 조금 이상 합니다
    
indent가
있다면 줄 바꿈 기호와 trimMargin()을 사용하세요
```
