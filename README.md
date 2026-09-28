# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**Write clear, natural Korean that says what you mean.** Humanize Sepia helps you turn ideas and experiences into a complete piece, organize your thoughts, and refine a draft while preserving your facts and voice. Use it to write something new, improve an existing text, or find out what needs work.

Version: **0.1.0**. The skill's instructions and examples are primarily Korean. All writing guidance is included in the `humanize-sepia` folder.

## What it does

| Mode | Use |
|---|---|
| `write` | Write a complete draft from your ideas, experiences, or notes. |
| `refactor` | Improve the wording while keeping the content, voice, and order of events. |
| `review` | Point out unclear or weak passages without changing the text. |
| `recreate` | Start again with a new structure when explicitly asked, keeping the facts and intended message. |

The skill starts with what you want to say and who will read it. It chooses relevant details and connects them so the reader can follow your thinking. It then improves the wording and flow while keeping the level of formality appropriate for the piece.

For job application essays, it considers the company and role to understand what the question is trying to assess. A question about a “different perspective” may call for showing what you noticed about a problem and why you chose a particular approach. The essay must also meet the stated length limit, number of examples, and required parts of the question.

It grounds the qualities you want to show in your actual experience. It keeps your actions distinct from other people's approval and the team's results. If essential facts are missing, it asks only what it needs or drafts from the confirmed information, with a note outside the essay explaining what still needs work.

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

작은 가게들이 입점하는 온라인 장터의 운영 담당자로 지원하려고 해.
판매자 문의에 답하고, 판매자들이 겪는 불편을 찾아 개선하는 일이래.
자소서 문항은 “기존 방식과 다르게 접근해 문제를 해결한 경험”이야.

아르바이트하던 매장에서는 직원마다 안내 내용이 달라서 손님이 같은
내용을 다시 묻곤 했어. 자주 들어오는 질문과 답변을 표로 정리했어.
매니저가 확인한 뒤 교대하는 동료들과 함께 사용하기 시작했고,
동료들은 답변을 찾기 편해졌다고 했어. 같은 질문이 얼마나 줄었는지는
따로 세어 보지 않았어.

안내 내용이 제각각이라는 점을 발견하고, 동료들이 함께 참고할 수 있는
표로 정리한 과정을 보여 주고 싶어.
초안에는 “남다른 관찰력으로 혁신적인 개선을 이루었다”고 썼는데,
너무 거창해 보여. 내가 한 일이 잘 드러나도록 자연스럽게 써줘.
공백 포함 500자 이내로, 담담한 말투면 좋겠어.
```

A draft can be a starting point for further writing. The skill keeps useful wording and voice, develops the piece around your intended message, and follows the scope you set. When a missing detail would change the meaning or an important fact, it asks a focused question.

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

You can follow up with a request such as “make only the second paragraph shorter.” The skill uses the latest text, revises the requested passage, and keeps the rest unchanged.

The result starts with the text, followed by brief notes on important changes or facts to confirm. Your requested format takes priority. Check the final text against your actual experience and numbers. AI-detector scores are not a measure of writing quality.

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
