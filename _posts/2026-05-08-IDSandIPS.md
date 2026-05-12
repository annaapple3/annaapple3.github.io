---
title: "IDS/IPS 원리와 활용 방법"
layout: single
date: 2026-05-08
categories: [document]
---

<br>

#### 침입 탐지 및 방지 시스템
![IDS/IPS]({{ 'data:image/png;base64,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' | relative_url }})

#### IDS(침입 탐지 시스템)란
시스템의 정상적인 네트워크 운영과 비정상적이고 잠재적으로 유해한 활동을 구분하며 네트워크에 연결된 잠재적 위협과 취약점을 식별합니다. <br>
네트워크 트래픽을 검사하여 데이터 전송에 개입하지 않고도 관리자에게 의심스러운 활동을 경고하는 역할을 합니다.<br>

#### 유형
##### 1. 시그니처 기반 IDS<br>
미리 정의된 공격 패턴(Signature)과 현재 트래픽을 비교하여 공격 여부를 판단하는 방식입니다.
백신 프로그램이 악성코드 패턴을 비교하여 탐지하는 방식과 유사합니다.

특징
- 알려진 공격 탐지에 매우 효과적
- 탐지 속도가 빠름
- 오탐(False Positive)이 비교적 적음
  
단점
- 새로운 공격(Zero-Day Attack) 탐지가 어려움
- 지속적인 패턴 업데이트 필요

탐지 예시
- SQL Injection 패턴
- 특정 악성코드 시그니처
- 알려진 취약점 공격 코드

##### 2. 이상 징후 기반 IDS<br>
정상적인 네트워크 동작 패턴을 학습한 뒤, 평소와 다른 비정상 행위를 탐지하는 방식입니다.

특징
- 알려지지 않은 공격 탐지 가능
- 내부자 공격 탐지에 유리
- AI/머신러닝 기반 분석에도 활용

단점
- 정상 행위를 잘못 공격으로 판단하는 오탐 가능성 존재
- 초기 학습 과정 필요
- 환경 변화에 민감함

탐지 예시
- 갑작스러운 대량 트래픽 발생
- 새벽 시간대의 비정상 접속
- 특정 사용자의 평소와 다른 행동 패턴

- NIDS(네트워크 침입 탐지 시스템): 네트워크 트래픽을 감시하여 DoS 공격, 포트 스캔, 컴퓨터를 크랙하려는 시도 등과 같은 악의적인 동작들을 탐지하는 시스템
- HIDS(호스트 기반 침입 탐지 시스템): 개별 호스트의 운영체제 내부에 설치되어 시스템 파일 변경, 로그, 프로세스 활동 등을 실시간으로 모니터링하여 침입 및 내부 공격을 감지하는 보안 소프트웨어
- PIDS(프로토콜 기반 침입 탐지 시스템): 네트워크나 시스템에서 사용되는 특정 통신 프로토콜을 모니터링하고 분석하여 위협을 식별하는 보안 솔루션

#### 동작 원리
##### 1. 데이터 수집(Data Collection)
IDS는 먼저 네트워크와 시스템에서 다양한 데이터를 수집합니다.

- NIDS의 데이터 수집
NIDS는 네트워크 구간을 지나가는 패킷(Packet)을 수집합니다.
일반적으로 다음과 같은 방식으로 패킷을 가져옵니다.

- 스위치의 SPAN(Mirroring) 포트
- 네트워크 TAP 장비
- 허브 기반 네트워크
- 라우터 미러링 기능

수집 대상:
- IP 패킷
- TCP/UDP 헤더
- HTTP 요청
- DNS 질의
- 이메일 트래픽
- FTP 통신
예를 들어 공격자가 특정 서버에 대량의 SYN 패킷을 보내면, IDS는 이를 수집하여 분석 대상으로 저장합니다.

- HIDS의 데이터 수집
HIDS는 개별 시스템 내부 정보를 수집합니다.

수집 대상:
- 시스템 로그
- 사용자 로그인 기록
- 프로세스 실행 정보
- 파일 무결성 변경
- 레지스트리 변경
- 권한 상승 시도
- 서비스 실행 상태

ex) /etc/passwd 파일 변경
    관리자 권한 획득 시도
    비정상 프로세스 실행
등을 실시간으로 감시합니다.

##### 2. 전처리 및 정규화(Preprocessing & Normalization)
수집된 데이터는 분석하기 쉽도록 정리됩니다.

이 과정에서는 <br>
불필요한 데이터 제거 <br>
패킷 재조립(Fragment Reassembly) <br>
세션 추적(Session Tracking)<br>
프로토콜 해석(Protocol Decoding)<br>
등이 수행됩니다.
예를 들어 HTTP 요청이 여러 패킷으로 나뉘어 전송되었다면, IDS는 이를 다시 조립하여 하나의 요청으로 분석합니다.

