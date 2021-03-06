---
layout: post
category: dart
title: "[Dart]변수와 타입"
---

# 변수선언

Dart의 변수는 3가지 방식으로 선언할 수 있다.

```dart
// 암시적인 방식
var a = 3;
var a = "haram";

// 명시적인 방식
int a = 3;
String a = "haram";

// 타입이 정해질 필요가 없다는 의미
dynamic a = 3;
dynamic a = "haram";
// Object 클래스를 이용할 수도 있다.
Object a = 3;
Object a = "haram";
```



# 타입

Dart의 built-in 타입은 다음과 같은 것들이 있다.

* **numbers**

int와 double이 있으며 num의 subtype이다.

```dart
int a = 1;
double a = 1.3;
num a = 1;
num a = 1.3;
```

[dart.math](https://api.dartlang.org/dev/dart-math) 라이브러리를 활용하면 더 다양한 기능과 값들을 찾을 수 있다.

```dart
var a = int.parse('1'); // int로 변환
var a = 1.toString(); // String으로 변환
var a = 3.14159.toStringAsFixed(2); // 소수점 이하 둘째자리까지 String으로 변환
```

위와 같은 메서드들도 유용하게 쓰일 수 있으며 int 형엔 shift/AND/OR 연산자도 쓰일 수 있다.

* **strings**

Dart의 string은 UTF-16 코드이며 작은/큰 따옴표 둘 다 사용할 수 있다. 또한 $와 {}를 통해서 변수를 넣을 수도 있다.

```dart
var s = "haram";
print("${s.toUpperCase()} $s");
// HARAM haram
```

String에서 많이 쓰이는 concatenation은 단순히 이어붙이거나 +, 혹은 $를 써서 할 수 있다.

```dart
var a = 'haram'" is good";
print(a);
var b = 'haram'+" is good";
print(b);
var s1 = 'haram';
var s2 = " is good";
print("$s1$s2");
// haram is good
```

* **booleans**

`bool` 키워드로 쓸 수 있는 건 다른 언어들과 비슷하지만 dart의 타입 안정성이라는 것이 있는데 if나 assert를 쓸 때 항상 true 값으로 써야 한다는 것이다.

```dart
var name = '';
assert(name.isEmpty());
```

* **lists (= arrays)**

자바스크립트의 array literals와 비슷하게 생겼으며 list 또한 타입 추론이 가능하다.

```dart
var list = [1, 2, 3];
// List<int>로 타입추론
```

또한 다음과 같이 const를 사용한다.

```dart
var constList = const [1, 2, 3];
```

* **maps**

Map 또한 타입추론이 된다.

```dart
var mapExample = {
    2: 'map1',
    3: 'map2',
    4: 'map3',
};
// Map<int, String>으로 추론
```

Map의 생성자로도 만들 수 있으며 new 키워드는 dart 2에서 옵션이 되었다.

```dart
var mapx = Map();
mapx[2] = 'map1';
mapx[3] = 'map2';
mapx[4] = 'map3';
```

새로운 key-value 쌍을 추가하거나 value 값을 얻는 방식은 자바스크립트와 동일하다.

```dart
mapx[5] = 'map4'; // 추가
print(mapx[2]); // 값 얻기
```

length 메서드로 key-value 쌍의 개수를 알 수도 있고 const 키워드를 사용할 수도 있다.

```dart
assert(mapx.length == 4);
final mapx = const{
    1: 'map1',
    2: 'map2',
    3: 'map3',
};
```

* **runes (string에서 Unicode 문자들을 나타내기 위함)**

Dart에서 runes는 string의 UTF-32 코드이다. 유니코드는 각 문자, 숫자 그리고 기호의 유일한 값을 정의한다. Dart는 UTF-16 코드 문자열이기 때문에 32-bit의 유니코드 값을 표현하기 위해선 새로운 문법이 필요하다. 이러한 문제를 해결하기 위한 방법이 UTF-32의 runes를 사용하는 것으로 `\uXXXX`처럼 표현한다. 예를 들어, `\u2665`는 ♥이고 `\u{1f600}`은 이모티콘 문자다. [DartPad](https://dartpad.dartlang.org/589bc5c95318696cefe5)를 통해 어떻게 나타나는지 확인해보는 것이 좋다.

이외에도 symbol이라는 것이 있는데 아직까지는 몰라도 될 것 같다.

## 출처

* [Dart 공식문서](https://www.dartlang.org/guides/language/language-tour)