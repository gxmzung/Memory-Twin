# System Architecture

## 전체 구조

Client
- React Web
- Flutter Mobile later

Backend
- FastAPI
- Auth
- Memory API
- Chat API
- Consent API
- Timeline API

Database
- PostgreSQL: 사용자, 권한, 메타데이터
- Qdrant: 임베딩 기반 기억 검색
- MinIO: 사진, 음성, 문서 파일 저장
- Redis: 캐시 및 세션

AI Layer
- Embedding Model
- Retriever
- Prompt Builder
- LLM
- Safety Filter
- Citation Engine

## 핵심 데이터 흐름
1. 사용자가 기억 데이터 업로드
2. 백엔드가 파일 저장
3. 텍스트 추출 및 전처리
4. 임베딩 생성
5. Qdrant 저장
6. 사용자가 질문 입력
7. 관련 기억 검색
8. Prompt Builder가 맥락 구성
9. LLM 응답 생성
10. 출처와 AI 고지 표시

## MVP 우선순위
1. Memory Archive
2. RAG Search
3. Chat with Citation
4. Consent Management
5. Timeline
