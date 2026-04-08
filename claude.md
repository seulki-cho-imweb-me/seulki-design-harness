## Git 워크플로우

작업 시작 전 반드시 아래 순서를 따른다.

1. `git pull` — 최신 상태 동기화
2. `git checkout -b feature/{ticket 또는 설명}` — 작업 브랜치 생성
3. 작업 진행
4. 커밋 후 `git push -u origin {브랜치명}`
5. `gh pr create`로 PR 생성

main 브랜치에 직접 커밋하지 않는다.

---

## 오케스트레이터

orchestrator/main.md 를 기준으로 동작한다.

## 스킬 파일 경로

- skills/problem-framer.md
- skills/clay-guide.md
- skills/design-validator.md
- skills/spec-writter.md