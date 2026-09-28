# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**Write clear, natural Korean that says what you mean.** Humanize Sepia helps you turn ideas and experiences into a complete draft, develop a coherent argument, and refine the language while preserving your facts and voice. Use it to write new prose, improve an existing draft, or review what a piece needs.

Version: **0.1.0**. The skill's instructions and examples are primarily Korean. All writing guidance is included in the `humanize-sepia` folder.

## What it does

| Mode | Use |
|---|---|
| `write` | Develop a complete draft from your ideas, experiences, or notes, with a clear point and coherent flow. |
| `refactor` | Revise an existing text while preserving its argument, facts, voice, and event order. |
| `review` | Diagnose a text without rewriting it; distinguish actual problems from optional suggestions. |
| `recreate` | Rebuild the structure when you explicitly request a full rewrite, preserving the facts and intent. |

The writing starts with your intended message and the reader. The skill selects details that support that message, gives important judgments and actions room to develop, and connects paragraphs so the reader can follow the reasoning. It then refines phrasing, sentence rhythm, and tone without forcing every piece into the same structure.

For job application essays, it reads what the prompt is trying to assess in the context of the company and role. A question about a “different perspective” may call for showing how you recognized a problem and chose an approach. The experience should make that judgment visible. Explicit length limits, example counts, and required subquestions still apply.

It distinguishes what you want to convey from what you actually did. Individual actions, approval by others, and team outcomes keep their respective scope. When essential facts are missing, it asks focused questions or gives a provisional draft with remaining gaps outside the essay body.

## Install for Codex

Ask Codex to install the skill:

```text
$skill-installer https://github.com/yeomin4242/humanize-sepia/tree/main/skills/humanize-sepia
```

For a manual user installation, clone the repository and copy the skill folder. If a folder named `humanize-sepia` is already installed, move it to a backup location first.

```bash
git clone https://github.com/yeomin4242/humanize-sepia.git
mkdir -p ~/.agents/skills
cp -R humanize-sepia/skills/humanize-sepia ~/.agents/skills/
```

For project-local use, place the folder at `.agents/skills/humanize-sepia` in your project.

## Use

Invoke `$humanize-sepia` and describe what you want to write. Share the message, audience, and tone you have in mind, along with any experiences, notes, or draft you want to use. You can write naturally, without a fixed template. “쓰고자 하는 방향” (“what I want to write”) is an optional label.

The company and experience below are fictional examples.

```text
$humanize-sepia

소규모 판매자들이 이용하는 온라인 장터의 운영 직무에 지원하려고 해.
판매자 문의에 답하고, 자주 생기는 불편을 찾아 개선하는 일이래.
자소서에서는 익숙한 방식에서 벗어나 문제를 해결한 경험을 묻고 있어.

매장에서 아르바이트할 때, 직원마다 안내가 달라서 손님이 같은 질문을
다시 하는 일이 있었어. 자주 들어오는 질문과 답을 표로 정리했고,
매니저가 확인한 뒤 교대 근무하는 동료들과 함께 쓰기 시작했어.
동료들은 답을 찾기 편해졌다고 했어. 같은 질문이 얼마나 줄었는지는
따로 세어 보지 않았고.

직원마다 안내가 달랐다는 점에 주목하고 해결한 경험을 쓰고 싶어.
초안에는 “남다른 관찰력으로 혁신적인 개선을 이루었다”고 썼는데,
좀 거창하게 느껴져. 내가 한 일이 잘 드러나도록 자연스럽게 써줘.
공백 포함 500자 이내로, 담담한 말투면 좋겠어.
```

A draft can be a starting point for further writing. The skill keeps useful wording and voice, develops the piece around your intended message, and follows the scope you set. When a missing detail would change the argument or a material fact, it asks a focused question.

To work on an existing text, specify the scope:

```text
$humanize-sepia 내용과 말투는 그대로 두고, 어색한 문장만 다듬어줘.
숫자와 인용문은 바꾸지 말아줘.
글: …
```

```text
$humanize-sepia 글은 고치지 말고, 어디가 어색하거나 부족한지 알려줘.
글: …
```

```text
$humanize-sepia 하고 싶은 말과 실제 있었던 일은 유지해줘.
글의 구성부터 새로 잡아서 처음부터 다시 써줘.
글: …
```

The default result starts with the text, followed by material reasons for changes or information to confirm. Your requested format takes priority. The author remains responsible for checking factual claims; AI-detector results are not a measure of completion.

## Repository

```text
skills/humanize-sepia/
  SKILL.md
  agents/openai.yaml
  references/
    editing.md
    drafting.md
    applications.md
  LICENSE
README.md
README.ko.md
LICENSE
```

## Inspired by

[Sepia](https://github.com/Nanako0129/sepia) · [humanize-korean](https://github.com/epoko77-ai/im-not-ai)

## License

[MIT](LICENSE).
