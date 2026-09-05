# Claude Code 개발 스킬 묶음

아이디어를 통과하는 테스트까지 끌고 가는 스킬 5개.

| 스킬 | 부르는 법 | 하는 일 |
| --- | --- | --- |
| [set-goal](set-goal/SKILL.md) | `/set-goal <주제>` | 막연한 아이디어 → 측정 가능한 목표, 성공 기준, 비목표, DoD |
| [interview](interview/SKILL.md) | `/interview <주제>` | 한 번에 한 질문씩 요구사항 캐내기 (discover 모드) |
| [interview](interview/SKILL.md) | `/interview grill` · `grill me` | 계획을 5축으로 적대적 심문 — 허점 먼저 찾기 (grill 모드) |
| [spec](spec/SKILL.md) | `/spec <기능>` | 명세서 한 장 쓰기 (무엇을·왜만, 구현 방법 금지) |
| [spec](spec/SKILL.md) | `/spec review <파일>` | 기존 명세를 10개 항목으로 점검 |
| [sdd](sdd/SKILL.md) | `/sdd <기능>` | 명세 우선 개발: spec.md → plan.md → tasks.md → 구현 |
| [tdd](tdd/SKILL.md) | `/tdd <대상>` | RED → GREEN → REFACTOR 강제 |
| [dev-loop](dev-loop/SKILL.md) | `/dev-loop <슬러그>` | 위 넷을 게이트로 묶은 전체 파이프라인 |

## 어떤 걸 언제 쓰나

```
뭘 만들지 모르겠다            → /set-goal
만들 건 알겠는데 상세가 흐리다  → /interview
계획은 섰는데 자신이 없다      → /interview grill
요구사항을 문서로 남겨야 한다   → /spec
남이 쓴 명세가 미덥지 않다     → /spec review
무엇을 만들지 분명하다         → /sdd
지금 이 함수를 짜야 한다       → /tdd
처음부터 끝까지 제대로         → /dev-loop
```

`spec` 과 `sdd` 는 겹쳐 보이지만 범위가 다르다.
`spec` 은 **명세 문서 한 장**에서 끝나고, `sdd` 는 **명세 → 계획 → 작업 → 구현** 전체를 게이트로 묶는다.
문서만 필요하면 `/spec`, 끝까지 갈 거면 `/sdd`.

작은 일(오타 수정, 한 줄 변경)에는 쓰지 않는다. `/dev-loop` 는 특히 과하다.

## grill 모드에 대해

`grill me` 는 **계획을 공격해서 약한 곳을 미리 찾는** 모드다. 사람이 아니라 아이디어를 친다.

- 시작 전에 동의를 받는다
- 5축(근거 · 범위 · 실패 · 대안 · 검증)으로 축마다 최대 2발
- "모르겠다"는 정당한 답 — 기록하고 넘어간다
- "그만"이라고 하면 즉시 멈추고 정리한다

## 설치

이 저장소 안에서는 이미 동작한다 (`.claude/skills/` 에 있음).

다른 프로젝트에서도 쓰려면 사용자 전역 폴더로 복사한다.

Windows (PowerShell):

```bash
Copy-Item -Recurse -Force .\.claude\skills\* "$env:USERPROFILE\.claude\skills\"
```

macOS / Linux:

```bash
cp -R ./.claude/skills/* ~/.claude/skills/
```

복사 후 `/set-goal`, `/interview`, `/spec`, `/sdd`, `/tdd`, `/dev-loop` 를 어디서든 쓸 수 있다.
(스킬은 폴더를 열 때 로드된다. 이미 그 폴더에서 세션이 열려 있었다면 새 세션을 시작한다.)

## 이름 규칙 주의

스킬 이름이 Claude Code 내장 명령어와 겹치면 **조용히 등록되지 않는다.**
`goal` 이 그래서 `set-goal` 이 됐다. 새 스킬을 추가한 뒤에는 목록에 실제로 떴는지 확인할 것.

확인된 충돌: `goal`, `plan`, `tasks` — 전부 내장 명령어라 스킬 이름으로 못 쓴다.

## 구조

각 스킬은 `SKILL.md` 하나로 끝난다. YAML 프론트매터의 `description` 이 언제 이 스킬이 켜질지를 결정하므로,
동작을 바꾸고 싶으면 본문을, 켜지는 조건을 바꾸고 싶으면 `description` 을 고친다.

```
.claude/skills/
├── set-goal/SKILL.md
├── interview/SKILL.md
├── spec/SKILL.md
├── sdd/SKILL.md
├── tdd/SKILL.md
└── dev-loop/SKILL.md
```
