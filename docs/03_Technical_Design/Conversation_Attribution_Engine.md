# Conversation Attribution Engine

## 목적

Memory Twin은 대화 전체를 학습하지 않는다.
각 발화를 해당 화자의 Human Profile에 귀속시키는 구조를 사용한다.

---

## 기존 방식 (사용하지 않음)

카카오톡 전체
        │
        ▼
     AI 학습

문제점
- 제3자 개인정보 포함
- 소유권 불명확
- 법적 위험
- 삭제 불가능

---

## Memory Twin 방식

카카오톡
        │
        ▼
Message Parser
        │
        ▼
Speaker Attribution
        │
 ┌──────┴──────┐
 │             │
 ▼             ▼
엄마 발화      내 발화
 │             │
 ▼             ▼
엄마 Profile   내 Profile

---

## 핵심 원칙

발화의 소유권은 화자에게 귀속된다.

상대방이 말한 내용은
내 Human Profile에 저장하지 않는다.

---

## 처리 과정

Conversation

↓

Message Parser

↓

Speaker Detection

↓

Speaker Attribution

↓

Third Party Detection

↓

NER Masking

↓

Human Profile Storage

↓

Embedding

↓

Qdrant

↓

RAG

---

## 예시

엄마:
"밥 먹었니?"

나:
"응 먹었어."

↓

엄마 Profile

- 밥 먹었니?

↓

내 Profile

- 응 먹었어.

---

## 장점

- 삭제권 보장
- 제3자 권리 보호
- Human Profile 정확도 향상
- RAG 품질 향상
- 법적 리스크 감소

