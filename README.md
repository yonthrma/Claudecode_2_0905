# Claudecode_2_0905

목포해양대학교 AI 교육 — 1차 AI 리터러시(9월 4~5일) 과정의 Claude Code 실습 저장소입니다.

## 무엇을 하는 저장소인가

Claude Code를 사용해 진행한 실습 결과물을 모아둡니다. 작업한 내용은 로컬 폴더에서
바로 이 저장소로 자동 반영됩니다.

## 자동 동기화

이 저장소는 수동으로 커밋·푸시하지 않아도 되도록 설정되어 있습니다.

| 시점 | 동작 |
| --- | --- |
| Claude Code 작업 종료 시 | 변경분 자동 커밋 후 업로드 |
| 10분마다 | 변경분 자동 커밋 후 업로드 |
| 변경사항이 없을 때 | 아무 동작도 하지 않음 |

폴더 안의 `.autosync` 파일이 자동 동기화 대상임을 표시합니다. 이 파일을 지우면
자동 반영이 멈춥니다.

## 개발 스킬 묶음

`.claude/skills/` 에 프로젝트 진행용 스킬 5개가 들어 있습니다. 이 저장소 안에서는 바로 쓸 수 있고,
다른 프로젝트로 복사하는 방법은 [.claude/skills/README.md](.claude/skills/README.md) 에 있습니다.

| 스킬 | 부르는 법 | 하는 일 |
| --- | --- | --- |
| set-goal | `/set-goal <주제>` | 막연한 아이디어를 측정 가능한 목표로 |
| interview | `/interview <주제>` | 한 번에 한 질문씩 요구사항 캐내기 |
| interview (grill) | `/interview grill`, `grill me` | 계획을 5축으로 심문해 허점 찾기 |
| spec | `/spec <기능>` · `/spec review <파일>` | 명세서 한 장 쓰기 / 기존 명세 점검 |
| sdd | `/sdd <기능>` | 명세 우선 개발 (spec → plan → tasks → 구현) |
| tdd | `/tdd <대상>` | RED → GREEN → REFACTOR 강제 |
| dev-loop | `/dev-loop <슬러그>` | 위 넷을 게이트로 묶은 전체 파이프라인 |

## 폴더 구조

```
Claudecode_2_0905/
├── README.md          이 문서
├── .gitignore         업로드에서 제외할 파일 목록
├── .autosync          자동 동기화 대상 표시
└── .claude/skills/    개발 스킬 묶음
    ├── README.md
    ├── set-goal/SKILL.md
    ├── interview/SKILL.md
    ├── spec/SKILL.md
    ├── sdd/SKILL.md
    ├── tdd/SKILL.md
    └── dev-loop/SKILL.md
```

## 참고

`.env`, `*.key`, `credentials.json` 등 비밀번호나 API 키가 담기는 파일은
`.gitignore`에 등록되어 있어 공개 저장소에 올라가지 않습니다.
