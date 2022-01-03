# 외부 반복과 아규먼트 매칭
## 레인지 클래스
- 특정 범위 값들을 반복하기 위해 만든 특화 클래스
- 숫자, 문자, 문자열 등을 지원함
```kotlin
val numberRange: IntRange = 1..5
var charRange: CharRange = 'a'..'e'
var stringRange: ClosedRange<String> = "aa".."az"

println(numberRange.contains(5)) // true
println(numberRange.contains(10)) // false

println(charRange.contains('c')) // true
println(charRange.contains('f')) // false 

println(stringRange.contains("ab")) // true
println(stringRange.contains("zz")) // false
```
## 정방향 & 역방향 반복
```kotlin
for (i in 1..5) { //
    print(i) // 결과 : 12345
}

for (i in 1 until 5) {
    print(i) // 결과 : 1234
}

for (i in 1..10 step 2) { //
    print(i) // 결과 : 13579
}

for (ch in 'a'..'c') {
    print(ch) // 결과 : abc
}

for (dt in 5 downTo 1) { // 혹은 for (dt in 5.downTo(1)) {
    print(dt) // 54321
}

for (ch2 in 'c' downTo 'a') { // 혹은 for (ch2 in 'c'.downTo('a')) { 
    print(ch2) // 결과 : cba
}
```
## 배열과 리스트 반복
```kotlin
val array = arrayOf(1, 2, 3)
var sumOfArray = 0
for (item in array) {
   sumOfArray += item
}
println(sumOfArray) // 결과 6
```
```kotlin
val charList = listOf('a', 'b', 'c')
for (char in charList) {
    println("$char is Ascii = ${char.code}")
}
// 결과
//a is Ascii = 97
//b is Ascii = 98
//c is Ascii = 99
```

## When
- 코틀린에서 switch문 대신 사용 하는 문법

### 표현식으로 When
```kotlin
fun getHttpResponseCodeCategory(code: Int) = when {
    code in 100..199 -> "informational response"
    code in 200..299 -> "successful"
    code in 300..399 -> "redirection"
    code in 400..499 -> "client error"
    code in 500.. 599 -> "server error"
    else -> "unknown"
}

println("404 code is " + getHttpResponseCodeCategory(404)) // 404 code is client error
println("999 code is " + getHttpResponseCodeCategory(999)) // 999 code is unknown
```

```kotlin
fun testWhen(arg: Any?) = when (arg) {
    "hi", "hello" -> "Hello World"
    in listOf("foo", "baz") -> "foo baz"
    in 1..100 -> "1<=$arg<=100"
    is String -> "Is String"
    null -> "this is null"
    else -> "else"
}


println(testWhen("hi")) // Hello World
println(testWhen("foo")) // foo baz
println(testWhen(50)) // 1<=50<=100
println(testWhen("this_is_string")) // Is String
println(testWhen(null)) // this is null
println(testWhen("안녕하세요")) // else
```
- 표현식으로 사용되는 경우 `else`가 반드시 존재해야함
