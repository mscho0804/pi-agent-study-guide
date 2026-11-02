# ⬛ Pi Coding Agent 실전 스터디 핸드북

회사에서 **Pi (`@earendil-works/pi-coding-agent`, `pi.dev`)** 에이전트의 내부 동작 원리와 확장 시스템(Extension, Skill, Tool, Command), 병렬 워크플로우(`git worktree`), 그리고 LLM JSON 스트리밍 및 프롬프트 캐싱 경제학을 학습하기 위한 인터랙티브 HTML 가이드 모음입니다.

---

## 📂 포함된 파일 목록

1. **[`index.html`](./index.html)** — 전체 가이드를 한눈에 오갈 수 있는 통합 대시보드 목차
2. **[`pi_agent_guide.html`](./pi_agent_guide.html)** — **Part 1: Pi 코딩 에이전트 완벽 가이드**
   - Pi의 4계층 아키텍처 (`pi-ai`, `pi-agent-core`, `pi-tui`, `pi-coding-agent`)
   - 5단계 에이전트 루프 & 세션 트리(`~/.pi/agent/sessions/*.jsonl`)
   - `/tree` 컨텍스트 분기와 파일시스템(Working Directory)의 독립성
   - `AGENTS.md` (Context) vs `SKILL.md` (Skill) vs `.ts` (Extension)
   - **`pi.registerTool` vs `SKILL.md` vs `pi.registerCommand` 심층 비교** (실행 주체, Request JSON 포함 위치, 토큰 비용)
3. **[`git_worktree_guide.html`](./git_worktree_guide.html)** — **Part 2: Git Worktree + Pi 병렬 개발 입문 가이드**
   - `git stash` / `git checkout` 없이 여러 기능/핫픽스를 동시에 AI에게 맡기는 원리
   - 실전 명령어 3종 (`git worktree add`, `list`, `remove`) 및 `pi-wt` 자동화 함수
4. **[`llm_json_and_cache_guide.html`](./llm_json_and_cache_guide.html)** — **Part 3: LLM JSON 스트리밍 & 프롬프트 캐싱 심화 가이드**
   - Request JSON 내부 구조 (`system`, `messages`, `tools`, 그리고 Claude/OpenAI/Gemini의 `thinking` 옵션 차이)
   - SSE(Server-Sent Events) 실시간 스트리밍 청크 시뮬레이터
   - 무상태(Stateless) 블랙박스로서의 LLM과 `/model` 핫스왑 원리
   - 매 턴 히스토리 중복 전송과 **Prefix KV Caching (90% 할인)**
   - **잦은 `/compact`가 오히려 비용을 증가시키는 이유(Cache Busting)**와 **5분 캐시 수명(TTL) 카운트다운 익스텐션 코드**

---

## 🚀 회사 PC에서 보는 방법

```bash
git clone https://github.com/mscho0804/pi-agent-study-guide.git
cd pi-agent-study-guide
```

클론한 폴더에서 **`index.html`** 파일을 크롬(Chrome)이나 엣지(Edge) 브라우저로 더블클릭해 열면 모든 인터랙티브 탭과 시뮬레이터, 다크/라이트 테마 전환이 바로 동작합니다.
