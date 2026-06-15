# Safety Architecture

## 목적

Memory Twin의 모든 AI 응답은 권한, 동의, 데이터 등급, 안전 필터를 통과해야 한다.

---

## Safety Pipeline

사용자 질문
↓
Authentication Check
↓
Permission Check
↓
Consent Check
↓
Data Classification Check
↓
Third Party Data Filter
↓
RAG Search
↓
Context Builder
↓
LLM Generation
↓
Safety Filter
↓
Hallucination Check
↓
Citation Attach
↓
AI Disclosure Banner
↓
사용자 응답

---

## 1. Authentication Check

사용자가 인증된 계정인지 확인한다.

---

## 2. Permission Check

사용자가 해당 Memory Profile에 접근할 권한이 있는지 확인한다.

권한 예시:
- Owner
- Family Viewer
- Family Admin
- Legacy Receiver
- Legal Guardian

---

## 3. Consent Check

데이터 유형별 동의 여부를 확인한다.

동의가 없으면:
- 검색 대상 제외
- AI 응답 제외
- 가족 공유 제외
- 음성/영상 기능 제외

---

## 4. Data Classification Check

모든 데이터는 등급을 가진다.

| 등급 | 설명 | AI 사용 |
|---|---|---|
| A | 본인 단독 생성 데이터 | 가능 |
| B | 본인 중심 데이터 | 가능 |
| C | 공동 생성 데이터 | 제한 |
| D | 제3자 민감정보 포함 | 기본 제외 |
| E | 법적 제한 데이터 | 금지 |

---

## 5. Third Party Data Filter

카카오톡, 문자, 이메일 등에서 제3자 정보를 감지한다.

처리:
- 이름 마스킹
- 전화번호 마스킹
- 주소 마스킹
- 민감 주제 제거
- 상대방 발언 제외

---

## 6. RAG Search

허용된 데이터만 벡터 검색 대상으로 사용한다.

조건:
- 동의 있음
- 권한 있음
- AI 사용 가능 등급
- 제3자 민감정보 제거됨

---

## 7. Context Builder

검색된 기억을 질문과 함께 프롬프트로 구성한다.

규칙:
- 검색되지 않은 기억은 포함하지 않는다.
- 출처 ID를 유지한다.
- AI가 실제 인물처럼 말하지 않도록 시스템 규칙을 포함한다.

---

## 8. LLM Generation

LLM은 검색된 기록을 기반으로 답변한다.

금지:
- 실제 인물 사칭
- 고인의 의사 단정
- 상속·법률·의료 판단
- 출처 없는 기억 생성

---

## 9. Safety Filter

응답에서 위험 표현을 차단한다.

차단 예:
- "나는 네 엄마야"
- "내 유산은 너에게 줄게"
- "병원 가지 마"
- "이 투자를 해"
- "그 사람을 믿지 마"

---

## 10. Hallucination Check

답변에 출처가 없는 사실 주장이 있는지 확인한다.

출처 없는 경우:
- 삭제
- 완화 표현
- "기록이 부족합니다"로 대체

---

## 11. Citation Attach

응답에는 관련 Memory 출처를 첨부한다.

예:
- 2018년 가족 여행 메모
- 2020년 생일 편지
- 2022년 인터뷰 기록

---

## 12. AI Disclosure Banner

모든 응답에 고지 문구를 표시한다.

> 이 응답은 저장된 기록을 기반으로 AI가 생성한 결과이며, 실제 인물의 의사와 동일하다고 보장하지 않습니다.
