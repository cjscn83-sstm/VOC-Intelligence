# VOC 인텔리전스 — 이동용 패키지 (Portable)

USB로 다른 PC에 복사해서 Claude Code로 그대로 사용하는 자립형 폴더입니다.
`.claude/` 안에 에이전트·스킬이 **표준 위치**로 들어 있어, 이 폴더를 열면 Claude Code가 자동 인식합니다.

## 폴더 구조
```
VOC-Intelligence-Portable/
├── README.md
├── .claude/
│   ├── agents/                       # 서브에이전트 4종 (프로젝트 스코프)
│   │   ├── voc-orchestrator.md       # 오케스트레이션(총괄 조율)
│   │   ├── voc-current-state.md      # 현황분석
│   │   ├── voc-web-research.md       # 웹 리서치
│   │   └── voc-improvement.md        # 개선제안
│   └── skills/                       # 스킬 4종 (폴더별 SKILL.md)
│       ├── voc-orchestration/SKILL.md
│       ├── voc-current-state-analysis/SKILL.md
│       ├── voc-web-research/SKILL.md
│       └── voc-improvement-proposal/SKILL.md
├── data/
│   └── 25년 VOC원문.xlsx             # 원본 VOC 데이터(788건)
└── report/
    ├── index.html                    # 완성 대시보드 보고서
    ├── VOC_인텔리전스_보고서.html    # 동일본(원본 파일명)
    └── VOC_분석_방법론.html          # v2 방법론(귀책 분류 + 워크플로우 매핑) 참조 문서
```

## v2 업데이트 (귀책 분류 + 워크플로우 매핑)
- **현황분석 에이전트** — VOC마다 **귀책(책임 소재)**을 판정: `C` 고객 억지 / `A` 상담사 응대 / `P` 회사·프로세스 / `X` 복합·불명. 접수 유형이 아니라 근본 원인으로 분류하고 원문 근거를 남깁니다.
- **개선제안 에이전트** — 귀책별로 **4대 워크플로우**를 선택: `C→분기` / `A→순환` / `P→순차` / `X·피크→병렬`. 선택 근거를 내부 집계 + 외부 출처(*Workflow Patterns* by van der Aalst, Bain NPS 등)로 명시합니다.
- 사람이 보기 쉬운 요약은 `report/VOC_분석_방법론.html`에서 확인하세요.

## 다른 PC에서 사용하는 법
1. 이 `VOC-Intelligence-Portable` 폴더 **전체**를 USB에 복사 → 대상 PC로 옮깁니다.
   - ⚠️ 숨김 폴더인 `.claude`가 반드시 함께 복사돼야 합니다. (탐색기에서 "숨긴 항목 표시" 켜기)
2. 대상 PC에서 이 폴더를 작업 디렉터리로 Claude Code를 실행합니다.
   ```
   cd VOC-Intelligence-Portable
   claude
   ```
3. 확인:
   - 에이전트 → `/agents` 입력 시 voc-orchestrator 등 4종이 보임
   - 스킬 → 관련 요청 시 voc-* 스킬이 자동 매칭됨
4. 사용 예:
   - "data 폴더의 VOC 원문으로 현황분석부터 다시 돌려줘"
   - voc-orchestrator에게 전체 파이프라인(현황분석→웹리서치→개선제안→종합)을 맡김

## 참고
- 에이전트/스킬 식별자는 Claude Code 호환을 위해 ASCII 슬러그(voc-*)를 사용하고, 표시·내용은 한글입니다.
- 전역(모든 프로젝트)에서 쓰려면 `.claude/agents/*`와 `.claude/skills/*`를 대상 PC의 `~/.claude/agents/`, `~/.claude/skills/`로 복사하세요. (프로젝트 스코프면 이 폴더에서 열 때만 활성화)
- 원본 데이터는 `data/`, 완성 보고서는 `report/`에 있습니다.
