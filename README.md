# native-korean-dev

Claude Code 가 한국어로 답할 때 자연스럽고 정확한 한국어를 쓰게 하는 output style 입니다. 별도의 추가 구성 없이 파일 하나로 적용할 수 있습니다.

A Claude Code output style for natural, native-sounding Korean and precise technical explanations. One file, no folders, no framework. Keeps Claude Code's built-in coding instructions intact.

## 개발 배경

Claude Code 는 한국어로 설명할 때 영어 문장 구조를 그대로 옮기고, 개발 현장에서 통용되는 용어를 모호한 일상어로 대체하며, 수학 용어를 비유로 끌어 쓰는 경향이 있습니다. 예를 들면 다음과 같은 문장입니다.

> 여기서 로직이 **갈립니다**.
> 이 변경으로 **회귀**가 발생할 수 있습니다.
> 판정 값을 카드 단계까지 **들고 있을** 필요가 없습니다.
> 두 판정은 서로 **직교**합니다.

갈린다는 분기인지 분리인지 불분명하고, 회귀는 통계 용어라 소프트웨어 문맥의 regression(기존 기능의 재고장)을 뜻하는지 한 번 더 해석해야 하며, 직교는 수학 밖에서는 뜻이 정해져 있지 않습니다. 이 저장소를 만든 사람도 이런 문장을 읽으며 자신의 독해력을 의심했고, AI 와 일하려면 AI 말투를 해독하는 능력을 따로 길러야 하는지 고민했습니다. 원인은 독자가 아니라 모델의 어휘 선택에 있으므로, 이 스타일은 그 어휘 선택을 바로잡습니다. 적용 전후 예시는 다음과 같습니다.

| 적용 전 | 적용 후 |
|---|---|
| 여기서 로직이 갈립니다 | 조건에 따라 처리 경로가 분기됩니다 |
| 이 변경으로 회귀가 발생할 수 있습니다 | 이 변경으로 기존에 동작하던 기능이 다시 고장날 수 있습니다 |
| 쿼리를 태웁니다 | 쿼리를 실행합니다 |
| 이 설정은 사용자에 의해 변경될 수 있습니다 | 사용자가 이 설정을 변경할 수 있습니다 |
| 좋은 질문입니다! 지금부터 차근차근 설명해 드리겠습니다 | (바로 답합니다) |
| 더 자세히 알아볼까요? 다른 예시도 보여드릴까요? | (끝났으면 끝냅니다) |

## 단일 파일 구성

비슷한 목적의 저장소는 폴더가 여러 겹이고 스킬·훅·커맨드·설정 파일이 서로를 가리키고 있어서, 한국어 규칙 한 줄을 고치려 해도 파일 사이의 의존 관계부터 파악해야 합니다.

이 저장소는 `styles/native-korean-dev.md` 한 파일이 전부입니다.

- **설치**: 파일을 복사하는 것으로 끝납니다. 폴더 구조를 맞출 것도, 다른 파일을 함께 가져올 것도 없습니다.
- **가독성**: 조항마다 부자연스러운 표현과 자연스러운 표현이 짝으로 붙어 있어서, 규칙이 무슨 뜻인지 예시로 바로 확인할 수 있습니다.
- **수정**: 필요 없는 조항은 삭제하고, 자주 나타나는 표현은 예시에 추가하면 됩니다. 다른 파일을 함께 고칠 필요가 없습니다.
- **코딩 지침 유지**: frontmatter 의 `keep-coding-instructions: true` 가 Claude Code 기본 코딩 지침을 그대로 남기고, 그 뒤에 이 파일이 붙습니다.

## 구성 내용

맨 앞에 응답 판단 우선순위가 있고, 그 뒤에 지시문이 이어집니다.

