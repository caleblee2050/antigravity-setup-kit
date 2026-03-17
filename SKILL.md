---
name: antigravity-setup-kit
description: "안티그래비티 파워 유저 세팅 원클릭 설치. '안티그래비티 세팅해줘'라고 요청하면 MCP 서버, 스킬 75개, 워크플로우, 브라우저 허용 목록, 모바일 에이전트까지 자동 구성. macOS/Windows 모두 지원."
---

# 안티그래비티 파워 유저 세팅 원클릭 설치

이 스킬은 안티그래비티를 **최강의 AI 코딩 에이전트**로 만들어주는 전체 세팅 패키지입니다.
**"안티그래비티 세팅해줘"** 또는 **"이 스킬 실행해줘"**라고 요청받으면 아래 8단계를 실행하세요.

> **중요**: 각 단계에서 사용자에게 설치 여부를 확인하세요. 안티그래비티가 CLI를 통해 직접 설정합니다.

---

## ⚙️ OS 감지 (최우선 실행)

설치 시작 전 **반드시 현재 OS를 확인**하고 아래 표에 맞게 경로/명령어를 자동 변환하세요:

| | macOS / Linux | Windows |
|---|---|---|
| **설정 경로** | `~/.gemini/antigravity/` | `%USERPROFILE%\.gemini\antigravity\` |
| **파일 복사** | `cp` | `Copy-Item` (PowerShell) |
| **디렉토리 생성** | `mkdir -p` | `New-Item -ItemType Directory -Force` |
| **파일 목록** | `ls ... \| wc -l` | `(Get-ChildItem ...).Count` |
| **모바일 에이전트** | ✅ 지원 | ✅ 지원 (Task Scheduler + pygetwindow) |

---

## STEP 1. MCP 서버 설정

안티그래비티가 직접 `mcp_config.json`을 조립합니다. 사용자가 파일을 직접 편집할 필요 없습니다.

### 1-1. 필수 설치 (자동 — 질문 없이 바로 진행)

| 서비스 | 설치 명령 | 키 필요 |
|--------|----------|---------|
| **memory** | npx 기반 | ❌ |
| **gws CLI** | `npm i -g @anthropic/gws` | ❌ (이후 OAuth 연동 필요) |

```bash
# gws CLI 필수 설치
npm i -g @anthropic/gws
```

설치 후 `gws --version`으로 확인. `google_workspace` MCP는 gws 설치 후 자동 구성됩니다.

> **gws OAuth 연동**: `gws auth login`으로 Google OAuth 인증을 진행합니다. 이 과정은 브라우저가 자동으로 열리므로 사용자가 Google 계정으로 로그인만 하면 됩니다.

### 1-2. 선택 설치 (사용자에게 개별 질문)

아래 각 서비스마다 **하나씩** 설치 여부를 질문하세요:

| 질문 | 필요한 키 | 발급 방법 |
|------|-----------|----------|
| "**GitHub** MCP를 설치할까요?" | PAT | github.com/settings/tokens |
| "**Notion** MCP를 설치할까요?" | Integration Token | notion.so/my-integrations |
| "**Airtable** MCP를 설치할까요?" | API Key | airtable.com/account |
| "**Slack** MCP를 설치할까요?" | Bot Token + Team ID | api.slack.com |
| "**Google Dev Knowledge** MCP를 설치할까요?" | API Key | Cloud Console |

→ **Y 선택 시**: 키를 입력받고 mcp_config.json에 해당 블록 추가
→ **N 선택 시**: 해당 서비스 건너뜀

### 1-3. mcp_config.json 자동 생성

안티그래비티가 직접 JSON을 조립하여 저장합니다:
- `config/mcp_config_template.json`을 기반으로 선택된 서비스만 포함
- `<PLACEHOLDER>`를 사용자가 입력한 키로 교체
- 저장 경로: `~/.gemini/antigravity/mcp_config.json`

### 1-4. 안티그래비티 재시작 안내

---

## STEP 2. 스킬 75개 일괄 설치

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

### 2-4. 전문 기술 (19개)
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
```

