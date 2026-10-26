# CLAUDE.md

## 프로젝트 개요
GeekNews(news.hada.io) 아티클을 골라 **심도 있게 회고**하는 글을 쓰고, 두 곳에 공개한다.

1. **GitHub 공개 저장소** — 이 저장소 자체가 회고 아카이브다 (마크다운 원본)
2. **Hashnode 블로그** — `main` 에 머지되면 GitHub Actions 가 Hashnode GraphQL API 로 자동 게시

글은 **한국어 + 영어** 두 버전을 쓴다.

## 기술 스택
- 콘텐츠: Markdown + YAML 프론트매터
- 게시 스크립트: Python 3 + `uv` (의존성·실행 관리)
- 자동화: GitHub Actions (`main` push 트리거)
- 게시 대상: Hashnode GraphQL API (`https://gql.hashnode.com`) — 스키마·뮤테이션 이름은 구현 시 context7/공식 문서로 확인할 것

## 프로젝트 구조
```
posts/
  YYYY-MM-DD-<slug>/        # 아티클 1건 = 폴더 1개
    source.md               # 원문 정보: GeekNews URL, 원 출처 URL, 요약·인용 메모
    ko.md                   # 한국어 회고 (프론트매터 포함)
    en.md                   # 영어 회고 (프론트매터 포함)
    assets/                 # 그림 (Excalidraw .excalidraw + .svg)
scripts/                    # Hashnode 게시 스크립트 (Python)
.github/workflows/          # 자동 게시 워크플로
docs/plans|reports|architecture/  # 작업 계획·보고·설계 문서
```

## 회고 글 작성 규칙
- **요약이 아니라 회고다.** 최소한 다음을 담는다: 아티클 핵심 주장 → 내 경험·맥락과의 연결 → 동의/반론과 근거 → 실제로 바꿔볼 행동
- 원문 인용은 짧게, 출처 URL 을 항상 붙인다 (저작권 — 원문 전문 전재 금지)
- 사실 주장에는 출처를 단다. 확인 못 한 내용은 확인 못 했다고 쓴다
- `en.md` 는 `ko.md` 의 기계 번역이 아니라 영어 독자 기준으로 다듬는다
- 그림은 Excalidraw (`excalidraw` 스킬) — Mermaid 를 쓰지 않는다

### 프론트매터 (ko.md / en.md 공통 — 초안, 게시 스크립트 구현 시 확정)
```yaml
---
title: "..."
slug: "..."              # Hashnode URL slug
lang: ko                 # ko | en
tags: [geeknews, retrospective]
geeknews_url: "https://news.hada.io/topic?id=..."
source_url: "..."
published: false         # true 로 바꾼 글만 게시 대상
hashnode_post_id: ""     # 최초 게시 후 기록 → 이후엔 업데이트로 처리(중복 게시 방지)
---
```

## 개발 규칙
- 작업은 feature 브랜치(`post/<slug>`, `feat/<name>`)에서 하고 PR 로 머지한다
- 커밋은 사용자 요청 시에만, 메시지는 한글 `<타입>: <제목>` — 글 추가는 `문서:` 타입
- Hashnode 토큰(PAT)·publication ID 는 **코드에 넣지 않는다** — 로컬은 `.env`, CI 는 GitHub Secrets
- `git add` 는 경로를 지정해서 한다 (샌드박스가 홈 dotfile 경로를 빈 장치로 덮어 보이게 하므로 — `.git/info/exclude` 에 제외 등록됨)

## 주요 커맨드
- (게시 스크립트 구현 후 채운다)
