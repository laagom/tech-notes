# [Java] Math 주요 메서드 정리

> 작성일: 2025-06-07 · 태그: Language/Java/Method, 기초

프로그래머스 코테를 오랜만에 풀어보는데 개발한지 몇 년이 지났는데도 Math함수가 헷갈려 정리를 좀 해 놓으려고 한다.

자바에서 계산을 위한 Math 클래스를 제공한다. Math 클래스는 **java.lang 패키지에 위치하고 있으므로 별도의 import없이 사용이 가능하다.**

아래는 Math 클래스의 메서드를 표로 정리한 것이다.

### 메서드 정리 표
---

|     구분      | 메서드                                                                            |
| :---------: | ------------------------------------------------------------------------------ |
|  절대값 / 부호   | `abs`, `signum`                                                                |
|   최대, 최소값   | `max`, `min`                                                                   |
| 소수점 올림 / 버림 | `ceil`, `floor`, `round`, `rint`                                               |
|  제곱 / 제곱근   | `pow`, `scalb`, `sqrt`, `cbrt`, `hypot`                                        |
|  삼각 함수 관련   | toRadians, toDegrees, sin, cos, tan, asin, acos, atan, atan2, sinh, cosh, tanh |
|    로그 관련    | exp, getExponent, expm1, log, log1p, log10                                     |
|    난수 관련    | ~~random~~ /   _**java.util.Random 클래스 사용 권장**_                                |
|    소수 관련    | ulp, nextAfter, nextUp, copySign                                               |

### 절대값 / 부호
---
```java
public class MathMethod {  
    public static void main(String[] args) {  
        // 절대값 / 부호  
        System.out.println(-35);                          // -35  
        System.out.println(Math.abs(-35));         // 35  
        System.out.println(Math.abs(35));          // 35  
        System.out.println(Math.signum(7));      // 1.0  
        System.out.println(Math.signum(-12));   // -1.0  
    }  
}
```
- abs() : 절대값 계산
- signum() : 부호 확인

#### Math.abs()
매개변수의 <ins>절대값을</ins> 반환한다. 두 점 사이의 거리를 구하는 등의 많은 문제에서 유용하게 사용된다.
```text
ex) -35 -> 35
```

#### Math.signum()
매개변수가 양수일 경우 1.0을, 음수일 경우 -1.0을 반환한다.
```text
ex) -12 -> -1.0
```

### 최대, 최소 값
---
```java
package MathExamPakage;  
  
public class MaxMin {  
    public static void main(String[] args) {  
        // 최대, 최소 값  
        System.out.println(Math.max(35.2, 12.1));  // 35.2
        System.out.println(Math.min(35.2, 12.1));  // 12.1
    }  
}
```
- max() : 두 매개변수 중 큰 값을 리턴
- min() : 두 매개변수 중 작은 값을 리턴

#### Math.max()
두 매개변수 중 큰 값을 리턴한다. 
* 배열 중에서 가장 큰 값을 리턴하기 위해선 반복문을 이용하여 별도의 함수를 만들어야 큰 값을 얻을 수 있다.

#### Math.min()
두 매개변수 중 작은 값을 리턴한다.
- 배열 중에서 가장 작은 값을 리턴하기 위해선 반복문을 이용하여 별도의 함수를 만들어야 작은 값을 얻을 수 있다.

### 소수점 올림 / 버림
---
```java
package MathExamPakage;  
  
public class RoundCeil {  
    public static void main(String[] args) {  
        // 소수점 올림 / 버림  
        // round() - 소수점 반올림 (정수형 리턴)  
        System.out.println("# round() - 소수점 반올림 (정수형 리턴)");    // 2  
        System.out.println("Math.round(2.4) : " + Math.round(2.4));    // 2  
        System.out.println("Math.round(2.5) : " + Math.round(2.5));    // 3  
        System.out.print("\n");  
  
        // rint() - 소스점 반올림 (dounble형 리턴)  
        System.out.println("# rint() - 소스점 반올림 (dounble형 리턴)");  
        System.out.println("Math.rint(2.4) : " + Math.rint(2.4));     // 2.0  
        System.out.println("Math.rint(-1.7) : " + Math.rint(-1.7));    // -2.0  
        // ## 참고 ## : 소수점은 반올림은 (-) 부호는 생략하고 반올림 한뒤 (-) 다시 붙이는걸로 생각하자.  
        System.out.print("\n");  
  
        // ceil() - 올림  
        System.out.println("# ceil() - 올림");  
        System.out.println("Math.ceil(-1.3) : " + Math.ceil(-1.3));    // -1.0  
        System.out.println("Math.ceil(4.2) : " + Math.ceil(4.2));     // 5.0  
        // ## 참고 ## : 수적인 부분에서 정말로 올림  
        System.out.print("\n");  
  
        // floor() - 버림  
        System.out.println("# floor() - 버림");  
        System.out.println("Math.floor(3.9) : " + Math.floor(3.9));    // 3.0  
        System.out.println("Math.floor(-3.6) : " + Math.floor(-3.6));   // -4.0  
        // ## 참고 ## : 수적인 부분에서 정말로 버림  
        System.out.print("\n");  
    }  
}
```
- round() : 소수점 반올림 (정수형 리턴)
- rint() : 소수점 반올림 (double형 리턴)
- ceil() : 올림
- floor() : 버림