### 2-5. 마케팅 & 자동화 (6개)
```bash
npx skills add jamditis/claude-skills-journalism@web-scraping -g -y
npx skills add inferen-sh/skills@ai-social-media-content -g -y
npx skills add anthropics/knowledge-work-plugins@data-visualization -g -y
npx skills add inferen-sh/skills@email-design -g -y
npx skills add kostja94/marketing-skills@email-marketing -g -y
npx skills add claude-dev-suite/claude-dev-suite@cron-scheduling -g -y
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

## STEP 6. (선택) 모바일 에이전트 — macOS / Windows 지원

> **설치 전 질문**: "모바일 에이전트(텔레그램 봇)를 설치할까요?"
> → **N 선택 시**: 이 단계를 건너뛰고 STEP 7로.

### 6-1. 설치

**가장 쉬운 방법 (한 줄 설치):**

macOS / Linux:
```bash
curl -sL a4k.ai/setup | bash
```

Windows (PowerShell):
```powershell
irm a4k.ai/setup.ps1 | iex
```

**수동 설치:**

macOS / Linux:
```bash
git clone https://github.com/caleblee2050/antigravity-agent.git ~/dev/antigravity-agent
cd ~/dev/antigravity-agent && bash setup/setup.sh
```

Windows (PowerShell):
```powershell
git clone https://github.com/caleblee2050/antigravity-agent.git "$env:USERPROFILE\dev\antigravity-agent"
cd "$env:USERPROFILE\dev\antigravity-agent"
powershell -ExecutionPolicy Bypass -File setup\setup.ps1
```

### 6-2. 텔레그램 봇 설정 (기본 인터페이스)

사용자에게 아래 단계를 안내합니다:

| 단계 | 설명 |
|------|------|
| 1 | 텔레그램에서 **@BotFather** 검색 후 `/newbot` 입력 |
| 2 | 봇 이름과 유저네임 입력 (예: `my_antigravity_bot`) |
| 3 | 발급받은 **API 토큰** 복사 |
| 4 | 봇에게 아무 메시지 보낸 후, `https://api.telegram.org/bot<토큰>/getUpdates` 에서 **Chat ID** 확인 |
| 5 | `.env`에 `TELEGRAM_TOKEN`과 `TELEGRAM_CHAT_ID` 입력 |

### 6-3. 호칭 설정

텔레그램 봇과 첫 대화 시 자동으로 호칭 설정 대화가 시작됩니다:
- "제가 당신을 어떻게 불러드릴까요?" → 사용자 호칭 저장
- "저를 뭐라고 불러주실 건가요?" → 에이전트 호칭 저장
- 이후 모든 대화에서 설정된 호칭을 사용합니다.
- 설정은 `agent_config.json`에 저장됩니다.

### 6-4. 음성 인식(STT) — 자동 활성화

텔레그램 음성 메시지를 텍스트로 자동 변환합니다.
**Whisper** 로컬 모델을 사용하며, API 키가 필요 없습니다 (완전 무료).

`.env` 파일:
```ini
ENABLE_STT=true   # 기본값 — 추가 설정 불필요
```

> 첫 실행 시 모델(~74MB)이 자동 다운로드됩니다.

### 6-5. 카카오톡 연동 (선택 — 한국 사용자 권장)

> **설치 전 질문**: "카카오톡 메시지 연동을 설정할까요?"
> → **N 선택 시**: 이 단계를 건너뛰고 STEP 7로.

