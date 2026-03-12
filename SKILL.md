---
name: antigravity-setup-kit
description: "안티그래비티 파워 유저 세팅 원클릭 설치. '안티그래비티 세팅해줘'라고 요청하면 MCP 서버 7개, 스킬 70개, 워크플로우, 브라우저 허용 목록까지 자동 구성. macOS/Windows 모두 지원."
---

# 안티그래비티 파워 유저 세팅 원클릭 설치

이 스킬은 안티그래비티를 **최강의 AI 코딩 에이전트**로 만들어주는 전체 세팅 패키지입니다.
**"안티그래비티 세팅해줘"** 또는 **"이 스킬 실행해줘"**라고 요청받으면 아래 6단계를 실행하세요.

> **중요**: API 키 등 민감 정보는 반드시 사용자에게 물어보세요.

---

## ⚙️ OS 감지 (최우선 실행)

설치 시작 전 **반드시 현재 OS를 확인**하고 아래 표에 맞게 경로/명령어를 자동 변환하세요:

| | macOS / Linux | Windows |
|---|---|---|
| **설정 경로** | `~/.gemini/antigravity/` | `%USERPROFILE%\.gemini\antigravity\` |
| **파일 복사** | `cp` | `Copy-Item` (PowerShell) |
| **디렉토리 생성** | `mkdir -p` | `New-Item -ItemType Directory -Force` |
| **파일 목록** | `ls ... \| wc -l` | `(Get-ChildItem ...).Count` |
| **모바일 에이전트** | ✅ 지원 | ❌ macOS 전용 |

---

## STEP 1. MCP 서버 설정

### 1-1. 이 스킬의 `config/mcp_config_template.json`을 읽으세요.

### 1-2. 사용자에게 API 키 요청

| 서비스 | 필요한 키 | 발급 |
|--------|-----------|------|
| **GitHub** | PAT | github.com/settings/tokens |
| **Notion** | Integration Token | notion.so/my-integrations |
| **Airtable** | API Key | airtable.com/account |
| **Google Workspace** | OAuth Client ID/Secret | Cloud Console > Credentials |
| **Google Dev Knowledge** | API Key | Cloud Console > Dev Knowledge API |
| Slack (선택) | Bot Token + Team ID | api.slack.com |

### 1-3. mcp_config.json 생성
- `<PLACEHOLDER>`를 사용자 키로 교체
- 키 없는 서비스는 해당 블록 제거
- **memory 서버**는 키 불필요 → 항상 포함
- 저장 경로: OS별 안티그래비티 설정 디렉토리의 `mcp_config.json`

> ⚠️ `google_workspace`의 `gws` CLI는 별도 설치 필요 (Go 바이너리, macOS/Windows 모두 지원)

### 1-4. 안티그래비티 재시작 안내

---

## STEP 2. 스킬 70개 일괄 설치

`config/skills_manifest.json`을 읽고 설치. `npx skills add` 명령은 **OS 무관** 동일 작동.

### 2-1. 문서/디자인 (12개)
```bash
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

### 2-2. 개발 워크플로우 (23개)
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

### 2-3. 에이전트 아키텍처 (15개)
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

### 2-4. 전문 기술 (20개)
```bash
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
npx skills add vercel-labs/agent-skills@vercel-deployment -g -y
npx skills add vercel-labs/agent-skills@vercel-react-best-practices -g -y
npx skills add vercel-labs/agent-skills@web-design-guidelines -g -y
npx skills add obsidianmd/obsidian-skills@obsidian-markdown -g -y
npx skills add obsidianmd/obsidian-skills@obsidian-bases -g -y
npx skills add remotion-dev/agent-skills@remotion-best-practices -g -y
```

> **💡**: 이미 존재하는 스킬은 자동 건너뜁니다. 5~10개씩 묶어서 실행 권장.

---

## STEP 3. 워크플로우 설치

**macOS / Linux:**
```bash
mkdir -p ~/.gemini/antigravity/.agent/workflows/
cp workflows/*.md ~/.gemini/antigravity/.agent/workflows/
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.gemini\antigravity\.agent\workflows"
Copy-Item workflows\*.md "$env:USERPROFILE\.gemini\antigravity\.agent\workflows\"
```

---

## STEP 4. 브라우저 허용 목록

**macOS / Linux:**
```bash
cp config/browser_allowlist.txt ~/.gemini/antigravity/browserAllowlist.txt
```

**Windows (PowerShell):**
```powershell
Copy-Item config\browser_allowlist.txt "$env:USERPROFILE\.gemini\antigravity\browserAllowlist.txt"
```

---

## STEP 5. 유저 규칙 (수동)

`config/user_rules_template.md`를 읽고 사용자에게 안내:
> "안티그래비티 설정 > User Rules에 복사해서 붙여넣으세요."

---

## STEP 6. (선택) 모바일 에이전트 — ⚠️ macOS 전용

> **Windows 사용자**: 이 단계는 건너뛰세요. AppleScript/macOS 접근성 API 기반으로 **Windows에서 사용 불가**합니다.

```bash
git clone https://github.com/caleblee2050/antigravity-mobile-agent.git ~/dev/antigravity-mobile-agent
cd ~/dev/antigravity-mobile-agent && bash setup.sh
```

필요: Telegram Bot Token, macOS 접근성/화면녹화 권한

---

## 설치 완료 확인

**macOS / Linux:**
- [ ] MCP 서버 연결됨
- [ ] 스킬 설치됨 (`ls ~/.gemini/antigravity/skills/ | wc -l`)
- [ ] 워크플로우 설치됨
- [ ] 브라우저 허용 목록 설정됨

**Windows:**
- [ ] MCP 서버 연결됨
- [ ] 스킬 설치됨 (`(Get-ChildItem $env:USERPROFILE\.gemini\antigravity\skills).Count`)
- [ ] 워크플로우 설치됨
- [ ] 브라우저 허용 목록 설정됨

🎉 **축하합니다! 안티그래비티 파워 유저 세팅이 완료되었습니다!**
