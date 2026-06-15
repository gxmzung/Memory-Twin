# Human Profile Layer

## 핵심 결론

Memory Twin은 개인 데이터를 직접 모델에 파인튜닝하지 않는다.  
대신 생전 동의가 확인된 데이터를 여러 레이어로 분리하여 Human Profile을 구성하고, 사용자의 질문이 들어오면 필요한 레이어만 RAG 방식으로 검색하여 답변을 생성한다.

즉, Memory Twin의 핵심은 "AI 학습"이 아니라 "기억과 말투, 가치관을 구조화한 Human Profile + RAG"이다.

---

## Human Profile 구조

Human Profile
├── Identity
├── Memory
├── Personality
├── Conversation Style
├── Voice Metadata
├── Behavior
├── Values
├── Relationships
└── Preferences

---

## 1. Identity Layer

개인의 기본 정체성 정보.

예시:
- 이름
- 생년월일
- 가족관계
- 직업
- 주요 생애 사건

사용 목적:
- 프로필 구성
- 타임라인 기준점
- 가족관계 연결

---

## 2. Memory Layer

개인의 기억과 사건 기록.

예시:
- 일기
- 메모
- 편지
- 사진 설명
- 여행 기록
- 가족 행사 기록
- 생애 타임라인

사용 목적:
- Memory Archive
- Timeline
- RAG 검색
- 기억 기반 답변

---

## 3. Personality Layer

성격과 가치관을 표현하는 데이터.

예시:
- 좋아하는 것
- 싫어하는 것
- 인생 철학
- 자주 하던 조언
- 가족에게 중요하게 여긴 가치
- 의사결정 기준

사용 목적:
- 답변의 가치관 근거
- Legacy Letter
- 가족 기억 해석

---

## 4. Conversation Style Layer

말투와 대화 습관을 표현하는 데이터.

예시:
- 자주 쓰는 말
- 문장 길이
- 이모티콘 습관
- 말버릇
- 농담 방식
- 사투리 표현
- 반응 패턴

주의:
카카오톡, 문자, 이메일 등 양방향 대화 데이터는 제3자 발언을 포함하므로 기본적으로 제한 데이터로 분류한다.

사용 목적:
- 답변 스타일 조정
- 말투 요약
- 대화형 응답의 자연스러움 향상

---

## 5. Voice Metadata Layer

목소리 자체를 복제하지 않고, 음성의 특징만 메타데이터로 저장한다.

예시:
- 말 속도
- 억양
- 사투리
- 감정 톤
- 자주 웃는 패턴
- 말 끊는 방식

MVP 정책:
음성 클론은 MVP에서 제외한다.  
음성 파일은 STT를 통해 텍스트 기억으로 변환하는 용도로만 사용한다.

---

## 6. Behavior Layer

생활 습관과 행동 패턴.

예시:
- 아침 루틴
- 자주 가던 장소
- 기념일 습관
- 식사 취향
- 가족에게 하던 행동
- 의사결정 습관

---

## 7. Values Layer

중요하게 여긴 가치.

예시:
- 가족
- 성실함
- 건강
- 신앙
- 교육
- 도전
- 절약
- 배려

사용 목적:
사용자가 "이 상황에서 어떤 조언을 했을까?"라고 물었을 때, 단정적 답변이 아니라 저장된 가치관을 근거로 참고 응답을 제공한다.

---

## 8. Relationships Layer

관계 정보.

예시:
- 가족
- 친구
- 동료
- 은사
- 제자
- 지인

주의:
제3자 개인정보는 자동 마스킹 또는 별도 동의가 필요하다.

---

## 9. Preferences Layer

취향 정보.

예시:
- 음식
- 음악
- 영화
- 장소
- 색상
- 말투 선호
- 선물 취향

---

## 답변 생성 방식

사용자 질문
↓
Permission Check
↓
Consent Check
↓
Data Classification
↓
Relevant Layer Search
↓
RAG Context Build
↓
LLM Response
↓
Safety Filter
↓
Citation Attach
↓
AI Disclosure
↓
사용자 응답

---

## 핵심 원칙

1. 모델에 직접 학습시키지 않는다.
2. 삭제 가능한 데이터 구조를 유지한다.
3. 제3자 데이터는 기본적으로 AI 활용에서 제외한다.
4. 음성 클론은 MVP에서 제외한다.
5. 답변은 출처 기반으로만 생성한다.
6. 근거가 부족하면 추측하지 않는다.
7. 실제 인물의 의사를 단정하지 않는다.
