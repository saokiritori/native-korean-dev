# native-korean-dev

Claude Code 의 output style 입니다. Claude 가 한국어로 답할 때 번역투와 AI 식 군말을 걷어내고, 개발 개념을 설명할 때 기술 용어를 일상어로 뭉개지 않게 합니다. Claude Code 의 기본 코딩 지침은 그대로 유지됩니다.

A Claude Code output style for natural, native-sounding Korean and precise technical explanations. Keeps Claude Code's built-in coding instructions intact.

## 무엇이 들어 있나

파일은 `styles/native-korean-dev.md` 하나입니다. 맨 앞에 **응답 판단 우선순위** 5단계가 있고, 그 뒤에 지시문 셋이 이어집니다.

| 지시문 | 다루는 것 |
|---|---|
| Korean Native Communication Instruction | 발화 의도 해석, 한국어식 생략, 번역투 제거, 말투 선택, AI 식 친절 표현 금지, 문장 호흡, 정보 밀도, 무조건 동의 금지, 문서 종류별 문체, 맞춤법 검수, 응답 구조 고정 금지 |
| Technical Communication Instruction | 기술 용어를 일상어로 치환하지 않기, 비유보다 동작 설명, 용어 번역 금지, 지식 수준 존중, 실행 흐름·조건·예외 명시, 코드와 설명 일치 |
| Advanced Korean & Technical Reasoning Instruction | 핵심 먼저 답하기, 헷갈리는 지점 찾기, 비슷한 개념 구분, 코드 실행 추적, 증상·원인·해결책 구분, 설계 선택의 조건, 기존 코드 존중, 보장 범위, 사실과 추정 구분, 검증 가능한 예시, 맥락 유지, 과시 금지, 설명과 평가 구분, 출력 형식 우선, 끝맺음 질문 금지, 서식 남용 금지, 오류 수정 방식 |

세 지시문이 충돌하면 우선순위를 따릅니다. 정확한 사실과 기술 동작 > 사용자의 실제 질문 > 대화 맥락과 기술 수준 > 명확한 인과관계와 실행 흐름 > 자연스러운 한국어와 간결함.

## 설치

파일 하나를 복사하고 설정 한 줄을 넣으면 끝납니다.

```sh
mkdir -p ~/.claude/output-styles
curl -fsSL https://raw.githubusercontent.com/saokiritori/native-korean-dev/main/styles/native-korean-dev.md \
  -o ~/.claude/output-styles/native-korean-dev.md
```

그다음 `~/.claude/settings.json` 에 아래 한 줄을 넣습니다. 세션 안에서 고르려면 `/config` 를 열어 Output style 에서 `native-korean-dev` 를 선택해도 됩니다.

```json
{
  "outputStyle": "native-korean-dev"
}
```

**새 세션을 열어야 적용됩니다.** output style 은 세션이 시작할 때 시스템 프롬프트에 들어가므로, 이미 열려 있는 세션에는 반영되지 않습니다.

프로젝트마다 다르게 쓰려면 그 프로젝트의 `.claude/settings.local.json` 에 같은 키를 넣습니다. 프로젝트 설정이 사용자 설정보다 우선합니다.

## 고치는 법

파일을 열어 조항을 고치면 됩니다. 조항마다 부자연스러운 표현과 자연스러운 표현의 짝을 예시로 두어야 Claude 가 문구만 기계적으로 대조하지 않습니다.

frontmatter 는 세 줄입니다.

```yaml
name: native-korean-dev          # 파일명과 같아야 하고, settings.json 의 outputStyle 값이 됩니다
description: ...                 # /config 목록에 보이는 한 줄 설명
keep-coding-instructions: true   # Claude Code 의 코딩 지침을 유지합니다. 빼면 코딩 지침이 사라집니다
```

## 라이선스

MIT
