# Claude Code 개발 스킬 묶음

아이디어를 통과하는 테스트까지 끌고 가는 스킬 5개.

| 스킬 | 부르는 법 | 하는 일 |
| --- | --- | --- |
| [goal](goal/SKILL.md) | `/goal <주제>` | 막연한 아이디어 → 측정 가능한 목표, 성공 기준, 비목표, DoD |
| [interview](interview/SKILL.md) | `/interview <주제>` | 한 번에 한 질문씩 요구사항 캐내기 (discover 모드) |
| [interview](interview/SKILL.md) | `/interview grill` · `grill me` | 계획을 5축으로 적대적 심문 — 허점 먼저 찾기 (grill 모드) |
| [sdd](sdd/SKILL.md) | `/sdd <기능>` | 명세 우선 개발: spec.md → plan.md → tasks.md → 구현 |
| [tdd](tdd/SKILL.md) | `/tdd <대상>` | RED → GREEN → REFACTOR 강제 |
| [dev-loop](dev-loop/SKILL.md) | `/dev-loop <슬러그>` | 위 넷을 게이트로 묶은 전체 파이프라인 |

## 어떤 걸 언제 쓰나

```
뭘 만들지 모르겠다            → /goal
만들 건 알겠는데 상세가 흐리다  → /interview
계획은 섰는데 자신이 없다      → /interview grill
무엇을 만들지 분명하다         → /sdd
지금 이 함수를 짜야 한다       → /tdd
처음부터 끝까지 제대로         → /dev-loop
```

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

복사 후 Claude Code 를 재시작하면 `/goal`, `/interview`, `/sdd`, `/tdd`, `/dev-loop` 를 어디서든 쓸 수 있다.

## 구조

각 스킬은 `SKILL.md` 하나로 끝난다. YAML 프론트매터의 `description` 이 언제 이 스킬이 켜질지를 결정하므로,
동작을 바꾸고 싶으면 본문을, 켜지는 조건을 바꾸고 싶으면 `description` 을 고친다.

```
.claude/skills/
├── goal/SKILL.md
├── interview/SKILL.md
├── sdd/SKILL.md
├── tdd/SKILL.md
└── dev-loop/SKILL.md
```