#### Math.round()
소수점 반올림하며, <span style="color:orange;">유일하게 정수를 반환</span>한다.
```text
ex) 2.4 -> 2
```

#### Math.rint()
소수점 반올림하며, double형을 반환한다.
```text
ex) 2.4 -> 2.0
```

#### Math.ceil()
소수점 올림 처리하며, 음수일 경우 소수점 밑으로 버리고, 소수점 밑 1 이상의 양수일 경우 소수점을 버리고 +1 한다.
```text
ex) 4.2 -> 5.0, -1.3 -> -1.0
```

#### Math.floor()
소수점 내림 처리하며, 소수점 밑 1 이상의 음수일 경우 소수점을 버리고 -1 한다고 보면 된다. 양수일 경우 소수점 밑으로 버림.
```text
ex) 3.9 -> 3.0, -3.6 -> -4.0
```

### 제곱 / 제곱근
---
```java
package MathExamPakage;  
  
public class Sqrt {  
    public static void main(String[] args) {  
        // 제곱 / 제곱근  
  
        // sqrt() - 매개변수 제곱근  
        System.out.println("매개변수 제곱근");  
        System.out.println("Math.sqrt(9) : " + Math.sqrt(9));  
        System.out.println("Math.sqrt(15) : " + Math.sqrt(15));  
        System.out.print("\n");  
  
        // cbrt() - 매개변수 세제곱근  
        System.out.println("매개변수 세제곱근");  
        System.out.println("Math.cbrt(8) : " + Math.cbrt(8));  
        System.out.println("Math.cbrt(64) : " + Math.cbrt(64));  
        System.out.print("\n");  
  
        // pow() - 첫번째 매개변수를 두번째 매개변수 수만큼 곱셈  
        System.out.println("첫번째 매개변수를 두번째 매개변수 수만큼 곱셈");  
        System.out.println("Math.pow(2, 6) : " + Math.pow(2, 6));  
        System.out.println("Math.pow(3, 3) : " + Math.pow(3, 3));  
        System.out.print("\n");  
  
        // scalb() - 첫번째 매개변수 *2^두 번째 매개변수 값을 구함  
        System.out.println("첫번째 매개변수 *2^두 번째 매개변수 값을 구함");  
        System.out.println("Math.scalb(3, 4) : " + Math.scalb(3, 4));  
        System.out.println("Math.scalb(2, 3) : " + Math.scalb(2, 3));  
        System.out.print("\n");  
  
        // hypot() - (첫 번째 매개변수의 제곱 + 두 번째 매개변수의 제곱)의 제곱근을 구함.  
        System.out.println("(첫 번째 매개변수의 제곱 + 두 번째 매개변수의 제곱)의 제곱근을 구함.");  
        System.out.println("Math.hypot(3, 4) : " + Math.hypot(3, 4));  
        System.out.println("Math.hypot(2, 3) : " + Math.hypot(2, 3));  
        System.out.print("\n");  
    }  
}
```
- sqrt() : 매개 변수의 **제곱근**을 구함
- cbrt() : 매개 변수의 **세제곱근**을 구함
- pow() : 첫 번째 매개 변수의 두 번째 매개변수만큼의 **제곱 값**을 구함
- scalb() : 첫 번째 매개변수 * 2^두 번째 매개변수 값을 구함.
- hypot() : (첫 번째 매개변수의 제곱 + 두 번째 매개변수의 제곱)의 제곱근을 구함.

#### Math.sqrt()
매개변수의 제곱근을 구한다.
```text
ex) 9 = 3^2 => 3.0
```

#### Math.cbrt()
매개변수의 세제곱근을 구한다.
```
ex) 64 = 4^3 = 4.0
```

#### Math.pow()
첫 번째 매개 변수의 두 번째 매개변수만큼의 제곱 값을 구한다.
```text
ex) Math.pow(2, 6) => 2^6 = 2*2*2*2*2*2* = 64.0
```

#### Math.scalb()
첫 번째 매개변수 * 2 ^ 두 번째 매개변수 값을 구한다.
```text
Math.scalb(3, 4) => 3 * 2^4 = 3 * 16 = 48.0
```

#### Math.hypot()
(첫 번째 매개변수의 제곱 + 두 번째 매개변수의 제곱) 의 제곱근을 구한다.
```text
ex) Math.hypot(3, 4) => (3^2 + 4^2) -> 25의 제곱근 = 5
```

추가적으로 필요한 메서드들은 다음 api 문서를 참고하자.
[Math (Java SE 17 & JDK 17)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Math.html)
