---
description: skills.sh에서 새로운 유용한 스킬을 검색하고 설치하는 정기 워크플로우 (주 1회 권장)
---

# 새로운 스킬 검색 및 설치

매주 1회 실행하여 최신 유용한 스킬을 검색, 비교, 설치하는 워크플로우.

## 사전 조건
- `npx skills` CLI 사용 가능
- 스킬 설치 경로: `~/.gemini/antigravity/skills/`

## 워크플로우

### 1단계: 현재 설치된 스킬 목록 확인
// turbo
```bash
ls ~/.gemini/antigravity/skills/ | sort
```

### 2단계: skills.sh 사이트에서 인기/최신 스킬 브라우징
브라우저로 https://skills.sh/ 을 방문하여 인기 스킬 리스트를 확인한다.

### 3단계: CLI로 관심 카테고리별 스킬 검색
유용할 수 있는 카테고리들을 검색:
// turbo
```bash
npx skills find "react"
npx skills find "testing"
npx skills find "deployment"
npx skills find "ai agent"
npx skills find "database"
npx skills find "design"
```

### 4단계: 새로운 스킬 발견 시 사용자에게 보고
- 스킬 이름, 설명, 출처를 표로 정리
- 이미 설치된 스킬은 제외
- 사용자에게 설치 여부를 확인 받기

### 5단계: 승인된 스킬 설치
```bash
npx skills add <owner/repo@skill-name> -g -y
```

### 6단계: 설치된 스킬 업데이트 확인
// turbo
```bash
npx skills check
npx skills update
```

## 참조 사이트
| 사이트 | URL | 용도 |
|---|---|---|
| Skills 브라우저 | https://skills.sh/ | 스킬 검색/순위/브라우징 |
| Agent Skills 공식 | https://agentskills.io | 공식 문서/스펙 |
| Anthropic 예제 | https://github.com/anthropics/skills | 공식 예제 스킬 |
| Awesome Claude Skills | https://github.com/ComposioHQ/awesome-claude-skills | 커뮤니티 스킬 모음 |
| Agent Skills CC | https://agent-skills.cc | GitHub 기반 인기 스킬 |
| MCP Market | https://mcpmarket.com | 스킬 리더보드 |
