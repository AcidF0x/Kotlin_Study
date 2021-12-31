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
