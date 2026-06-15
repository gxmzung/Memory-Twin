# AI Pipeline

## 목적
개인의 사진, 텍스트, 음성, 문서 데이터를 AI가 검색 가능한 기억 단위로 구조화하고, 질문에 대해 관련 기억을 기반으로 응답한다.

## Pipeline
1. Data Upload
2. Preprocessing
3. Metadata Extraction
4. Embedding
5. Vector Storage
6. Retrieval
7. Prompt Building
8. LLM Generation
9. Safety Check
10. Response with Source

## 핵심 원칙
- AI는 실제 사람을 대체하지 않는다.
- AI 답변은 기록 기반 생성 결과임을 표시한다.
- 출처 없는 단정적 답변을 제한한다.
- 민감 데이터는 암호화하고 접근 권한을 검증한다.

## Hallucination 방지
- 검색된 기억 데이터만 답변 근거로 사용
- 관련 근거가 부족하면 모른다고 답변
- 실제 기록과 생성 답변을 구분 표시
