---
name: antigravity-setup-kit
description: "안티그래비티 파워 유저 세팅 원클릭 설치. 이 스킬을 설치한 후 '안티그래비티 세팅해줘'라고 요청하면, MCP 서버 7개, 스킬 70개, 워크플로우, 브라우저 허용 목록, 모바일 에이전트까지 전체 환경이 자동 구성됩니다."
---

# 안티그래비티 파워 유저 세팅 원클릭 설치

이 스킬은 안티그래비티를 **최강의 AI 코딩 에이전트**로 만들어주는 전체 세팅 패키지입니다.
사용자가 **"안티그래비티 세팅해줘"** 또는 **"이 스킬 실행해줘"**라고 요청하면, 아래 6단계를 순서대로 실행하세요.

> **중요**: 각 단계에서 사용자에게 진행 상황을 알리고, API 키 등 민감 정보는 반드시 사용자에게 물어보세요.

---

## STEP 1. MCP 서버 설정 (핵심 서비스 연결)

MCP(Model Context Protocol) 서버는 안티그래비티가 외부 서비스와 통신하는 채널입니다.

### 1-1. 템플릿 읽기
이 스킬 폴더의 `config/mcp_config_template.json` 파일을 읽으세요.

### 1-2. 사용자에게 API 키 요청
각 서비스별로 사용자에게 키를 요청하세요. 아래는 필요한 항목들입니다:

| 서비스 | 필요한 키 | 발급 방법 |
|--------|-----------|----------|
| **GitHub** | Personal Access Token | https://github.com/settings/tokens → "Generate new token (classic)" → repo, workflow 권한 선택 |
| **Notion** | Integration Token | https://www.notion.so/my-integrations → 새 통합 만들기 |
| **Airtable** | API Key | https://airtable.com/account → API 섹션 |
| **Google Workspace** | OAuth Client ID/Secret | Google Cloud Console → API & Services → Credentials |
| **Google Dev Knowledge** | API Key | https://console.cloud.google.com → Developer Knowledge API 활성화 |

**선택 사항 (사용하지 않으면 건너뛰기):**
- Slack: Bot Token + Team ID

### 1-3. mcp_config.json 생성
템플릿의 `<PLACEHOLDER>` 값들을 사용자가 제공한 키로 교체하고, 안티그래비티 설정 디렉토리에 저장하세요:

```bash
# 저장 경로
~/.gemini/antigravity/mcp_config.json
```

> **⚠️ 주의**: 사용자가 키를 제공하지 않은 서비스는 해당 블록을 제거하세요. 빈 플레이스홀더가 있으면 오류가 발생합니다.
> **⚠️ memory 서버**: API 키가 필요 없으므로 항상 포함하세요.
> **⚠️ google-dev-knowledge**: URL 기반이므로 API 키만 URL에 포함하면 됩니다.

### 1-4. MCP 서버 확인
설정 후 안티그래비티를 재시작하라고 안내하세요. MCP 서버는 재시작 후 자동으로 연결됩니다.

---

## STEP 2. 핵심 스킬 일괄 설치

이 스킬 폴더의 `config/skills_manifest.json` 파일을 읽고, 우선순위별로 설치하세요.

### 2-1. 필수 스킬 설치 (core)
```bash
# anthropics/skills 패키지 (문서/프레젠테이션/디자인)
npx skills add anthropics/skills@docx -g -y
npx skills add anthropics/skills@pdf -g -y
npx skills add anthropics/skills@pptx -g -y
npx skills add anthropics/skills@xlsx -g -y
npx skills add anthropics/skills@frontend-design -g -y
npx skills add anthropics/skills@canvas-design -g -y
npx skills add anthropics/skills@brand-guidelines -g -y
npx skills add anthropics/skills@web-artifacts-builder -g -y
npx skills add anthropics/skills@theme-factory -g -y
npx skills add anthropics/skills@slack-gif-creator -g -y
npx skills add anthropics/skills@algorithmic-art -g -y
npx skills add anthropics/skills@json-canvas -g -y
```

