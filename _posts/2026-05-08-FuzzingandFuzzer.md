---
title: "fuzzing과fuzzer"
layout: single
date: 2026-05-08
categories: [BugBounty]
---

#### 1. 퍼징이란?

퍼징(Fuzzing)은 프로그램에 비정상적이거나 예상하지 못한 입력값을 반복적으로 전달하여 오류나 취약점을 찾는 동적 테스트 기법입니다.
주로 소프트웨어의 크래시(Crash), 메모리 오류, 예외 처리 미흡, 보안 취약점 등을 발견하기 위해 사용됩니다.

예를 들어 로그인 프로그램에 매우 긴 문자열이나 특수문자, 잘못된 파일 형식 등을 입력하여 프로그램이 비정상 종료되는지 확인하는 방식입니다.
이를 자동화한 도구를 퍼저(Fuzzer) 라고 합니다.

퍼징은 다음과 같은 특징을 가집니다.

- 자동으로 대량의 입력값 생성 가능
- 사람이 찾기 어려운 취약점 탐지 가능
- 실제 실행 환경에서 동작 확인 가능
- 보안 취약점 분석에 널리 사용됨

최근에는 운영체제, 웹 브라우저, IoT 기기, 네트워크 장비 등 다양한 분야에서 활용되고 있으며, 취약점 분석과 보안 연구의 핵심 기술 중 하나로 자리 잡고 있습니다.

---

#### 2. 퍼징의 분류

##### 1) Black-box Fuzzing

프로그램 내부 구조를 모른 채 입력과 출력만을 기반으로 테스트하는 방식입니다.

특징:
- 구현이 간단함
- 실행 속도가 빠름
- 코드 분석 없이 테스트 가능
- 코드 내부 경로 탐색 한계 존재

예시:
- 랜덤 문자열 입력
- 파일 포맷 변조

##### 2) White-box Fuzzing

프로그램 내부 코드와 실행 경로를 분석하면서 테스트하는 방식입니다.

특징:
- 높은 코드 커버리지 확보 가능
- 복잡한 취약점 탐지 가능
- 분석 비용과 실행 시간이 큼

대표 기술: Symbolic Execution(심볼릭 실행)

##### 3) Gray-box Fuzzing

Black-box와 White-box의 중간 형태입니다.
프로그램의 일부 실행 정보를 활용하여 효율적으로 입력을 생성합니다.

특징:
- 코드 커버리지를 참고하여 입력 생성
- 성능과 효율의 균형이 좋음
- 현재 가장 많이 사용되는 방식

대표 예시: AFL(American Fuzzy Lop)

##### 4) Mutation-based Fuzzing

기존 정상 입력값을 변형하여 새로운 테스트 케이스를 생성합니다.

예시:
- 문자열 길이 증가
- 특정 바이트 변조
- 파일 헤더 변경

장점:
- 실제 동작 가능한 입력 생성 가능
- 빠른 테스트 가능

##### 5) Generation-based Fuzzing

프로토콜이나 파일 포맷 구조를 이해하고 규칙 기반으로 입력을 생성하는 방식입니다.

특징:
- 복잡한 프로그램 테스트에 유리
- 높은 정확도
- 포맷 정보 필요

예시:
- PDF 퍼징
- 네트워크 프로토콜 퍼징

| 구분         | Black-box Fuzzing | Gray-box Fuzzing        | White-box Fuzzing  |
| ---------- | ----------------- | ----------------------- | ------------------ |
| 동작 방식      | 입력과 출력만 확인        | 일부 실행 정보 활용             | 내부 코드와 경로 분석       |
| 코드 접근 여부   | 불가능               | 제한적 가능                  | 완전 가능              |
| 입력 생성 방식   | 무작위 입력 중심         | 코드 커버리지 기반 변형           | 경로 분석 기반 생성        |
| 분석 난이도     | 낮음                | 중간                      | 높음                 |
| 실행 속도      | 빠름                | 비교적 빠름                  | 느림                 |
| 코드 커버리지    | 낮음                | 높음                      | 매우 높음              |
| 복잡한 취약점 탐지 | 어려움               | 가능                      | 매우 강력              |
| 대표 기술      | Random Fuzzing    | Coverage-guided Fuzzing | Symbolic Execution |
| 대표 퍼저      | Radamsa           | AFL, AFL++              | KLEE               |
| 장점         | 간단하고 빠름           | 효율성과 성능 균형              | 깊은 경로 탐색 가능        |
| 단점         | 탐지 한계 존재          | 일부 조건 우회 한계             | 높은 자원 소모           |
| 주 사용 분야    | 간단한 프로그램 테스트      | 일반 소프트웨어 취약점 분석         | 연구 및 고급 보안 분석      |

