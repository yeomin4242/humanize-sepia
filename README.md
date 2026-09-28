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

온라인 장터의 운영 직무에 지원하는 자기소개서를 쓰고 싶어.
회사는 소규모 판매자를 돕고, 이 직무는 판매자 문의를 처리하고
반복되는 불편을 개선하는 일을 해. 문항은 “익숙한 방식에서
벗어나 문제를 해결한 경험을 설명해 주세요.”야.

매장에서 알바할 때 담당자마다 답이 달라 손님이 다시 묻곤 했어.
나는 자주 오는 문의를 모아 답변표 초안을 만들었고, 매니저가
확인한 뒤 교대자들이 함께 쓰기 시작했어. 교대자가 답을 찾기
편해졌다고 했지만, 재문의 건수는 측정하지 않았어.

문제를 응대 속도보다 답변의 일관성에서 본 점을 드러내고 싶어.
초안에 쓴 “남다른 관찰력”, “혁신적인 개선” 같은 말보다는
실제로 한 일로 설득해 줘. 과장 없이 담담하게, 공백 포함
500자 이내로 써줘. 회사 슬로건은 억지로 넣지 말아줘.
```

A draft can be a starting point for further writing. The skill keeps useful wording and voice, develops the piece around your intended message, and follows the scope you set. When a missing detail would change the argument or a material fact, it asks a focused question.

To work on an existing text, specify the scope:

```text
$humanize-sepia 원문을 최소한으로 다듬어줘. 수치와 직접 인용은 유지해줘.
원문: …

$humanize-sepia 진단만 해줘. 실제 문제와 선택 가능한 개선을 구분해줘.
원문: …

$humanize-sepia 사실과 핵심 메시지를 유지하면서 전면 개작해줘.
원문: …
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