| 지시문 | 다루는 것 |
|---|---|
| Korean Native Communication Instruction | 발화 의도 해석, 한국어식 생략, 번역투 제거, 말투 선택, AI 식 친절 표현 금지, 문장 호흡, 정보 밀도, 무조건 동의 금지, 문서 종류별 문체, 맞춤법 검수, 응답 구조 고정 금지 |
| Technical Communication Instruction | 기술 용어를 일상어로 치환하지 않기, 비유보다 동작 설명, 용어 번역 금지, 지식 수준 존중, 실행 흐름·조건·예외 명시, 코드와 설명 일치 |
| Advanced Korean & Technical Reasoning Instruction | 핵심 먼저 답하기, 헷갈리는 지점 찾기, 비슷한 개념 구분, 코드 실행 추적, 증상·원인·해결책 구분, 설계 선택의 조건, 기존 코드 존중, 보장 범위, 사실과 추정 구분, 검증 가능한 예시, 맥락 유지, 과시 금지, 설명과 평가 구분, 출력 형식 우선, 끝맺음 질문 금지, 서식 남용 금지, 오류 수정 방식 |
| Korean Documentation Style Instruction | 영어식 의문형 제목 금지, 명사형 항목명, 제목과 본문의 문체 구분, 한국어 문서 관습 표현, 광고 문구 금지, 질문형 구성 금지, 제목 검수 |
| Quantity Expression & Natural Korean Instruction | 핵심이 아닌 개수 생략, 고유어 수사 남용 금지, 영어식 수량 도입문 금지, 정확한 수량이 필요한 자리 유지, 작업 보고에서 개수보다 변경 내용 |
| Korean Lexical Precision & Information Structure | 설명형 명사구 대신 정확한 어휘, 첫 문장에 핵심 정보, 독자 반응 서술 금지, 짧은 문장 반복 금지, 극적 전개 금지, 감정적 비유 금지, 문어체 기본 |

지시문이 서로 충돌하면 우선순위를 따릅니다. **정확한 사실과 기술 동작** > 사용자의 실제 질문 > 대화 맥락과 기술 수준 > 명확한 인과관계와 실행 흐름 > 자연스러운 한국어와 간결함. 자연스러운 한국어가 맨 아래인 이유는 틀린 내용을 자연스럽게 말하는 것이 가장 나쁘기 때문입니다.

## 설치 방법

```sh
mkdir -p ~/.claude/output-styles
curl -fsSL https://raw.githubusercontent.com/saokiritori/native-korean-dev/main/styles/native-korean-dev.md \
  -o ~/.claude/output-styles/native-korean-dev.md
```

그다음 `~/.claude/settings.json` 에 아래 설정을 넣습니다. Claude Code 안에서 `/config` 를 열어 Output style 에서 `native-korean-dev` 를 골라도 같습니다.

```json
{
  "outputStyle": "native-korean-dev"
}
```

**새 세션을 열어야 적용됩니다.** output style 은 세션이 시작할 때 시스템 프롬프트에 들어가므로, 이미 열려 있는 세션은 옛 지침을 계속 따릅니다.

특정 프로젝트에서만 쓰려면 그 프로젝트의 `.claude/settings.local.json` 에 같은 키를 넣습니다. 프로젝트 설정이 사용자 설정보다 우선합니다.

## 수정 방법

파일을 열어 조항을 고치면 됩니다. 조항마다 부자연스러운 표현과 자연스러운 표현의 짝을 예시로 둡니다. 예시가 없으면 모델이 규칙의 문구만 기계적으로 대조하고, 예시가 있으면 그 짝을 보고 비슷한 자리를 스스로 고칩니다.

frontmatter 는 다음과 같습니다.

```yaml
name: native-korean-dev          # 파일명과 같아야 하고, settings.json 의 outputStyle 값이 됩니다
description: ...                 # /config 목록에 보이는 한 줄 설명입니다
keep-coding-instructions: true   # Claude Code 의 코딩 지침을 유지합니다. 빼면 코딩 지침이 사라집니다
```

이름을 바꾸려면 파일명과 `name` 을 같이 바꾸고 `settings.json` 의 값도 맞춥니다.

## 라이선스

MIT 입니다. 복사·수정·재배포가 가능합니다.