##### 3. 패킷 및 이벤트 분석(Analysis Engine)
IDS의 핵심 단계입니다.
분석 엔진은 수집된 데이터를 기반으로 공격 여부를 판단합니다.
분석 방식은 크게 두 가지로 나뉩니다.

###### (1) 시그니처 기반 분석(Signature-based Detection)
이미 알려진 공격 패턴(Signature)과 비교하여 탐지하는 방식입니다.

동작 과정:
1. 패킷 수집
2. 패턴 데이터베이스와 비교
3. 일치 여부 확인
4. 공격 판단
예를 들어 다음과 같은 SQL Injection 패턴이 있다고 가정합니다.
```sql
' OR 1=1 --
```
IDS는 HTTP 요청 안에 해당 문자열이 포함되어 있는지 검사합니다.

특징:
- 빠르고 정확함
- 알려진 공격 탐지에 강함
- 오탐률이 낮음
  
단점:
- 새로운 공격 탐지 어려움
- 패턴 업데이트 필요

###### (2) 이상 징후 기반 분석(Anomaly-based Detection)
정상적인 시스템 동작 패턴을 기준으로 비정상 행위를 탐지하는 방식입니다.

동작 과정:
1. 정상 트래픽 학습
2. 기준(Baseline) 생성
3. 현재 상태와 비교
4. 이상 여부 판단

예를 들어 평소 초당 100개의 패킷이 발생하던 서버에서
갑자기 초당 10만 개의 패킷이 발생하면 이를 비정상 행위로 판단합니다.

머신러닝 활용
최근 IDS는 AI/머신러닝 기술을 이용하여<br>
사용자 행동 분석(UBA)<br>
트래픽 패턴 분석<br>
비정상 행위 예측<br>
등도 수행합니다.

특징:
- 알려지지 않은 공격 탐지 가능
- 내부자 공격 탐지 가능

단점
- 오탐률이 높을 수 있음
- 초기 학습 필요

###### 4. 탐지 및 정책 판단(Detection & Policy Decision)
분석 결과 공격으로 판단되면 IDS는 정책에 따라 행동합니다.
IDS는 일반적으로 다음 요소를 기준으로 판단합니다.

- 공격 위험도
- 공격 빈도
- 출발지 IP
- 대상 시스템 중요도
- 프로토콜 종류

동일 IP에서 짧은 시간 동안 수천 번 로그인 시도, 
비인가 포트 접근, 
비정상 DNS 요청, 
등을 침입 시도로 판단할 수 있습니다.

###### 5. 경고(Alert) 생성
침입이 탐지되면 관리자에게 경고를 전달합니다.

경고 방식:
- 이메일
- SMS
- 대시보드
- SIEM 연동
- 로그 파일 기록

경고 정보에는 일반적으로 다음 내용이 포함됩니다.

- 공격 시간
- 공격 유형
- 출발지/목적지 IP
- 사용된 프로토콜
- 위험 수준(Severity)

예시:
```
[ALERT]
Potential Port Scan Detected
Source IP: 192.168.1.15
Destination IP: 10.0.0.5
Severity: High
```

###### 6. 로그 저장 및 포렌식(Logging & Forensics)
탐지 결과는 로그 형태로 저장됩니다.

이 로그는<br>
사고 분석<br>
디지털 포렌식<br>
공격 경로 추적<br>
보안 정책 개선<br>
등에 활용됩니다.

특히 기업 환경에서는 IDS 로그를 SIEM(Security Information and Event Management) 시스템과 연동하여 중앙에서 통합 관리합니다.

대표적인 SIEM 솔루션:
- Splunk
- Elastic Stack

###### 장점
- 항시 모니터링: 서비스 중단이나 지연 없이 안전하게 네트워크를 모니터링합니다.
- 다양한 위협 탐지: 정상적이지 않은 트래픽 패턴부터 알려진 위협까지 다양한 공격을 탐지할 수 있습니다.
- 유연성: 다양한 환경에 적용이 가능하며 위치에 따른 제약이 적습니.

###### 단점
- 반응의 부재: 공격을 단순히 탐지하고 알릴 뿐 자동으로 차단하지 않습다.
- 미탐 가능성: 패턴에 없는 새로운 공격은 탐지가 불가능합니다.
- 우회 가능성: 공격자가 IDS의 탐지 메커니즘을 알 경우, 우회하는 방법으로 공격을 시도할 수 있습니다.

---

#### IPS(침입 방지 시스템)란
위협이 네트워크 방어에 침투하기 전에 <br> 선제적으로 작동하여 위협을 완화하는 등 <br>
악성 트래픽을 실시간으 차단하고 분석하는 동적 보안 솔루션입니다.

