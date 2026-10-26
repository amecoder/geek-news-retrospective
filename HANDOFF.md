# HANDOFF.md

## Current State: 초기 설정 완료 (2026-10-26)

디렉터리 뼈대만 있다. `origin` = https://github.com/amecoder/geek-news-retrospective (public).

## Pending Tasks
- [ ] Hashnode PAT 발급 + publication ID 확인 → GitHub Secrets 등록
- [ ] 결정 필요: Hashnode 에 ko/en 을 둘 다 올릴지, 한 블로그에 두 글로 올릴지, en 만 올릴지
- [ ] 게시 스크립트(`scripts/`) TDD 로 구현 — 프론트매터 파싱, 생성/업데이트 분기
- [ ] GitHub Actions 워크플로(`.github/workflows/`) 작성
- [ ] 첫 회고 글 작성 (`posts/YYYY-MM-DD-<slug>/`)

## Completed Tasks
- [x] 프로젝트 초기 설정 (CLAUDE.md · HANDOFF.md · CHANGELOG.md · .gitignore · 디렉터리)
- [x] 공개 저장소 생성·푸시 — https://github.com/amecoder/geek-news-retrospective (`1abc0e0`)

## Key Decisions
- Hashnode 게시: GitHub Actions 자동 게시 (사용자 결정 2026-10-26)
- 글 언어: 한국어 + 영어 두 버전 (사용자 결정 2026-10-26)
- 아티클 1건 = `posts/` 아래 폴더 1개 (`source.md`·`ko.md`·`en.md`)
- 중복 게시 방지: 최초 게시 후 `hashnode_post_id` 를 프론트매터에 기록

## Files Modified
- CLAUDE.md · HANDOFF.md · CHANGELOG.md · .gitignore 생성
- posts/ · scripts/ · .github/workflows/ · docs/{plans,reports,architecture}/ (`.gitkeep`)