### 2-2. 개발 워크플로우 스킬 설치
```bash
npx skills add anthropics/skills@brainstorming -g -y
npx skills add anthropics/skills@doc-coauthoring -g -y
npx skills add anthropics/skills@executing-plans -g -y
npx skills add anthropics/skills@writing-plans -g -y
npx skills add anthropics/skills@planning-with-files -g -y
npx skills add anthropics/skills@dispatching-parallel-agents -g -y
npx skills add anthropics/skills@subagent-driven-development -g -y
npx skills add anthropics/skills@finishing-a-development-branch -g -y
npx skills add anthropics/skills@using-git-worktrees -g -y
npx skills add anthropics/skills@using-superpowers -g -y
npx skills add anthropics/skills@writing-skills -g -y
npx skills add anthropics/skills@lint-and-validate -g -y
npx skills add anthropics/skills@verification-before-completion -g -y
npx skills add anthropics/skills@requesting-code-review -g -y
npx skills add anthropics/skills@receiving-code-review -g -y
npx skills add anthropics/skills@systematic-debugging -g -y
npx skills add anthropics/skills@test-driven-development -g -y
npx skills add anthropics/skills@create-pr -g -y
npx skills add anthropics/skills@find-skills -g -y
npx skills add anthropics/skills@skill-creator -g -y
npx skills add anthropics/skills@internal-comms -g -y
npx skills add anthropics/skills@prompt-engineer -g -y
npx skills add anthropics/skills@notebooklm -g -y
```

### 2-3. 에이전트 아키텍처 스킬 설치
```bash
npx skills add anthropics/skills@context-fundamentals -g -y
npx skills add anthropics/skills@context-compression -g -y
npx skills add anthropics/skills@context-degradation -g -y
npx skills add anthropics/skills@context-optimization -g -y
npx skills add anthropics/skills@filesystem-context -g -y
npx skills add anthropics/skills@memory-systems -g -y
npx skills add anthropics/skills@multi-agent-patterns -g -y
npx skills add anthropics/skills@hosted-agents -g -y
npx skills add anthropics/skills@tool-design -g -y
npx skills add anthropics/skills@bdi-mental-states -g -y
npx skills add anthropics/skills@evaluation -g -y
npx skills add anthropics/skills@advanced-evaluation -g -y
npx skills add anthropics/skills@project-development -g -y
npx skills add anthropics/skills@agent-browser -g -y
npx skills add anthropics/skills@webapp-testing -g -y
```

### 2-4. 전문 기술 스킬 설치
```bash
# ComposioHQ/awesome-claude-skills
npx skills add ComposioHQ/awesome-claude-skills@security-auditor -g -y
npx skills add ComposioHQ/awesome-claude-skills@docker-expert -g -y
npx skills add ComposioHQ/awesome-claude-skills@api-design-principles -g -y
npx skills add ComposioHQ/awesome-claude-skills@database-design -g -y
npx skills add ComposioHQ/awesome-claude-skills@architecture -g -y
npx skills add ComposioHQ/awesome-claude-skills@debugging-strategies -g -y
npx skills add ComposioHQ/awesome-claude-skills@python-patterns -g -y
npx skills add ComposioHQ/awesome-claude-skills@react-patterns -g -y
npx skills add ComposioHQ/awesome-claude-skills@typescript-expert -g -y
npx skills add ComposioHQ/awesome-claude-skills@rag-engineer -g -y
npx skills add ComposioHQ/awesome-claude-skills@mcp-builder -g -y
npx skills add ComposioHQ/awesome-claude-skills@seo-audit -g -y
npx skills add ComposioHQ/awesome-claude-skills@ui-ux-pro-max -g -y

# Vercel
npx skills add vercel-labs/agent-skills@vercel-deployment -g -y
npx skills add vercel-labs/agent-skills@vercel-react-best-practices -g -y
npx skills add vercel-labs/agent-skills@web-design-guidelines -g -y

# Obsidian
npx skills add obsidianmd/obsidian-skills@obsidian-markdown -g -y
npx skills add obsidianmd/obsidian-skills@obsidian-bases -g -y

# Remotion 비디오 제작
npx skills add remotion-dev/agent-skills@remotion-best-practices -g -y
```