#### 유형
- 데이터 수집 방식
  - NIPS: 네트워크 내 주요 지점에 Inline으로 설치되어 실시간 트래픽을 감시하고, 해킹·웜·바이러스 등 악성 트래픽을 선제적으로 탐지하여 차단하는 능동형 보안 시스템
  - HIPS: 개별 호스트에 설치되어 맬웨어, 해킹 시도 등 시스템에 부정적인 영향을 주는 행위를 실시간으로 모니터링하고 차단하는 보안 솔루션
  
- 탐지 방식
  - Misuse(오용 탐지): 이미 알려진 공격 패턴과 비교하여 탐지하는 방식
  - Anomaly(이상 탐지): 정상 행위 기준에서 벗어난 트래픽을 탐지하는 방식

#### 동작 원리
##### 1. Inline 방식으로 트래픽 수신
IPS는 네트워크 중간에 Inline 형태로 설치됩니다.
즉, 모든 트래픽이 IPS를 반드시 통과해야 합니다.

구조 예시:<br>
인터넷 → 방화벽 → IPS → 내부 네트워크<br>
따라서 IPS는 패킷을 직접 검사하고 제어할 수 있습니다.

##### 2. 패킷 검사(Packet Inspection)
IPS는 들어오는 패킷을 실시간으로 검사합니다.

검사 항목:
- 패킷 헤더
- 페이로드 데이터
- 세션 상태
- 프로토콜 규칙
- 공격 시그니처

##### 3. 위협 분석 및 탐지

IDS와 동일하게 시그니처 기반 탐지
이상 탐지 기반 분석을 수행합니다.

추가적으로 IPS는<br>
DPI(Deep Packet Inspection)<br>
애플리케이션 계층 분석(L7)<br>
SSL/TLS 복호화 검사<br>
등 고급 분석 기술도 활용합니다.

###### 4. 차단 및 대응(Response)
공격으로 판단되면 IPS는 즉시 대응합니다.

대응 방식:
- 패킷 드롭(Drop)
- 세션 종료(TCP Reset)
- IP 차단
- 포트 차단
- 속도 제한(Rate Limiting)

예를 들어 DDoS 공격이 탐지되면
공격 IP를 차단하고,
비정상 세션을 종료하며
관리자에게 경고를 보냅니다.

5. 이벤트 기록 및 정책 업데이트
모든 차단 이벤트는 로그로 저장됩니다.
또한 최신 공격 패턴에 대응하기 위해
시그니처 업데이트,
정책 업데이트,
위협 인텔리전스 연동
등이 지속적으로 수행됩니다.

###### 장점
- 능동적인 방어: 실시간으로 위협에 대응하며, 자동으로 공격을 차단합니다.
- 다양한 차단 기능: IP 주소, 프로토콜, 특정 서명 등 다양한 방법으로 위협을 차단합니다.
- 동적 업데이트: 새로운 위협 패턴에 빠르게 대응할 수 있습다.

###### 단점
- 오탐 가능성: 공격 패턴 학습자체가 잘못되는 경우에는 침입이 아닌데, 침입이라고 판단 할 수가 있습니다.
- 성능 부하: 높은 성능의 장비가 필요할 수 있습니다.
- 네트워크 속도 저하 가능성: 패킷을 일일히 분석하고 대응하기 때문에, 장비 성능에 따라 네트워크 속도가 저하될 수 있습니다.

---

#### IDS와 IPS의 차이점

| 구분 | IDS | IPS |
| :--- | :--- | :--- |
| **목적** | 모니터링하여 악의적인 행위나 정책 위반을 감시 | 트래픽을 분석하여 식별된 위협을 실시간으로 검사하고 방지 |
| **운영** | 트래픽을 관찰하고 공격 패턴이나 이상 징후를 찾아 경고 | 트래픽에 대한 실시간 공격을 검사하고 탐지 시 이를 차단하기 위해 개입 |
| **기능** | 탐지 / 분석 / 보고 | 차단 / 탐지 / 분석 / 보고 |
| **트래픽 경로** | 방화벽을 통과한 후 트래픽을 분석 | 필터링된 트래픽을 검사하기 위해 방화벽 뒤에 배치 |
| **무단 트래픽에 대한 대응** | 의심스러운 활동을 감지하면 경고 | 탐지된 위협의 진행을 적극적으로 방지 |

#### 활용 방법
방화벽으로 초기 트래픽을 필터링한 뒤, <br>
IDS와 IPS는 필터링된 트래픽을 분석하여 잠재적인 위협을 확인하는 식으로 활용합니다.<br>
계층화된 접근 방식은 위협이 방화벽을 우회하더라도<br>
IDS가 관리자에게 의심스러운 활동을 경고하고<br>
IPS가 위협으로 인한 피해를 방지하기 위해 조치를 취할 수 있도록 합니다.
