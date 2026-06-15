# 이영준 개발 태스크

## MVP 기술 범위
v1.0 이전에는 Voice Clone, Avatar, 3D Human을 핵심 기능으로 넣지 않는다.
MVP는 Memory Archive + RAG Chat + Consent System으로 간다.

## v0.1
- FastAPI 백엔드 초기화
- User, Memory, File, Consent 모델 설계
- PostgreSQL 연결
- 기본 업로드 API 설계

## v0.3
- 텍스트 메모 저장
- 임베딩 생성
- Qdrant 저장
- Memory Search API 작성

## v0.5
- RAG 기반 대화
- 답변 출처 표시
- AI 고지 문구 표시

## v0.7
- Timeline 생성
- Family Profile
- Legacy Letter 예약 구조

## v1.0
- 웹 MVP
- 관리자 페이지
- 동의/삭제/권한 관리
- 베타 테스트 가능 상태

## 기술 스택
- Backend: FastAPI
- DB: PostgreSQL
- Vector DB: Qdrant
- Storage: MinIO
- Frontend: React
- Mobile: Flutter later
- AI: OpenAI API 또는 Local LLM
- Infra: Docker
