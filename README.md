# korean-office-skills

한국 사무실의 문서 문화(개조식 보고, 품의서, 공문, 곤란한 메일)에 맞춘 **무료 Claude 스킬 모음**입니다.
회의 메모를 붙여 넣으면 할 일 표가, 정리 안 된 메모를 붙여 넣으면 개조식 보고서나 품의서 초안이 나옵니다.

생활과 공공 데이터 스킬은 [k-skill](https://github.com/NomaDamas/k-skill)을 함께 쓰면 좋습니다.

## 설치

**방법 1. skills CLI (한 줄, Claude Code 말고 다른 에이전트도 지원)**

```bash
npx skills add stanlee7/korean-office-skills
```

- 설치하지 않고 목록만 보려면 `npx skills add stanlee7/korean-office-skills --list`
- 하나만 설치하려면 `--skill report-gaejosik`처럼 이름을 붙이고, 모든 프로젝트에서 쓰려면 `-g`를 붙입니다.
- 안내 출처: [vercel-labs/skills](https://github.com/vercel-labs/skills) (2026-10-08 확인). Node.js의 `npx`가 필요합니다.

**방법 2. Claude Code 플러그인 마켓플레이스**

Claude Code 안에서 차례로 입력합니다.

```
/plugin marketplace add stanlee7/korean-office-skills
/plugin install korean-office-skills@korean-office-skills
```

플러그인으로 설치하면 스킬 이름 앞에 플러그인 이름이 붙습니다(예: `/korean-office-skills:report-gaejosik`). 자연어로 부르면 이름을 몰라도 됩니다.

**방법 3. 직접 복사**

[Claude Code](https://code.claude.com/docs/en/skills) 개인 스킬 폴더(`~/.claude/skills/`)에 원하는 스킬 폴더를 복사하면 모든 프로젝트에서 쓸 수 있습니다.

```bash
git clone https://github.com/stanlee7/korean-office-skills.git && mkdir -p ~/.claude/skills && cp -r korean-office-skills/*/ ~/.claude/skills/
```

- 한 프로젝트에서만 쓰려면 그 프로젝트의 `.claude/skills/`에 복사합니다.
- 윈도우는 `~` 대신 `%USERPROFILE%` 폴더(예: `C:\Users\내이름\.claude\skills\`)에 스킬 폴더를 복사하면 됩니다.

## 스킬 목록

| 스킬 | 하는 일 | 이렇게 부르면 됩니다 |
|---|---|---|
| [`meeting-to-todo`](meeting-to-todo/SKILL.md) | 회의 메모 → 할 일 표(할 일, 담당, 기한, 근거 문장) + 결정 사항 3줄. 메모에 없는 담당과 기한은 「미정」, 고객명과 연락처는 `[고객A]`처럼 가림 | `/meeting-to-todo` 또는 「이 회의 메모 할 일로 정리해 줘」 |
| [`weekly-report`](weekly-report/SKILL.md) | 한 주 메모 → 주간보고 초안(이번 주 한 일, 다음 주 계획, 이슈와 요청). 숫자는 원문에 있는 것만, 회사 양식이 있으면 그 칸에 맞춤 | `/weekly-report` 또는 「이번 주 메모로 주간보고 써 줘」 |
| [`report-gaejosik`](report-gaejosik/SKILL.md) | 메모나 긴 글 → 개조식 보고서. 결론 먼저, □ ○ - 기호, 「~함」「~임」 끝맺음, 숫자는 원문에 있는 것만, 근거 없는 판단은 `[확인 필요]` | `/report-gaejosik` 또는 「개조식 보고서로 정리해 줘」 |
| [`pumui-draft`](pumui-draft/SKILL.md) | 메모 → 품의서, 기안문 초안(제목, 목적, 추진 배경, 주요 내용, 소요 예산, 기대 효과, 붙임). 예산이 원문에 없으면 빈칸, 회사 양식이 있으면 그 칸에 맞춤 | `/pumui-draft` 또는 「품의서 초안 써 줘」 |
| [`gongmun-tone`](gongmun-tone/SKILL.md) | 일반 글 → 공문 어투(「~하고자 하오니」, 붙임, 「끝.」, `2026. 10. 8.` 날짜). 반대로 공문을 쉬운 말과 「내가 할 일」로 풀기도 함 | `/gongmun-tone` 또는 「공문체로 바꿔 줘」, 「이 공문 쉽게 풀어 줘」 |
| [`email-reply-kr`](email-reply-kr/SKILL.md) | 곤란한 업무 메일 답장(거절, 일정 미루기, 재촉, 범위 밖 요청, 실수 사과). 결론은 사용자가 정하고 문장만 씀, 말하지 않은 약속과 날짜는 넣지 않음 | `/email-reply-kr` 또는 「이 메일 정중하게 거절하는 답장 써 줘」 |
| [`pii-mask-before-ai`](pii-mask-before-ai/SKILL.md) | AI에 붙여 넣기 전 개인정보 가리기. 전화, 이메일, 주민번호 형식, 사업자번호, 카드번호, 계좌 의심 숫자를 `[전화1]`처럼 바꾸고 되돌리기 표를 따로 줌. 이름과 주소는 직접 확인 안내 | `/pii-mask-before-ai` 또는 「AI에 넣기 전에 개인정보 가려 줘」 |

## 쓰는 법 예시

Claude Code를 열고 메모를 그대로 붙여 넣습니다.

```
/meeting-to-todo
10/6 주간 회의
- 견적 단가 5% 조정해서 다시 보내기로 함. 김대리가 수요일까지.
- 신제품 소개 자료는 디자인팀이랑 같이 손보기로. 누가 할지는 못 정함
```

결과(요약):

| 번호 | 할 일 | 담당 | 기한 | 근거 문장 |
|---|---|---|---|---|
| 1 | 견적서 단가 5% 조정해 다시 보내기 | 김대리 | 수요일 | "단가 5% 조정해서 다시 보내기로 함..." |
| 2 | 신제품 소개 자료 디자인팀과 함께 수정하기 | 미정 | 미정 | "누가 할지는 못 정함" |

회사 양식(주간보고, 보고서, 품의서)이 있으면 양식을 같이 붙여 넣으세요. 그 칸 이름과 순서대로 채웁니다.

```
이번 주 메모로 주간보고 써 줘. 양식은 [추진 실적 / 차주 계획 / 건의 사항] 이야.
(메모 붙여 넣기)
```

곤란한 메일은 받은 메일과 **내가 정한 결론**을 같이 줍니다.

```
/email-reply-kr 결론은 거절. 이번 계약에 영상 편집은 없음. 원하면 별도 견적 가능.
(받은 메일 붙여 넣기)
```

각 스킬 폴더의 `예시/`에 입력과 기대 출력 예시가 있습니다(모두 **가상 데이터**).

## 주의

- **회사 기밀과 개인정보는 넣지 마세요.** 고객 연락처, 주민번호, 계약 금액, 미공개 사업 계획 같은 내용은 지우거나 `[고객A]`처럼 바꾼 뒤 붙여 넣으세요. 회사의 AI 사용 규정이 있으면 그 규정이 먼저입니다.
- `pii-mask-before-ai`도 AI 안에서 돌아갑니다. 원문을 붙여 넣으면 원문은 그 대화에 들어갑니다. 외부 AI에 넣으면 안 되는 자료는 회사가 허용한 도구로 가리세요.
- 스킬은 결과를 **초안**으로 만듭니다. 보고나 발송 전에 사람이 꼭 읽고 고치세요. 같은 입력이어도 결과가 조금씩 다를 수 있습니다.
- 스킬은 원문에 없는 담당, 기한, 숫자, 약속을 지어내지 않도록 만들었지만, 틀린 곳이 없는지 원문과 대조해 보세요.

## 확인한 환경

- 형식 기준: Claude Code 공식 문서 [Skills](https://code.claude.com/docs/en/skills) (2026-10-08 확인). `SKILL.md` 머리말은 모두 선택 항목이고 `description` 작성을 권장하며, `name`을 비우면 폴더 이름을 씁니다. 개인 스킬은 `~/.claude/skills/<스킬이름>/SKILL.md`에 둡니다. 머리말의 `license`, `metadata`(category, locale)는 다른 스킬 모음과 맞추기 위한 정보 항목입니다.
- 플러그인 형식: Claude Code 공식 문서 [Create a marketplace](https://code.claude.com/docs/en/plugin-marketplaces), [Plugin manifest reference](https://code.claude.com/docs/en/plugins/manifest-reference) (2026-10-08 확인). `claude plugin validate`로 `marketplace.json`, `plugin.json` 모두 통과했고, 따로 만든 빈 설정 폴더에서 마켓플레이스 추가와 설치를 해 스킬 7개가 잡히는 것을 확인했습니다.
- skills CLI: 2026-10-08 `npx skills add <이 저장소 경로> --list`(설치 없이 목록만)로 스킬 7개가 모두 잡히는 것을 확인했습니다.
- 동작 확인: 2026-10-08 윈도우 11, Claude Code 2.1.292, `claude -p --add-dir`로 스킬을 불러와 각 `예시/` 입력으로 시험했습니다. 새 스킬 5개 모두 슬래시 호출과 자연어 요청(「개조식 보고서로 정리해 줘」, 자동 호출)으로 동작했고, 개조식 「~함」「~임」 끝맺음, 품의서 예산 빈칸, 공문 날짜 표기와 「끝.」(연도 없는 날짜는 연도를 지어내지 않음), 메일 답장에 말하지 않은 약속 미추가, 개인정보 8종 가림과 되돌리기 표 분리 규칙을 지켰습니다. 기존 두 스킬은 같은 날 같은 방법으로 시험했습니다.

## 만든 사람

이규동 (AI 교육, AX 컨설팅)
새 스킬 아이디어나 고칠 점은 이 저장소의 Issues에 남겨 주세요.

## 라이선스

[MIT](LICENSE). 회사와 개인 모두 자유롭게 쓰고 고칠 수 있습니다.