---

#### 3. 계측(Instrumentation)

계측은 프로그램 실행 중 내부 동작 정보를 수집하기 위해 코드를 삽입하거나 수정하는 기술입니다.
특히 Gray-box Fuzzing의 핵심 기술로 사용됩니다.

퍼저는 계측을 통해 어떤 코드가 실행되었는지, 어떤 조건문을 통과했는지, 어느 함수가 호출되었는지, 어디서 크래시가 발생했는지 등의 정보를 확인합니다.

ex)다음 코드가 있습니다.
```cpp
if(input[0] == 'A'){
    if(input[1] == 'B'){
        crash();
    }
}
```

랜덤 퍼징만 사용하면 "AB"를 찾기 어렵지만 계측을 사용하면: <br>
"A" → 첫 번째 조건 통과<br>
"AB" → 두 번째 조건 통과
라는 실행 정보를 확인할 수 있습니다.

퍼저는 이를 바탕으로 “A로 시작하는 입력이 더 깊은 코드에 도달한다”고 판단하여 해당 입력을 집중적으로 변형합니다.

즉, 계측은 단순 랜덤 테스트를 효율적인 지능형 퍼징으로 발전시키는 핵심 기술입니다.

계측의 종류:
- Compile-time Instrumentation: 컴파일 과정에서 코드 삽입
- Binary Instrumentation:	바이너리에 직접 계측 삽입
- Static Instrumentation:	실행 전 바이너리 수정
- Dynamic Instrumentation:	실행 중 실시간 계측

대표 계측 기술:
- Coverage Tracking
:어떤 코드가 실행되었는지 추적합니다.

- Edge Coverage
:분기 간 이동 경로를 추적합니다.

- Sanitizer
:메모리 오류를 탐지합니다. <br>
대표적으로 ASan(메모리 오류 탐지), UBSan(정의되지 않은 동작 탐지), MSan(초기화되지 않은 메모리 사용 탐지)이 있습니다.

탐지 가능한 오류:
- Buffer Overflow
- Use After Free
- Integer Overflow

---

#### 4. 커버러지(Coverage)
1. Coverage Tracking

Coverage Tracking은 프로그램 실행 중 어떤 코드가 실행되었는지 추적하는 기술입니다.<br>
퍼저는 입력값을 실행한 뒤<br>
새로운 코드가 실행되었는지<br>
이전에 도달하지 못한 영역에 접근했는지<br>
를 확인합니다.

새로운 코드 영역이 발견되면
해당 입력을 저장(seed) 후
추가 변형(Mutation) 수행을 진행합니다.

즉, 더 많은 코드를 실행하는 입력”을 우선적으로 발전시키는 방식을 말합니다.

- Coverage Tracking의 동작 예시<br>
ex)
if(input[0] == 'A'){
    printf("A");
}
위와 같은 코드에서
퍼저가 "B"를 입력하면 조건문 미통과<br>

퍼저가 "A"를 입력하면 새로운 코드 영역 실행<br>

퍼저는 "A" 입력이 더 깊은 코드에 도달했다고 판단하고 "A" 기반 입력을 집중적으로 변형합니다.

ex)
- "AB"
- "A123"
- "AAAA"
  
Coverage Tracking의 목적:
| 목적        | 설명             |
| --------- | -------------- |
| 새로운 코드 탐색 | 실행되지 않은 코드 발견  |
| 입력 최적화    | 의미 있는 입력 우선 변형 |
| 취약점 탐지 향상 | 깊은 코드 영역 접근    |
| 효율 향상     | 무의미한 입력 감소     |

2. Edge Coverage

Edge Coverage는 코드 블록 간 이동 경로(Edge)를 추적하는 방식입니다.
Coverage Tracking보다 더 정밀한 방식이며, 현대 Gray-box Fuzzer에서 가장 널리 사용됩니다.

대표적으로 AFL, AFL++가 있습니다.

- Edge란?
Edge는 하나의 Basic Block에서 다른 Block으로 이동하는 연결을 의미합니다.

ex)
```cpp
if(x > 10){
    foo();
}else{
    bar();
}
```
실행 흐름:
Block1 → Block2
Block1 → Block3

여기서<br>
1 → 2<br>
1 → 3<br>
이 각각 Edge입니다.

- 왜 Edge Coverage가 중요한가?

