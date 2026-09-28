# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**Natural Korean writing from loosely organized material and your own intentions.** Paste company information, a prompt, your preferred direction, and a draft in any order. Humanize Sepia interprets what the reader needs to assess, then selects evidence from your experience to write an appropriate answer. It also revises and reviews existing Korean prose.

Version: **0.1.0**. The skill's instructions and examples are primarily Korean. All writing guidance is included in the `humanize-sepia` folder.

## What it does

| Mode | Use |
|---|---|
| `write` | Use mixed material, intentions, and drafts to answer the reader's underlying question. |
| `refactor` | Revise an existing text while preserving its argument, facts, voice, and event order. |
| `review` | Diagnose a text without rewriting it; distinguish actual problems from optional suggestions. |
| `recreate` | Rebuild the structure when you explicitly request a full rewrite, preserving the facts and intent. |

For applications, the skill reads the prompt in the context of the company and role. A question about a “different perspective” may call for explaining how you recognized a problem and chose an approach. Explicit length limits, example counts, and required subquestions still apply.

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

Invoke `$humanize-sepia` and paste your material. There are no required field names or ordering. “쓰고자 하는 방향” (“what I want to write”) is an optional label for free-form input.

The company and experience below are fictional examples.

```text
$humanize-sepia

과장 없이 담담하게, 공백 포함 500자 이내로 써줘.
지원 회사는 소규모 판매자를 위한 온라인 장터를 운영하고,
운영 직무는 판매자 문의를 처리하고 반복되는 불편을 개선한대.

초안은 “저는 남다른 관찰력으로 기존의 틀을 깨는 사람입니다.
매장에서 문의를 정리하며 혁신적인 개선을 이루었습니다.” 정도야.
너무 거창해서 내가 실제로 한 일로 설득하고 싶어.

문항은 “익숙한 방식에서 벗어나 문제를 해결한 경험을 설명해 주세요.”
매장에서 알바할 때, 답이 담당자마다 달라서 손님이 다시 묻곤 했어.
나는 자주 오는 문의를 모아 답변표 초안을 만들었고,
매니저가 확인한 뒤 교대자들이 함께 쓰기 시작했어.
이후 교대자가 답을 찾기 편해졌다고 했어. 재문의 건수는 측정 안 했어.
새 프로그램을 만든 건 아니고, 문제를 응대 속도보다 답변의
일관성에서 본 점을 보여 주고 싶어. 회사 슬로건은 억지로 넣지 말아줘.
```

A draft remains useful material when you ask for a completed answer using the broader context. The skill preserves useful wording and voice and follows your latest explicit direction. It clarifies ambiguity when it would change the subject or a material fact.

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
