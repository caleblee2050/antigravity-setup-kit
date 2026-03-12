# 🚀 Antigravity Setup Kit

**안티그래비티 파워 유저 세팅 원클릭 설치 패키지**

다른 컴퓨터에 설치된 안티그래비티에서 이 패키지 하나로 동일한 환경을 구성할 수 있습니다.
**macOS, Windows 모두 지원합니다.**

---

## 📦 패키지에 포함된 것

| 구성 요소 | 수량 | 설명 |
|-----------|------|------|
| MCP 서버 템플릿 | 7개 | GitHub, Notion, Airtable, Google 등 |
| 스킬(Skills) | 70개 | 문서, 디자인, 개발, 에이전트, 전문 기술 |
| 워크플로우 | 2개 | 스킬 검색/관리 자동화 |
| 브라우저 허용 목록 | 82개 도메인 | 개발에 필요한 웹사이트 |
| 유저 규칙 템플릿 | 1개 | 추천 설정 가이드 |
| 모바일 에이전트 | 선택 | Telegram으로 원격 제어 (macOS 전용) |

---

## 🖥️ 지원 OS

| 기능 | macOS | Windows |
|------|-------|---------|
| MCP 서버 설정 | ✅ | ✅ |
| 스킬 설치 | ✅ | ✅ |
| 워크플로우 | ✅ | ✅ |
| 브라우저 허용 목록 | ✅ | ✅ |
| 유저 규칙 | ✅ | ✅ |
| 모바일 에이전트 | ✅ | ❌ (macOS 전용) |

---

## 🎯 설치 방법 (초보자용)

### 방법 1: Skills CLI로 설치 (추천)

```bash
npx skills add caleblee2050/antigravity-setup-kit -g -y
```

설치 후 안티그래비티에게:

> **"안티그래비티 세팅해줘"** 또는 **"antigravity-setup-kit 스킬 실행해줘"**

### 방법 2: 수동 설치

```bash
# 1. 이 레포를 클론
git clone https://github.com/caleblee2050/antigravity-setup-kit.git

# 2. 스킬 폴더에 복사 (macOS)
cp -r antigravity-setup-kit ~/.gemini/antigravity/skills/antigravity-setup-kit

# 2. 스킬 폴더에 복사 (Windows PowerShell)
# Copy-Item -Recurse antigravity-setup-kit "$env:USERPROFILE\.gemini\antigravity\skills\antigravity-setup-kit"
```

그 다음 안티그래비티에게:

> **"antigravity-setup-kit 스킬 읽고 세팅해줘"**

---

## 📋 설치되는 내용 상세

### MCP 서버 (7개)

| 서비스 | 용도 | API 키 필요 |
|--------|------|-------------|
| GitHub | 코드 관리, PR, 이슈 | ✅ PAT |
| Notion | 문서/워크스페이스 관리 | ✅ Integration Token |
| Airtable | 데이터베이스 관리 | ✅ API Key |
| Google Workspace | Gmail, Drive, Calendar | ✅ OAuth |
| Google Dev Knowledge | 공식 문서 검색 | ✅ API Key |
| Slack | 팀 커뮤니케이션 | ✅ Bot Token |
| Memory | 에이전트 기억 저장 | ❌ 불필요 |

### 스킬 카테고리 (70개)

| 카테고리 | 수량 | 주요 스킬 |
|----------|------|----------|
| 📄 문서/디자인 | 12 | docx, pdf, pptx, xlsx, frontend-design |
| 🔧 개발 워크플로우 | 23 | brainstorming, test-driven-development, code-review |
| 🤖 에이전트 아키텍처 | 15 | context-optimization, multi-agent-patterns |
| 💻 전문 기술 | 13 | security-auditor, docker-expert, typescript-expert |
| ▲ Vercel 배포 | 3 | vercel-deployment, react-best-practices |
| 📝 Obsidian | 2 | obsidian-markdown, obsidian-bases |
| 🎬 비디오 제작 | 2 | remotion-best-practices |

---

## 📱 (선택) 모바일 에이전트 — macOS 전용

> ⚠️ **Windows 미지원**: AppleScript/macOS 접근성 API 기반이므로 macOS에서만 작동합니다.

```bash
git clone https://github.com/caleblee2050/antigravity-mobile-agent.git
cd antigravity-mobile-agent && bash setup.sh
```

---

## 🔧 패키지 구조

```
antigravity-setup-kit/
├── SKILL.md                          # 메인 설치 지침서
├── README.md                         # 이 파일
├── LICENSE
├── config/
│   ├── mcp_config_template.json      # MCP 서버 설정 템플릿
│   ├── skills_manifest.json          # 70개 스킬 목록
│   ├── browser_allowlist.txt         # 브라우저 허용 도메인
│   └── user_rules_template.md        # 추천 유저 규칙
└── workflows/
    ├── find-new-skills.md            # 스킬 검색 워크플로우
    └── skills-management.md          # 스킬 관리 워크플로우
```

---

## ❓ FAQ

**Q. 설치에 얼마나 걸리나요?**
A. MCP 설정 5분 + 스킬 설치 10~15분 정도입니다.

**Q. 기존 설정이 덮어씌워지나요?**
A. 아닙니다. mcp_config.json이 이미 있으면 백업을 먼저 만듭니다.

**Q. Windows에서도 되나요?**
A. 네! 모바일 에이전트를 제외한 모든 기능이 Windows에서 작동합니다.

**Q. API 키는 안전한가요?**
A. 모든 키는 로컬 `mcp_config.json`에만 저장됩니다. 이 패키지에는 키가 포함되지 않습니다.

---

## 📝 라이선스

MIT License

---

*Built with ❤️ by [caleblee2050](https://github.com/caleblee2050) — Powered by Antigravity*
