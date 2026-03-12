---
description: skills.sh에서 새로운 스킬을 검색하고 설치하는 방법
---

# Skills.sh 스킬 관리 워크플로우

## 정기 스킬 검색 (주 1회 권장)

### 1. 트렌딩 스킬 확인
https://skills.sh/trending 에서 최근 인기 스킬 확인

### 2. 유용한 스킬 설치
```bash
// turbo
npx skills add <owner/repo>
```

### 3. 현재 설치된 스킬 확인
```bash
// turbo
ls ~/.gemini/antigravity/skills/
```

## 추천 소스 저장소

| 저장소 | 스킬 종류 |
|--------|----------|
| anthropics/skills | PDF, DOCX, PPTX, 프론트엔드, 디자인 |
| ComposioHQ/awesome-claude-skills | 보안, Docker, API, DB, 아키텍처 |
| vercel-labs/agent-skills | React, Next.js, 웹 디자인, 배포 |
| obsidianmd/obsidian-skills | Obsidian 마크다운, 데이터베이스 |
| remotion-dev/agent-skills | Remotion 비디오 제작 |
| expo/skills | React Native, Expo |
| inference-sh/skills | AI 이미지/비디오 생성 |
| coreyhaines31/marketingskills | SEO, 카피라이팅, 마케팅 |

## 에이전트에게 스킬 요청

"skills.sh에서 [기능] 관련 새로운 스킬을 검색해서 설치해줘"

예시:
- "skills.sh에서 Vue.js 관련 스킬 검색해줘"
- "마케팅 스킬 중 새로 추가된 것 있는지 확인해줘"
