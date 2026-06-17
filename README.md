# LLMwiki

> PM 업무에 Claude Code를 "도구"가 아니라 **"같은 맥락을 아는 협업자"** 로 쓰는 패턴.
> 클론해서 채우는 고정 템플릿이 아니라, **경로만 주면 자라나는 위키**다.

📖 **실습 가이드**: https://jennyby-ops.github.io/llmwiki-template/

---

## 한 줄 요약

`CLAUDE.md`에 **초기화 규칙 + 누적 규칙**을 적어두면, 사람은 **경로와 소스(Confluence 링크 등)만** 던지고
구조 생성·문서화·이력 관리는 Claude Code가 매 세션 동일하게 처리한다.

## 어떻게 쓰나 (클론 불필요)

**① 초기화 — 한 번만.** 경로만 주면 기초 트리를 만든다. (업무/팀 입력 불필요 — 위키는 여러 프로젝트를 담는 그릇)
```
내 LLM wiki를 여기에 만들어줘: ~/work/my-wiki
아래 공유용 CLAUDE.md 레시피를 읽고, 로컬용 CLAUDE.md와 기초 트리를 생성해줘.
https://jennyby-ops.github.io/llmwiki-template/CLAUDE.md
```

**② 누적 — 반복.** 소스만 던지면 쌓인다. (6섹션·다이어그램·이력 갱신은 CLAUDE.md가 자동 처리 — 매번 지시 불필요)
```
이 소스 wiki화해줘: https://wiki.../pages/123456
```

**③ 조회.** 쌓인 프로젝트를 나열하고 골라 본다.
```
프로젝트 목록 보여줘
```

**④ 다음 세션부터.** 로컬 CLAUDE.md가 자동으로 읽혀, 규칙을 다시 말할 필요가 없다.

## 3레이어

```
raw/        ← 원본 자료 (읽기 전용)
wiki/       ← Claude가 구조화해 관리 (진실의 원본)
{공유처}     ← Confluence / Notion 등 팀 공유 (선택)
```

## 폴더 구조

```
llmwiki/
├── CLAUDE.md          ← 초기화·누적 규칙 = AI 작동 설명서 (핵심)
├── raw/               ← 원본 자료 (읽기 전용)
├── wiki/
│   ├── index.md           ← 전체 카탈로그
│   ├── log.md             ← 작업 이력
│   ├── cross_issues.md    ← 프로젝트 간 걸친 미결사항
│   └── {프로젝트명}/      ← 프로젝트 템플릿 예시. 실제 프로젝트는 "누적" 때 자동 생성됨
│       ├── overview.md   ← 6섹션 요약
│       ├── issues.md     ── 미결사항
│       ├── meetings.md   ── 회의 이력 (append only)
│       └── flows.md      ── Mermaid 다이어그램
└── docs/              ← GitHub Pages 실습 가이드
```

## 왜 작동하는가

- **사람은 경로·소스만** → 구조/포맷/이력은 규칙대로 AI가 → 매 세션 동일 퀄리티
- **raw/ 읽기 전용** → 원본 훼손 없이 출처 추적
- **index.md + log.md 강제 갱신** → 변경 이력이 항상 남음
- **버전업 누락 체크 규칙** → 추상화하다 디테일 잃는 사고 방지

> 이 레포 자체는 가이드 호스팅용 + 참고용이다. 실습은 클론 없이 위 프롬프트만으로 가능하다.

---

made by jenny.by · 물류플랫폼팀 AI 스터디