Basic Block Coverage는 어떤 코드가 실행되었는가만 확인하지만 Edge Coverage는 어떤 경로로 실행되었는가 까지 추적합니다.
그 덕에 실행 흐름 자체를 분석할 수 있고,
조건문 분기를 더 정확히 탐색할 수 있습니다.

Edge Coverage 동작 예시
```cpp
if(a == 'A'){
    if(b == 'B'){
        crash();
    }
}
```
입력 "A":<br>
Block1 → Block2

입력 "AB":<br>
Block1 → Block2 → Block3

퍼저는 새로운 Edge가 발견되었다고 판단하고 "AB" 계열 입력을 계속 변형합니다.
이 과정을 반복하면서 더 깊은 코드 영역을 탐색하게 됩니다.

Coverage Tracking과 Edge Coverage의 차이:

  | 구분       | Coverage Tracking | Edge Coverage |
  | -------- | ----------------- | ------------- |
  | 추적 대상    | 실행된 코드            | 코드 간 이동 경로    |
  | 정밀도      | 상대적으로 낮음          | 높음            |
  | 실행 흐름 분석 | 제한적               | 가능            |
  | 분기 추적    | 단순                | 정밀            |
  | 대표 사용    | 기본 Coverage 분석    | AFL/AFL++     |
  | 목적       | 새로운 코드 발견         | 새로운 경로 발견     |


---

#### 5. 세니타이저(Sanitizer)의 종류
##### 1. ASan (AddressSanitizer)
메모리 오류를 탐지하는 Sanitizer입니다.

주요 탐지 대상:
- Buffer Overflow
- Heap Overflow
- Stack Overflow
- Use After Free
- Double Free
- Out-of-bounds Access

ex)
```cpp
#include <stdio.h>

int main() {
    int arr[3];
    arr[5] = 10;
    return 0;
}
```
위 코드는 배열 범위를 초과해서 접근합니다.

ASan으로 실행하면 <br>
어느 줄에서 오류가 발생했는지<br>
어떤 메모리를 잘못 접근했는지<br>
Stack/Heap 정보<br>
등을 상세하게 출력합니다.

특징:

| 항목       | 설명               |
| -------- | ---------------- |
| 목적       | 메모리 오류 탐지        |
| 속도       | 비교적 빠름           |
| 퍼징 사용 빈도 | 매우 높음            |
| 대표 활용    | AFL++, LibFuzzer |

##### 2. UBSan (UndefinedBehaviorSanitizer)

정의되지 않은 동작을 탐지하는 Sanitizer입니다.

C/C++에는 결과가 정의되지 않은 동작들이 존재합니다.

이런 동작은<br>
프로그램 오동작<br>
보안 취약점<br>
예기치 않은 결과<br>
를 발생시킬 수 있습니다.

주요 탐지 대상
- Integer Overflow
- Null Pointer Dereference
- Misaligned Pointer
- Invalid Shift
- Divide By Zero

ex)
```cpp
int x = 2147483647;
x = x + 1;
```
위 코드에서 정수 오버플로우가 발생합니다.
UBSan은 이런 위험한 동작을 탐지합니다.

특징:
| 항목    | 설명               |
| ----- | ---------------- |
| 목적    | 정의되지 않은 동작 탐지    |
| 탐지 범위 | 논리 오류 포함         |
| 속도    | ASan보다 가벼운 경우 많음 |
| 활용    | 안정성 검사           |


##### 3. MSan (MemorySanitizer)
초기화되지 않은 메모리 사용을 탐지하는 Sanitizer이다.

즉, 값이 없는 메모리를 읽는 문제를 탐지합니다.

ex)
```cpp
#include <stdio.h>

int main() {
    int x;
    printf("%d\n", x);
}
```
코드에서 보면 x는 초기화되지 않았다.
MSan은 이런 문제를 탐지합니다.

특징:
| 항목     | 설명              |
| ------ | --------------- |
| 목적     | 초기화되지 않은 메모리 탐지 |
| 탐지 정확도 | 매우 높음           |
| 단점     | 속도가 느림          |
| 사용 환경  | 디버깅/보안 분석       |

- Sanitizer 비교:
| 종류    | 탐지 대상        | 대표 오류              |
| ----- | ------------ | ------------------ |
| ASan  | 메모리 접근 오류    | Buffer Overflow    |
| UBSan | 정의되지 않은 동작   | Integer Overflow   |
| MSan  | 초기화되지 않은 메모리 | Uninitialized Read |

