# native-korean-dev

Claude Code 가 한국어로 말할 때 **사람 말을 하게** 만드는 output style 이다. 파일 하나다. 복사해서 넣으면 끝난다.

A Claude Code output style for natural, native-sounding Korean and precise technical explanations. One file, no folders, no framework. Keeps Claude Code's built-in coding instructions intact.

## 왜 만들었나

Claude Code 의 설명을 읽다 보면 이런 문장을 만난다.

> 여기서 로직이 **갈립니다**.
> 이 변경으로 **회귀**가 발생할 수 있습니다.
> 판정 값을 카드 단계까지 **들고 있을** 필요가 없습니다.
> 두 판정은 서로 **직교**합니다.

읽고 나서 잠깐 멈춘다. 갈린다는 게 분기한다는 건가, 갈라진다는 건가. 회귀는 통계 용어 아닌가. 직교는 또 뭔가. 내 독해력이 떨어진 건가. 이제 인간은 AI 네이티브가 되기 위해 글 읽는 능력이 아니라 **AI 말투를 해독하는 능력**을 따로 길러야 하는 건가.

아니다. 모델이 영어 문장 구조를 그대로 한국어로 옮기고, 개발 현장에서 멀쩡히 쓰는 용어를 굳이 일상어로 바꿔 뭉개고, 수학에서 가져온 말을 비유로 끌어 쓰기 때문이다. 읽는 사람 잘못이 아니다. 그래서 만들었다. 이 스타일을 켜면 저 문장은 이렇게 나온다.

| 켜기 전 | 켠 뒤 |
|---|---|
| 여기서 로직이 갈립니다 | 조건에 따라 처리 경로가 분기됩니다 |
| 이 변경으로 회귀가 발생할 수 있습니다 | 이 변경으로 기존에 동작하던 기능이 다시 고장날 수 있습니다 |
| 쿼리를 태웁니다 | 쿼리를 실행합니다 |
| 이 설정은 사용자에 의해 변경될 수 있습니다 | 사용자가 이 설정을 변경할 수 있습니다 |
| 좋은 질문입니다! 지금부터 차근차근 설명해 드리겠습니다 | (바로 답한다) |
| 더 자세히 알아볼까요? 다른 예시도 보여드릴까요? | (끝났으면 끝낸다) |

## 파일 하나면 된다

비슷한 목적의 저장소를 열어 보면 폴더가 여러 겹이고, 스킬·훅·커맨드·설정 파일이 서로를 가리키고 있다. 한국어 규칙 한 줄을 고치고 싶은데 구조부터 파악해야 한다. 쓰기 전에 지친다.

이 저장소는 `styles/native-korean-dev.md` 한 파일이 전부다.

- **설치는 복사 한 번이다.** 폴더 구조를 맞출 것도, 다른 파일을 함께 가져올 것도 없다.
- **읽을 수 있다.** 조항마다 '부자연스러운 표현'과 '자연스러운 표현'이 짝으로 붙어 있어서, 규칙이 무슨 뜻인지 예시로 바로 보인다.
- **고칠 수 있다.** 마음에 안 드는 조항은 지우고, 자주 걸리는 표현은 예시에 한 줄 더 넣으면 된다. 고친 뒤 새 세션을 열면 그대로 반영된다.
- **코딩 지침은 건드리지 않는다.** frontmatter 의 `keep-coding-instructions: true` 가 Claude Code 기본 코딩 지침을 그대로 남기고, 그 뒤에 이 파일이 붙는다.

## 무엇이 들어 있나

맨 앞에 **응답 판단 우선순위** 5단계가 있고, 그 뒤에 지시문 셋이 이어진다.

| 지시문 | 다루는 것 |
|---|---|
| Korean Native Communication Instruction | 발화 의도 해석, 한국어식 생략, 번역투 제거, 말투 선택, AI 식 친절 표현 금지, 문장 호흡, 정보 밀도, 무조건 동의 금지, 문서 종류별 문체, 맞춤법 검수, 응답 구조 고정 금지 |
| Technical Communication Instruction | 기술 용어를 일상어로 치환하지 않기, 비유보다 동작 설명, 용어 번역 금지, 지식 수준 존중, 실행 흐름·조건·예외 명시, 코드와 설명 일치 |
| Advanced Korean & Technical Reasoning Instruction | 핵심 먼저 답하기, 헷갈리는 지점 찾기, 비슷한 개념 구분, 코드 실행 추적, 증상·원인·해결책 구분, 설계 선택의 조건, 기존 코드 존중, 보장 범위, 사실과 추정 구분, 검증 가능한 예시, 맥락 유지, 과시 금지, 설명과 평가 구분, 출력 형식 우선, 끝맺음 질문 금지, 서식 남용 금지, 오류 수정 방식 |

세 지시문이 충돌하면 우선순위를 따른다. **정확한 사실과 기술 동작** > 사용자의 실제 질문 > 대화 맥락과 기술 수준 > 명확한 인과관계와 실행 흐름 > 자연스러운 한국어와 간결함. 자연스러운 한국어가 맨 아래인 이유는, 틀린 내용을 자연스럽게 말하는 것이 제일 나쁘기 때문이다.

## 설치

```sh
mkdir -p ~/.claude/output-styles
curl -fsSL https://raw.githubusercontent.com/saokiritori/native-korean-dev/main/styles/native-korean-dev.md \
  -o ~/.claude/output-styles/native-korean-dev.md
```

그다음 `~/.claude/settings.json` 에 아래 한 줄을 넣는다. Claude Code 안에서 `/config` 를 열어 Output style 에서 `native-korean-dev` 를 골라도 같다.

```json
{
  "outputStyle": "native-korean-dev"
}
```

**새 세션을 열어야 적용된다.** output style 은 세션이 시작할 때 시스템 프롬프트에 들어가므로, 이미 열려 있는 세션은 옛 지침을 계속 따른다.

특정 프로젝트에서만 쓰려면 그 프로젝트의 `.claude/settings.local.json` 에 같은 키를 넣는다. 프로젝트 설정이 사용자 설정보다 우선한다.

## 고치는 법

파일을 열어 조항을 고치면 된다. 조항마다 부자연스러운 표현과 자연스러운 표현의 짝을 예시로 두어야 한다. 예시가 없으면 모델이 규칙의 문구만 기계적으로 대조하고, 예시가 있으면 그 짝을 보고 비슷한 자리를 알아서 고친다.

frontmatter 는 세 줄이다.

```yaml
name: native-korean-dev          # 파일명과 같아야 하고, settings.json 의 outputStyle 값이 된다
description: ...                 # /config 목록에 보이는 한 줄 설명
keep-coding-instructions: true   # Claude Code 의 코딩 지침을 유지한다. 빼면 코딩 지침이 사라진다
```

이름을 바꾸고 싶으면 파일명과 `name` 을 같이 바꾸고 `settings.json` 의 값도 맞춘다.

## 라이선스

MIT. 가져다 쓰고, 고치고, 다시 나눠도 된다.