### 2-5. 커스텀 스킬 (수동 설치 안내)
아래 스킬은 사용자가 직접 만든 것이므로 수동 설치가 필요합니다:
- `seedance-api`: BytePlus Seedance API 기반 비디오 생성 스킬 → 별도 안내

> **💡 팁**: 설치 중 일부 스킬이 이미 존재하면 자동으로 건너뜁니다. 오류가 나도 무시해도 됩니다.
> **💡 팁**: 모든 스킬이 한 번에 안 될 수 있으니, 5~10개씩 묶어서 실행하세요.

---

## STEP 3. 워크플로우 설치

워크플로우는 안티그래비티가 특정 작업을 자동 수행하는 절차서입니다.

이 스킬 폴더의 `workflows/` 디렉토리에 있는 파일들을 복사하세요:

```bash
# 대상 경로
mkdir -p ~/.gemini/antigravity/.agent/workflows/

# 이 스킬의 workflows/ 내용을 복사
cp workflows/*.md ~/.gemini/antigravity/.agent/workflows/
```

복사할 파일:
- `find-new-skills.md` — 주간 새 스킬 검색/설치 워크플로우
- `skills-management.md` — 스킬 관리/업데이트 워크플로우

---

## STEP 4. 브라우저 허용 목록 설정

안티그래비티가 접근 가능한 웹사이트 목록입니다.

이 스킬 폴더의 `config/browser_allowlist.txt` 파일을 복사하세요:

```bash
cp config/browser_allowlist.txt ~/.gemini/antigravity/browserAllowlist.txt
```

이 목록에는 GitHub, Google Cloud, MDN, Stack Overflow 등 개발에 필요한 82개 도메인이 포함되어 있습니다.

---

## STEP 5. 유저 규칙 설정 (수동)

이 스킬 폴더의 `config/user_rules_template.md` 파일을 읽고, 사용자에게 다음을 안내하세요:

> "안티그래비티 설정 > User Rules에 이 내용을 복사해서 붙여넣으세요."

사용자는 자신의 환경에 맞게 이메일, 언어 등을 수정할 수 있습니다.

---

## STEP 6. (선택) 모바일 에이전트 설치

사용자가 모바일에서도 안티그래비티를 제어하고 싶다면:

```bash
# GitHub에서 클론
git clone https://github.com/caleblee2050/antigravity-mobile-agent.git ~/dev/antigravity-mobile-agent

# 원커맨드 설치
cd ~/dev/antigravity-mobile-agent && bash setup.sh
```

설치 후 필요한 것:
- **Telegram Bot Token**: @BotFather에서 발급 (https://t.me/BotFather)
- **macOS 접근성 권한**: 시스템 설정 > 개인정보 > 접근성
- **macOS 화면 녹화 권한**: 시스템 설정 > 개인정보 > 화면 기록

---

## 설치 완료 확인

모든 단계가 완료되면, 사용자에게 다음 체크리스트를 보여주세요:

- [ ] MCP 서버 연결됨 (안티그래비티 재시작 후)
- [ ] 스킬 70개 설치됨 (`ls ~/.gemini/antigravity/skills/ | wc -l`)
- [ ] 워크플로우 2개 설치됨
- [ ] 브라우저 허용 목록 설정됨
- [ ] (선택) 유저 규칙 설정됨
- [ ] (선택) 모바일 에이전트 설치됨

🎉 **축하합니다! 안티그래비티 파워 유저 세팅이 완료되었습니다!**
