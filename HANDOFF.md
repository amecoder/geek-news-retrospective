# HANDOFF.md

## Current State: 첫 원문 정리 머지 (2026-10-28)

`origin` = https://github.com/amecoder/geek-news-retrospective (public).
Dan Koe 글 원문 정리(`source.md`)가 PR #1 로 머지됐다. 회고(`ko.md`·`en.md`)는 아직 없다.

## Pending Tasks
- [ ] Dan Koe 회고 `ko.md` — 사용자 답 대기: ① 프로토콜을 해 봤는지 ② "행동보다 정체성"과 "불편하면 빠르게 고친다"의 관계 ③ 비판하고 싶은 점·써먹을 점
- [ ] Dan Luu 회고 (`post/danluu-ambitious`, 미커밋 · `posts/2026-10-26-danluu-ambitious/` 는 untracked) — `ko.md` 마지막 문단(추측) 확인, geeknews_url 미확인, 사례 보강 여부
- [ ] stash `translation-policy` (전문 번역은 허락·라이선스 근거가 있을 때만) — 계속 가져갈지 결정
- [ ] Hashnode PAT 발급 + publication ID 확인 → GitHub Secrets 등록
- [ ] 결정 필요: Hashnode 에 ko/en 을 둘 다 올릴지, 한 블로그에 두 글로 올릴지, en 만 올릴지
- [ ] 게시 스크립트(`scripts/`) TDD 로 구현 — 프론트매터 파싱, 생성/업데이트 분기
- [ ] GitHub Actions 워크플로(`.github/workflows/`) 작성

## Completed Tasks
- [x] 프로젝트 초기 설정 (CLAUDE.md · HANDOFF.md · CHANGELOG.md · .gitignore · 디렉터리)
- [x] 공개 저장소 생성·푸시 — https://github.com/amecoder/geek-news-retrospective (`1abc0e0`)
- [x] PR #1 — Dan Koe 「How to fix your entire life in 1 day」 원문 정리 (squash `5e26dbf`, 2026-10-28). WebFetch 대조 + Gemini 4 Argon 교차 검증 + 스크린샷 PDF 직접 대조. 도입부(I절 앞)는 PDF 에 없어 미확인

## Key Decisions
- Hashnode 게시: GitHub Actions 자동 게시 (사용자 결정 2026-10-26)
- 글 언어: 한국어 + 영어 두 버전 (사용자 결정 2026-10-26)
- 아티클 1건 = `posts/` 아래 폴더 1개 (`source.md`·`ko.md`·`en.md`)
- 중복 게시 방지: 최초 게시 후 `hashnode_post_id` 를 프론트매터에 기록
- 원문 전문 번역은 하지 않는다 — `source.md` 는 절별 요지 정리 (CLAUDE.md 저작권 규칙)
- 원문 정리는 다른 모델로 교차 검증한다. Codex 가 실패하면 Gemini 4 Argon(`agy`) (사용자 결정 2026-10-26)

## 주의·함정
- `gh`·`git push` 는 단독 명령으로. 여러 줄 본문을 넣은 `gh pr create` 는 샌드박스 안에서 돌아 가짜 401 이 난다 → `--body-file` 사용
- 이 저장소는 public — 커밋하면 곧 공개된다. 비공개로 정한 글은 커밋하지 않는다

## Files Modified
- CLAUDE.md · HANDOFF.md · CHANGELOG.md · .gitignore 생성
- posts/ · scripts/ · .github/workflows/ · docs/{plans,reports,architecture}/ (`.gitkeep`)
