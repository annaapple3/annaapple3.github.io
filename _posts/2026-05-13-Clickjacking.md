---
title: "브라우저 확장 프로그램 클릭재킹"
layout: single
date: 2026-05-13
categories: [paper-conference]
---

# 브라우저 확장 프로그램 클릭재킹 분석

[![[DEF CON 33 - 브라우저 확장 프로그램 클릭재킹: 단 한 번의 클릭으로 신용카드 정보가 유출됩니다 - 마렉 토트](data:image/jpeg;base64,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)](https://www.youtube.com/watch?v=Gu4IoDXNqoU)

## 주제 선정 이유

최근에 DEFCON을 나가기 위해 웹해킹을 공부하고 있었습니다. 그래서 DEFCON의 컨퍼런스 영상을 찾아보다 이 영상을 찾았습니다.
기존에는 클릭재킹(Clickjacking)을 비교적 오래된 웹 취약점으로 생각하고 있었지만, 이번 발표에서는 브라우저 확장 프로그램과 비밀번호 관리자 환경에서 완전히 새로운 형태로 발전한 공격 기법을 소개하고 있었습니다.

특히 사용자가 단순히 “쿠키 허용” 버튼을 누르는 행동만으로 신용카드 정보와 비밀번호가 유출될 수 있다는 점이 매우 충격적이었습니다. 별도의 악성 프로그램 설치 없이, 사용자가 평소와 같은 행동을 했을 뿐인데도 공격이 가능하다는 점에서 현실적인 위협이라고 느꼈습니다.

또한 저는 평소 웹 보안과 브라우저 기반 공격 기법에 관심이 있었기 때문에, DOM 조작과 브라우저 확장 프로그램 구조를 결합한 이번 연구가 매우 흥미롭게 다가왔습니다. 기존 웹 보안 개념이 브라우저 확장 프로그램 환경에서는 어떻게 달라질 수 있는지를 보여준 사례라고 생각해 이 주제를 더 깊게 정리해보고 싶었습니다.

---

## “단 한 번의 클릭으로 비밀번호와 카드 정보가 유출될 수 있다”

최근 브라우저 확장 프로그램(Extension)의 보안 위험성이 다시 주목받고 있습니다. 특히 비밀번호 관리자(Password Manager)는 사용자 편의성을 위해 자동 입력(AutoFill) 기능을 제공하지만, 이 기능이 오히려 새로운 공격 표면(Attack Surface)이 될 수 있다는 연구 결과가 공개되었습니다.

이번 발표에서는 브라우저 확장 프로그램의 UI를 악용하는 새로운 형태의 **DOM 기반 Extension Clickjacking** 기법이 소개되었습니다. 연구자는 단 한 번의 클릭만으로

* 비밀번호
* 2FA 코드(TOTP)
* 신용카드 정보
* 개인정보
* 패스키(Passkey)

까지 탈취할 수 있음을 시연했습니다.

특히 이 공격은

* 일반 웹사이트에서도 가능하고
* 별도 악성 프로그램 설치가 필요 없으며
* 사용자가 단순히 “쿠키 허용” 버튼만 눌러도 동작할 수 있다는 점

에서 매우 위험하게 평가됩니다.

---

# 클릭재킹(Clickjacking)이란 무엇인가

클릭재킹은 사용자가 실제로 무엇을 클릭하는지 모르게 만들어 공격자가 원하는 동작을 수행하게 하는 공격 기법입니다.

대표적인 방식은

* 투명한 iframe 위에 UI를 숨기고
* 사용자가 보이는 버튼을 클릭한다고 착각하게 만드는 것

입니다.

예를 들어 사용자는 “쿠키 허용" 버튼을 누른다고 생각하지만 실제로는

* 계정 공유
* 권한 허용
* 비밀번호 자동 입력

등이 실행될 수 있습니다.

기존 클릭재킹은

* X-Frame-Options
* CSP(Content Security Policy)
* SameSite Cookie

등으로 상당 부분 방어가 가능해졌습니다.

그래서 많은 기업들은 클릭재킹은 이제 큰 위협이 아니라고 생각해왔습니다.

하지만 이번 연구는 브라우저 확장 프로그램 환경에서는 이야기가 다르다”는 점을 보여주었습니다.

---

# 왜 브라우저 확장 프로그램이 위험한가

브라우저 확장 프로그램은 일반 웹사이트보다 훨씬 강력한 권한을 가집니다.

예를 들어 비밀번호 관리자는

* 웹페이지 DOM 접근
* 입력값 읽기/수정
* 자동 입력
* 인증 정보 저장

등을 수행합니다.

문제는 확장 프로그램 UI가 웹페이지 내부 DOM과 함께 동작한다는 점입니다.

즉 공격자는

* CSS
* JavaScript
* DOM 조작

을 이용해 확장 프로그램 UI를 숨기거나 위치를 바꿀 수 있습니다.

---

# 연구 핵심: DOM 기반 Extension Clickjacking

이번 발표의 핵심은 기존 iframe 기반 공격이 아니라 <br>
“DOM 기반 확장 프로그램 클릭재킹”입니다.

기존 방식은 iframe을 사용했지만, 새로운 방식은 브라우저 확장 프로그램이 웹페이지에 삽입한 UI 자체를 조작합니다.

즉 공격자는

1. 가짜 쿠키 배너 생성
2. 비밀번호 입력 폼 생성
3. 자동완성 메뉴 표시 유도
4. 확장 프로그램 UI 투명화
5. 사용자가 버튼 클릭
6. 실제로는 AutoFill 메뉴 클릭

이 이루어지도록 만듭니다.

사용자는 자신이 무엇을 클릭했는지 전혀 알지 못합니다.

---

# 공격 흐름 분석

## 1. 가짜 UI 생성

공격자는 먼저

* 쿠키 배너
* Cloudflare CAPTCHA
* 로그인 팝업
* 뉴스레터 창

등 사용자가 흔히 보는 UI를 생성합니다.

현대 웹사이트는

* “쿠키 허용”
* “닫기”
* “인증하기”

등 클릭을 계속 요구합니다.

연구자는 바로 이 사용자 습관을 악용했습니다.

---

## 2. AutoFill 메뉴 호출

이후 공격자는 숨겨진 입력창에 focus를 강제로 주어 비밀번호 관리자 AutoFill UI를 표시시킵니다.

ex)

* 신용카드 입력창
* 이름/주소 입력창
* 로그인 폼

등입니다.

사용자는 보지 못하지만 브라우저 확장 프로그램은 자동 입력 가능한 상황이라고 인식합니다.

---

## 3. UI 투명화(Opactiy 0)

이 단계가 핵심입니다.

공격자는 CSS를 이용해

```css
opacity: 0;
```

를 적용하여 AutoFill 메뉴를 완전히 투명하게 만듭니다.

즉 실제 AutoFill 메뉴는 존재하지만 사용자는 볼 수 없습니다.

---

## 4. 사용자의 클릭 유도

이후 사용자가 

* “쿠키 허용”
* “나는 인간입니다”
* “닫기”

버튼을 누르면 실제로는

* 비밀번호 자동 입력
* 카드 정보 입력
* 개인정보 입력

이 수행됩니다.

그리고 공격자는 입력된 값을 JavaScript로 읽어 서버로 전송합니다.

---

# 실제 시연: “쿠키 허용” 클릭만으로 카드 정보 탈취

연구자는 발표에서 실제 데모를 공개했습니다.

사용자는

1. CAPTCHA 클릭
2. 쿠키 허용 클릭
3. 확인 버튼 클릭

정도만 수행합니다.

하지만 실제로는 카드번호, 만료일, 보안코드(CVC)가 공격자에게 전송되었습니다.

심지어 사용자는

* 어떤 데이터가 입력되었는지
* AutoFill이 실행되었는지
* 카드 정보가 유출되었는지

전혀 알 수 없었습니다.

---

# iframe 기반 공격도 여전히 존재

발표에서는 기존 iframe 기반 공격도 소개되었습니다.

특히 일부 확장 프로그램은
```json
web_accessible_resources
```
설정 오류로 인해 내부 UI를 외부 사이트에서 로드할 수 있었습니다.

연구자는 NordPass에서<br>
* 확장 프로그램 UI를 iframe으로 불러오고
* opacity 0 처리 후
* “공유” 버튼 클릭을 유도하여
  
사용자의 전체 비밀번호 저장소를 공격자와 공유하는 공격까지 시연했습니다.

이 공격으로 연구자는 실제 버그 바운티 1만 달러를 받았다고 밝혔습니다.

---

# 가장 충격적인 부분: 대부분의 비밀번호 관리자가 취약

연구자는 총 11개의 주요 비밀번호 관리자를 테스트했습니다.

대상:<br>
* NordPass
* Proton Pass
* Bitwarden
* 1Password
* Dashlane
* RoboForm
* Keeper
* iCloud Passwords

등이 포함되었습니다.

결과는 매우 충격적이었습니다.

## 결과 요약

### 신용카드/개인정보 탈취

* 10개 중 8개 취약

### 로그인 정보 탈취

* 대부분 취약

### TOTP(2FA 코드) 탈취

* 대부분 취약

### Passkey 인증 흐름 하이재킹

* 일부 FIDO 인증 솔루션 취약

즉, 사용자가 한 번 클릭하면 비밀번호 + 2FA까지 동시에 탈취 가능한 상황이 존재했습니다.

---

# 왜 2FA도 무력화되는가

많은 사용자는 2FA를 쓰니까 안전하다고 생각합니다.

하지만 비밀번호 관리자에 아이디, 비밀번호, TOTP 코드를 모두 저장하는 경우가 많습니다.

즉 공격자가 AutoFill을 유도하면 비밀번호, OTP 코드가 동시에 입력됩니다.

결국 MFA가 사실상 단일 인증처럼 동작하게 되는 것입니다.

---

# 패스키(Passkey)도 안전하지 않을 수 있다

발표에서는 Passkey 공격 가능성도 소개되었습니다.

특정 구현에서는

* 인증 요청(Session)
* Challenge

가 강하게 바인딩되지 않아

* 서명된 Assertion 탈취
* 세션 하이재킹

가능성이 존재했습니다.

즉 사용자가 “Passkey 인증 승인”버튼을 눌렀다고 생각했지만 실제로는 공격자 세션 인증이 완료될 수 있다는 것입니다.

---

# 왜 이런 공격이 가능한가

핵심 원인은 다음과 같습니다.

## 1. 확장 프로그램 UI가 DOM 내부에서 동작

확장 프로그램은 웹페이지와 같은 DOM 공간을 공유합니다.

즉 웹페이지 스크립트가

* 위치 변경
* 투명화
* Overlay 생성

등을 수행할 수 있습니다.

---

## 2. AutoFill 기능의 과도한 편의성

많은 비밀번호 관리자는

* 모든 서브도메인 허용
* 자동완성 빠른 호출
* 사용자 클릭 최소화

를 목표로 설계되었습니다.

하지만 편의성이 증가할수록 공격 표면도 커집니다.

---

## 3. 사용자 클릭 피로(User Click Fatigue)

현대 웹은

* 쿠키 배너
* CAPTCHA
* 로그인 팝업
* 광고 닫기

등 클릭을 너무 많이 요구합니다.

결국 사용자는 생각 없이 클릭하게 됩니다.

공격자는 바로 이 심리를 악용합니다.

---

# 현실적인 공격 시나리오

발표에서는 매우 현실적인 공격 흐름도 제시되었습니다.

ex) <br>
1. 공격자가 XSS 취약점 발견
2. 정상 도메인에 악성 스크립트 삽입
3. 사용자가 링크 방문
4. 클릭 몇 번 수행
5. 계정/카드정보/TOTP 탈취