1. [Kakao Developers](https://developers.kakao.com/)에서 앱 생성
2. **카카오 로그인** 활성화
3. **앱** → **플랫폼 키** → REST API 키에서 **Redirect URI** 등록: `http://localhost:9250/oauth`
4. **동의항목**에서 `talk_message`(카카오톡 메시지 전송), `friends`(친구목록) 권한 활성화
5. `.env` 파일 설정:
   ```ini
   KAKAO_REST_API_KEY=발급받은_REST_API_키
   KAKAO_CLIENT_SECRET=클라이언트_시크릿
   KAKAO_REDIRECT_URI=http://localhost:9250/oauth
   ```
6. OAuth 인증:
   ```bash
   python kakao_api.py auth
   ```
7. 테스트:
   ```bash
   python kakao_api.py send "카카오톡 연동 테스트!"
   ```

필요 권한:
- **macOS**: 접근성/화면녹화 권한
- **Windows**: 관리자 권한 (Task Scheduler 등록 시)

---

## STEP 7. 에이전트 워크스페이스 시스템

모바일에서 지시가 들어오면 작업할 전용 폴더를 생성하고, 멀티 창 자동 타겟팅을 설정합니다.

### 7-1. 에이전트 전용 폴더 생성

**macOS / Linux:**
```bash
mkdir -p ~/.gemini/antigravity/anti-agent
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.gemini\antigravity\anti-agent"
```

### 7-2. 에이전트 폴더 경로 설정

사용자에게 에이전트 폴더 경로를 확인합니다:
> "에이전트 전용 폴더를 `~/.gemini/antigravity/anti-agent`로 설정할까요? 다른 경로를 원하시면 알려주세요."

`agent_config.json`의 `workspace.agent_folder`에 경로를 저장합니다:
```json
{
  "workspace": {
    "agent_folder": "~/.gemini/antigravity/anti-agent",
    "target_window_index": null
  }
}
```

### 7-3. `/에이전트` 워크플로우 설치

안티그래비티에서 `/에이전트` 라고 입력하면 에이전트 폴더를 새 창으로 자동 오픈합니다.

**macOS / Linux:**
```bash
mkdir -p ~/.gemini/antigravity/.agents/workflows/
```

다음 내용으로 `에이전트.md` 워크플로우를 생성합니다:
```markdown
---
description: 에이전트 전용 폴더로 새 안티그래비티 창 열기
---
// turbo-all
1. 에이전트 폴더 생성: `mkdir -p ~/.gemini/antigravity/anti-agent`
2. 새 창으로 열기: `antigravity --new-window ~/.gemini/antigravity/anti-agent`
```

### 7-4. 멀티 창 관리 (텔레그램 명령어)

모바일 에이전트 설치 시, 다음 텔레그램 명령어가 자동 제공됩니다:

| 명령어 | 설명 |
|--------|------|
| `/windows` | 열린 안티그래비티 창 목록 + 현재 타겟 표시 |
| `/target 2` | 2번 창으로 타겟 변경 |
| `/target auto` | 자동 탐색 모드 (에이전트 폴더명 매칭) |

> **자동 타겟팅**: 텔레그램 메시지 전송 시, 창 제목에 에이전트 폴더명(`anti-agent`)이 포함된 창을 자동으로 찾아 입력합니다.

---

## STEP 8. 설치 완료 확인

**macOS / Linux:**
- [ ] MCP 서버 연결됨 (필수: memory, gws)
- [ ] 스킬 설치됨 (`ls ~/.gemini/antigravity/skills/ | wc -l`)
- [ ] 워크플로우 설치됨
- [ ] 브라우저 허용 목록 설정됨
- [ ] (선택) 모바일 에이전트 텔레그램 연결됨
- [ ] (선택) anti-agent 워크스페이스 생성됨

**Windows:**
- [ ] MCP 서버 연결됨 (필수: memory, gws)
- [ ] 스킬 설치됨 (`(Get-ChildItem $env:USERPROFILE\.gemini\antigravity\skills).Count`)
- [ ] 워크플로우 설치됨
- [ ] 브라우저 허용 목록 설정됨

🎉 **축하합니다! 안티그래비티 파워 유저 세팅이 완료되었습니다!**
