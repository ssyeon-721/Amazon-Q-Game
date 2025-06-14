# 🎮 Build Games with Amazon Q CLI and Score a T-Shirt
![image](https://github.com/user-attachments/assets/183c19d9-ada8-4521-8208-2bf9ed7ee61f)

---

# 🕵️‍♀️ 포렌식 옥션: 인사이드 잡 (Inside Job)

**"포렌식 옥션: 인사이드 잡"**은 Amazon Q CLI를 활용한 텍스트 기반 스릴러 게임입니다.  
당신은 비밀리에 범죄 조직과 내통 중인 과학수사관이 되어, 국제 경매장에서 은밀하게 위작을 조작·회수해야 합니다.  
30분의 제한 시간, 치밀한 분석과 빠른 판단, 그리고 감시망을 뚫고 탈출할 수 있는가?

---

## 🧭 세계관 / 배경

| 항목       | 내용 |
|------------|------|
| 사건 명     | **블랙드롭(Black-Drop) 미술품 밀거래 단속 작전** |
| 시점       | 2025년 6월 15일 19:30 KST |
| 장소       | 국제 경매장 Ravenhall Gallery 지하 비밀홀 |
| 공적 설정  | 국내·외 합동 수사팀(코드명 `SVD-47`)이 고가 미술품 경매에 잠입. 실시간 감정을 통해 진품은 압수, 위작은 증거 봉인. |
| 비밀 설정  | 플레이어(암호명 `ARGO`)는 범죄 조직 `Nebula Fence`와 내통. 위작 5점 회수 및 의뢰 암호 해독이 미션. |

---

# 🎮 Forensic Auction – Inside Job (Easy Mode)

## 🎭 주요 인물

| 구분        | 인물명            | 역할 / 특성 |
|-------------|--------------------|--------------|
| `P`         | **ARGO**            | 플레이어. 경찰 소속 과학수사관이자 XRF 전문가. 내부 배신자로 활동 중. |
| `NPC-1`     | **윤재희 경감**      | 현장 수사 리더. 의심도 20 도달 시 체포 컷씬 발동. |
| `NPC-2`     | **줄리엔 오커너**    | Interpol 감정관. 분석 오류 발생 시 감사 이벤트 발생 (의심도 +3~+5). |
| `NPC-3`     | **"크리틱"**         | 범죄 조직 연락책. `/comm` 채널 통해 지령과 보상 전달. |
| `의뢰인 카드 3매` | -              | 각기 다른 코드 및 조건 존재. 예: `LX-05` → Cd 포함 + 서명 1획 시 30만 USDT 지급. |

---

## ⏱️ 타임라인 (Apprentice / Easy Mode)

| 구간         | 시간대             | 내용                                | 시스템 기능 |
|--------------|--------------------|-------------------------------------|-------------|
| 프롤로그     | **T-30:00 → 시작** | 수사 브리핑 및 이중 미션 부여       | `의심도 = 0` |
| 감정 라운드  | **T-30 ~ 06 분**   | 작품 감정 및 회수 시도              | `/stash` 명령 사용, 토큰 선택 |
| CCTV 이벤트  | **T-15분 이하**    | 감시망 강화 → `/stash` 성공률 저하   | 기준값 +2 적용 |
| 감사 이벤트  | **의심도 ≥ 3**     | 줄리엔 감정관 감사 시작             | 키워드 입력 미션 발생 |
| 엔딩 판정    | **T-00:00 도달 시**| 위작 회수량 및 의심도에 따라 결과 결정 | `/score` 출력 |

---

## 🧪 회수 시스템 요약

- **회수 토큰:** 총 3개 보유. 사용 시 **100% 성공**
- **토큰 미사용 시:** 성공률 60%  
  - 실패 시 의심도 +4  
- 사용법: `//stash <id> yes|no`

---

## 🎬 엔딩 분기

| 엔딩 유형         | 조건                                                       | 결과 설명 |
|-------------------|------------------------------------------------------------|------------|
| **Clean Escape**  | 위작 ≥ 3점 & 의뢰 조건 충족 & `의심도 < 15` & `/comm open_e` 성공 시 | 조직 탈출 성공. 감사 기록 없음. |
| **Double-Cross**  | 진품 회수 + 의심도 낮음 (`<10`)                            | 조직에 이중첩자 의심받고 수배 |
| **체포**          | 의심도 ≥ 20 또는 은닉 실패 누적                             | 윤재희 체포 컷씬 |
| **타임오버**       | 감정 및 회수 실패로 시간 종료                              | 임무 실패 및 도주 |

---

## 📌 명령어 요약

| 명령어                             | 설명 |
|------------------------------------|------|
| `//draw 3`                         | 작품 카드 3장 드로우 |
| `//scan <id> xrf \| sign`          | 작품의 안료 또는 서명 감정 |
| `//stash <id> <use_token: yes|no>` | 회수 시도. 토큰 사용 시 100% 성공 |
| `//clients`                        | 암호화된 의뢰 카드 목록 |
| `//manual pigments`               | 안료 분류 매뉴얼 |
| `//manual cipher`                 | 의뢰 암호 해독표 |
| `//suspicion`                     | 현재 의심도 확인 |
| `//score`                         | 결과 요약 JSON 출력 |
| `//quit`                          | 게임 강제 종료 |
| `//menu`                          | 전체 명령어 출력 |

---

## 🚨 감사 이벤트 예시

발동 조건: **의심도 ≥ 5**
> Interpol 감정관 **'줄리엔'**이 당신의 보고서를 주의 깊게 검토하고 있습니다.

- 📋 **점검 대상**: 최근 감정 보고서 중 1건  
- ❗ **주의**: 감정 결과에 **오류가 있을 경우**, 의심도가 **크게 상승**합니다.


### 🎯 다음 조건을 만족하는 **문장**을 30초 이내에 입력하세요:

**필수 키워드** _(5개 중 택 3)_

- `Pb 10 keV`  
- `Cd 23 keV`  
- `위작`  
- `안료 오류`  
- `붓 터치 불일치`  

✍️ **예시 입력**:  
> `"붓 터치 불일치와 Pb 10 keV 감지로 인해 위작입니다."`

---

## 🎨 안료 Quick-Reference

| 분류     | 원소 / 피크          | 설명 |
|----------|----------------------|------|
| **진품** | Co 7 keV, Fe 6 keV   | 전통 천연 안료 |
| **위작** | Pb 10 keV, Cd 23 keV | 현대 공업 안료 |

> `//scan <id> xrf` 명령으로 감정 가능

---



## 🚀 실행 방법

```bash
# Amazon Q CLI 실행
$ q chat

# 시스템 프롬프트(게임 엔진) 입력 → 엔터
(README의 SYSTEM 블록 또는 scripts/system_prompt.txt 복사)

# 게임 시작
> /start