특히 대부분 비밀번호 관리자가 서브도메인 전체에서 AutoFill 허용하는 점이 매우 위험하다고 지적되었습니다.

즉,

```text
accounts.google.com
```

용 자격증명이

```text
vulnerable-sub.google.com
```

에서도 자동 입력될 수 있다는 의미입니다.

---

# 대응 방안

## 사용자 측 대응

### 1. 수동 AutoFill 비활성화

가장 안전한 방법은 불편하지만 직접 복사/붙여넣기, 수동 선택 방식이 안전합니다.

---

## 2. 정확한 URL만 허용

서브도메인 전체 허용 대신 정확한 URL만 AutoFill 설정하는 것이 좋습니다.

---

## 3. 브라우저 확장 프로그램 권한 최소화

Chromium 기반 브라우저에서는:

 “클릭 시에만 사이트 접근 허용”

설정이 가능합니다.

즉 사용자가 직접 확장 프로그램을 눌러야 AutoFill이 동작하게 만드는 방식입니다.

---

# 개발자 측 대응

## 1. Shadow DOM 보호 강화

* Closed Shadow Root 사용
* DOM 접근 제한

등이 필요합니다.

---

## 2. Opacity 조작 탐지

확장 프로그램은

* body opacity
* overlay 생성
* popover API

