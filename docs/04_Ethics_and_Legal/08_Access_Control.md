# 08. Access Control

## 목적

Memory Twin은 민감한 가족 기억 데이터를 다루므로 강력한 권한 관리 체계가 필요하다.

## 권한 체계

- User
- Family Viewer
- Family Admin
- Legacy Receiver
- Service Admin
- Legal Guardian

## 접근 통제 원칙

1. 최소 권한 원칙
2. 역할 기반 접근 제어
3. 데이터 유형별 접근 분리
4. 모든 접근 로그 기록
5. 관리자 접근 제한
6. 민감 데이터 다운로드 제한

## 기술 구현

- JWT 인증
- RBAC
- MFA 선택 적용
- Audit Log
- Signed URL 기반 파일 접근
- 관리자 접근 승인 절차

## 접근 로그 항목

- 사용자 ID
- 접근 시간
- 접근 데이터 유형
- 접근 행위
- IP
- 기기 정보
- 성공/실패 여부
