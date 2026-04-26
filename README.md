# esg-survey

ESG AI 컨설팅 전문가 평가 설문 사이트 — 한성대학교 박사학위 연구 (노은미)

## 시스템 구조

- **단일 HTML** (`index.html`) + Vanilla JS + Supabase 직접 호출
- 어드민(`esg-agent-admin`)과 **같은 Supabase 프로젝트** 공유
  - URL: `https://mwkdtasjkktqqlqefdhr.supabase.co`
  - Anon Key 사용 (어드민과 동일 패턴)
- Vercel 자동 배포 (main 푸시 시)

## 진입 방식

- `https://esg-survey-peach.vercel.app/?token={토큰}`
- 토큰은 어드민 `검증 링크 관리` 페이지에서 발급
- 토큰 검증 → 회사 정보 + 보고서 다운로드 → 5차원 평가 → 응답 저장

## DB 테이블

- `diagnosis_results` (어드민이 사용 중, 그대로 읽음)
- `survey_invitations` (토큰 발급)
- `survey_responses` (응답 저장)

## Storage

- 버킷: `sample-reports`
- 경로 규칙: `{diagnosis_id}/{filename}` (어드민이 업로드)

## 일정

- 5/11(월): 전문가 설문 오픈 (D-15)

## 작업 사이클

새 채팅 Claude → 지시문 .md → 저장소 루트 저장 → Claude Code read → 자동 커밋·푸시 → Vercel 자동 배포 → 시크릿 창 검증