등 비정상 DOM 변경을 탐지해야 합니다.

---

## 3. AutoFill UI 격리

궁극적으로는 웹페이지 DOM과 완전히 분리된 UI가 필요하다는 의견도 제시되었습니다.

현재 구조에서는

* CSS 조작
* Overlay
* Pointer Events

등 다양한 우회가 가능하기 때문입니다.

---

# 이 연구가 중요한 이유

이번 연구는 단순 브라우저 취약점 발표가 아닙니다.

이 연구는

* 브라우저 확장 프로그램 보안 한계
* 사용자 인터페이스 신뢰 문제
* AutoFill 설계 위험성
* DOM 기반 공격 가능성

을 모두 보여준 사례입니다.

특히 중요한 점은 별도 악성코드가 필요 없다는 것입니다.

사용자는 단지 웹사이트 방문, 버튼 클릭만 했을 뿐인데

카드 정보, 비밀번호, OTP, 패스키 인증까지 탈취될 수 있습니다.

---

# 정리

많은 사람들은 비밀번호 관리자를 사용하면 안전하다고 생각합니다.

실제로 비밀번호 관리자는:

* 강력한 비밀번호 생성
* 재사용 방지
* MFA 지원

등 매우 중요한 보안 도구입니다.

하지만 이번 연구는 편의성 기능 자체가 공격 벡터가 될 수 있다는 사실을 보여주었습니다.

특히 AutoFill 기능은

* 사용자 경험 측면에서는 매우 편리하지만
* 보안 관점에서는 강력한 공격 표면

이 될 수 있습니다.

결국 현대 보안에서 중요한 것은 신뢰 가능한 UI가 정말 신뢰 가능한가를 끊임없이 검증하는 것입니다.