퍼저와 Sanitizer와 함께 사용하면
메모리 손상,
위험한 연산,
숨겨진 버그
까지 발견할 수 있어 크래시가 발생하지 않아도 취약점을 탐지할 수 있습니다.
<br>
그래서 현대 퍼징에서는 AFL++, LibFuzzer, honggfuzz 등이 Sanitizer와 함께 자주 사용됩니다.

---

#### 6. 주요 퍼저(Fuzzer)
##### 1) AFL (American Fuzzy Lop)

가장 유명한 Gray-box 기반 퍼저 중 하나입니다.

특징:
- 코드 커버리지를 기반으로 입력 생성
- 빠른 속도
- 사용이 비교적 간단
- 오픈소스 프로젝트에서 많이 사용됨

장점:
- 성능 우수 
- 다양한 취약점 발견 가능

단점: 복잡한 조건 우회 어려움

2) AFL++

기존 AFL을 개선한 확장 버전입다.

특징:
- 더 높은 성능
- 다양한 instrumentation 지원
- 현대 환경에 맞춘 기능 추가

최근에는 AFL보다 AFL++ 사용이 증가하는 추세입니다.

3) LibFuzzer

LLVM/Clang 기반의 인메모리 퍼저입니다.

특징:
- 함수 단위 퍼징 가능
- Sanitizer와 함께 사용 가능
- 빠른 실행 속도

장점:
- 메모리 오류 탐지에 강력함
- CI 환경과 연동 용이

단점: 대상 코드 수정이 필요한 경우 존재

4) honggfuzz

Google에서 개발한 퍼저입니다.

특징:
- 다양한 CPU 아키텍처 지원
- Sanitizer 연동 가능
- 성능 최적화 우수

특히 Linux 환경에서 많이 활용된다.

5) Peach Fuzzer

Generation-based 방식에 강점을 가진 퍼저이다.

특징:
- 프로토콜 및 파일 포맷 기반 퍼징 가능
- 구조화된 입력 생성 지원

장점: 복잡한 데이터 구조 테스트 가능

단점: 초기 설정이 복잡함

6) Syzkaller

리눅스 커널 퍼징에 특화된 퍼저입니다.

특징:
- 시스템 콜 기반 퍼징
- 커널 취약점 탐지에 강력함

Google의 커널 보안 연구에서도 활용됩니다.

| 퍼저           | 방식                 | 특징                    | 장점             | 단점            |
| ------------ | ------------------ | --------------------- | -------------- | ------------- |
| AFL          | Gray-box           | 코드 커버리지 기반 입력 생성      | 빠르고 유명함        | 복잡한 조건 우회 어려움 |
| AFL++        | Gray-box           | AFL 개선 버전             | 성능 및 기능 강화     | 설정이 다소 복잡     |
| LibFuzzer    | In-process Fuzzing | 함수 단위 퍼징              | 매우 빠름          | 코드 수정 필요 가능   |
| honggfuzz    | Gray-box           | Sanitizer 연동 지원       | 다양한 환경 지원      | 설정 이해 필요      |
| Peach Fuzzer | Generation-based   | 규칙 기반 입력 생성           | 구조화 데이터 테스트 강력 | 초기 설정 복잡      |
| Syzkaller    | Kernel Fuzzing     | 시스템 콜 기반              | 커널 취약점 탐지 강력   | 리눅스 커널 중심     |
| Radamsa      | Mutation-based     | 단순 변형 중심              | 사용이 매우 쉬움      | 정밀한 분석 한계     |
| KLEE         | White-box          | Symbolic Execution 사용 | 높은 코드 탐색률      | 속도가 느리고 복잡함   |

---

#### 7. 핵심 정리

퍼징은 비정상적인 입력을 자동으로 생성하여 프로그램의 오류와 취약점을 찾는 중요한 보안 테스트 기법입니다.
특히 메모리 손상, 크래시, 예외 처리 문제 등 사람이 직접 찾기 어려운 취약점을 발견하는 데 매우 효과적입니다.

퍼징은 크게 Black-box, White-box, Gray-box 방식으로 나뉘며, 최근에는 효율성과 성능의 균형이 좋은 Gray-box Fuzzing이 가장 널리 사용됩니다.

대표적인 퍼저로는 AFL, AFL++, LibFuzzer, honggfuzz, Peach Fuzzer, Syzkaller 등이 있으며 각각 목적과 사용 환경이 다릅니다.

AFL/AFL++ : 범용 퍼징
LibFuzzer : 함수 단위 테스트
Syzkaller : 커널 퍼징
Peach : 구조 기반 퍼징
