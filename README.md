# native-korean-dev

Claude Code 가 한국어로 답할 때 자연스럽고 정확한 한국어를 쓰게 하는 output style 입니다. 파일 하나를 복사하면 적용됩니다.

A Claude Code output style for natural, native-sounding Korean and precise technical explanations. One file. Keeps Claude Code's built-in coding instructions intact.

## 개발 배경

Claude Code 는 한국어로 설명할 때 영어 문장 구조를 그대로 옮기고, 개발 현장에서 통용되는 용어를 모호한 일상어로 대체하며, 수학 용어를 비유로 끌어 쓰는 경향이 있습니다.

> 여기서 로직이 **갈립니다**.
> 이 변경으로 **회귀**가 발생할 수 있습니다.
> 두 판정은 서로 **직교**합니다.

'갈린다'는 분기인지 분리인지 불분명합니다. '회귀'는 통계 용어라서, 기존 기능이 다시 고장 나는 현상(regression)을 뜻하는지 한 번 더 해석해야 합니다. '직교'는 수학 밖에서는 뜻이 정해져 있지 않습니다. 작성자도 이런 문장을 읽으며 자신의 독해력을 의심했고, AI 와 일하려면 AI 말투를 해독하는 능력을 따로 길러야 하는지 고민했습니다. 원인은 독자가 아니라 모델의 어휘 선택에 있으므로, 이 output style 은 그 어휘 선택을 바로잡습니다.

| 적용 전 | 적용 후 |
|---|---|
| 여기서 로직이 갈립니다 | 조건에 따라 처리 경로가 분기됩니다 |
| 이 변경으로 회귀가 발생할 수 있습니다 | 이 변경으로 기존에 동작하던 기능이 다시 고장 날 수 있습니다 |
| 이 설정은 사용자에 의해 변경될 수 있습니다 | 사용자가 이 설정을 변경할 수 있습니다 |
| 좋은 질문입니다! 지금부터 차근차근 설명해 드리겠습니다 | (도입 문장 없이 바로 답합니다) |

기존에 공개된 스킬·프롬프트 저장소를 써 보니 폴더와 파일이 많아서, 어느 파일을 어디에 넣어야 하는지부터 파악해야 했고 그 과정이 불편했습니다. 그래서 직접 만들어 올렸습니다. 이 저장소에는 `styles/native-korean-dev.md` 파일 하나만 있고, 앞으로도 파일을 늘리거나 복잡한 규칙을 추가하지 않고 이 한 파일만 간결하게 유지할 계획입니다. 필요 없는 조항은 파일을 열어 지우면 됩니다.

## 사용 방법

```sh
mkdir -p ~/.claude/output-styles
curl -fsSL https://raw.githubusercontent.com/saokiritori/native-korean-dev/main/styles/native-korean-dev.md \
  -o ~/.claude/output-styles/native-korean-dev.md
```

`~/.claude/settings.json` 에 아래 설정을 넣습니다. Claude Code 안에서 `/config` 를 열어 Output style 항목에서 `native-korean-dev` 를 선택해도 됩니다.

```json
{
  "outputStyle": "native-korean-dev"
}
```

새 세션을 열어야 적용됩니다. 특정 프로젝트에서만 쓰려면 그 프로젝트의 `.claude/settings.local.json` 에 같은 키를 넣습니다.

## 라이선스

MIT
