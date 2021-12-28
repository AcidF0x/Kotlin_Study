# 코틀린 시작하기
- `InteliJ`로 유명한 `JetBrain`사에서 제작함 
- 안드로이드 공식 개발 언어

## 특징
1. 다양한 프로그래밍 패러다임을 지원함
2. Java, JavaScript, WebAssem, Native(LLVM)형태로 컴파일(트랜스컴파일) 가능
3. non-nullable 타입과 Nullable 타입을 구분
4. 클래스는 `final`이 기본
5. `;` 선택사항
6. `infix`어노테이션 제공 (.과 {}를 선택사항으로 만듬)

## 사용하기
InteliJ를 사용하거나 SDK를 직접 설치 할수 있음 
[Link](https://kotlinlang.org/docs/command-line.html)

### 바이트 코드로 컴파일하고 실행하기
- JDK 필요
```kotlin
// Hello.kt
fun main() = println("hello world")
```
```bash
$ kotlinc-jvm Hello.kt -d Hello.jar
$ java -classpath Hello.jar HelloKt // 1
hello world
$ java -jar Hello.jar // 2
hello world
```
#### -classpath
- Hello.kt파일 내의 main 함수 만으로 클래스가 완성되지 않음
- 따라서 코틀린 컴파일러가 자동으로 확장자를 제거한 이름과 Kt 접미사로 클래스 이름을 지정함 
- classpath옵션으로 클래스 명을 지정해준다
#### -jar
- 코틀린 컴파일러가 main 함수를 찾을때 jar파일내 Main-Class 매니페스트 어트리뷰트를 추가하여 -jar옵션을 사용해서 실행 가능

### REPL
- REPL (Read-Evaluate-Print Loop) (레플이라고 읽음)
```
$ kotlinc-jvm
Welcome to Kotlin version 1.6.0 (JRE 1.8.0_292-b10)
Type :help for help, :quit for quit
>>> 7 + 5
res0: kotlin.Int = 12
```

### 스크립트로 실행 하기
```kotlin
// Hello.kts
println("hello world")
```
```bash
$ kotlinc-jvm -script Hello.kts
hello world
```
참고로 확장자가 `.kts`가 아니면 아래와 같이 에러가 난다
```
$  kotlinc-jvm -script Hello.kt
error: unrecognized script type: Hello.kt; Specify path to the script file as the first argument
```
