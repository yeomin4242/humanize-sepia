# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**Write clear, natural Korean that says what you mean.** Humanize Sepia helps you turn ideas and experiences into a complete piece, organize your thoughts, and refine a draft while preserving your facts and voice. Use it to write something new, improve an existing text, or find out what needs work.

Version: **0.3.1**. The skill works in Codex and Claude Code. Its instructions and examples are primarily Korean. All writing guidance is included in the `humanize-sepia` folder.

## What it does

| What you need | Example request |
|---|---|
| A complete piece from your material | “Use this experience and draft to write what I want to say.” |
| An edited draft | “Keep my voice and improve only the wording,” or “reorganize the piece.” |
| Feedback without edits | “Explain what needs work and why, without changing the text.” |
| Improvement through critique | “Check the reasoning and evidence, revise what needs work, and verify the result.” |

Use `$humanize-sepia` in Codex or `/humanize-sepia` in Claude Code and describe what you need. One skill handles the requested result and editing scope. You can also ask it to write a piece and then examine it critically. A light wording edit does not trigger repeated critique. Ordinary writing, editing, and review use a compact shared guide. Detailed references are read when needed for difficult prompt interpretation or content selection, repeated improvement, or comparing alternatives. The skill does not load every reference or generate multiple drafts by default.

The skill starts with what the reader should understand and chooses material that explains it. Rather than listing activities, it connects the problem, your actions, and what you learned. When you request alternatives or need to choose between different judgments or lessons, it writes complete versions and compares what each conveys. Changes in wording or order alone do not count as a new perspective. If an explanation is weak or important content is scattered, it writes a coherent new version using the relevant evidence. It compares actual alternatives before accepting a change and keeps the earlier text when rewriting does not help. Reference examples illustrate these choices; they are not validated answers or evidence of your preferences.

For job application essays, it considers the company and role to understand what the question is trying to assess. A question about a “different perspective” may call for showing what you noticed about a problem and why you chose a particular approach. The essay must also meet the stated length limit, number of examples, and required parts of the question.

It grounds the qualities you want to show in your actual experience. It keeps your actions distinct from other people's approval and the team's results. If essential facts are missing, it asks a focused question or drafts from confirmed information. It can also ask about a decision that would make your account more meaningful, such as why you chose an approach. Requests to write immediately or return only the text take priority, and questions stay outside the essay.

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

## Install for Claude Code

Claude Code loads personal skills from `~/.claude/skills/`. Clone the repository and copy the skill to invoke it as `/humanize-sepia`. Move any existing installation to a backup location first.

```bash
git clone https://github.com/yeomin4242/humanize-sepia.git
mkdir -p ~/.claude/skills
cp -R humanize-sepia/skills/humanize-sepia ~/.claude/skills/
```

For project-local use, place it at `.claude/skills/humanize-sepia`. If you use both tools, update both installed copies to the same version.

## Use

Invoke `$humanize-sepia` in Codex or `/humanize-sepia` in Claude Code and describe what you want to write. Share the message, audience, and tone you have in mind, along with any experiences, notes, or draft you want to use. You can write naturally, without a fixed template. “쓰고자 하는 방향” (“what I want to write”) is an optional label.

The company and experience below are fictional examples. In Claude Code, replace `$humanize-sepia` with `/humanize-sepia` in the examples.

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

A draft can be a starting point for further writing. The skill keeps useful wording and voice, develops the piece around your intended message, and follows the scope you set. To explore your material first, ask it to start with one question that would help explain your judgment.


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

### Automatic model guidance

When the host exposes the exact current model name, the skill reads **one matching profile**. It does not load every model profile.

| Current model | Additional guidance |
|---|---|
| Claude Sonnet 5.5 | Finish the requested scope and avoid unrequested additions |
| Claude Opus 5.5 | Separate material from instructions and retain settled decisions in follow-ups |
| GPT-6.1 Sol | Keep instructions concise and follow the requested output format |
| GPT-6 Astra | Limit unnecessary questions, formatting, and extra reviews |

If the exact name is unavailable or unsupported, the skill uses its common instructions. It does not infer the running model from saved defaults, which can differ from the active model. Each invocation selects guidance using the model identity available at that time.

When the host does not expose the model, add `모델 지침: gpt-6.1-sol` to your request to select guidance manually. This does not switch the actual model or reasoning effort. To check the selection, ask which profile was applied and whether it came from the host, a manual choice, or the common fallback.

The profiles adapt official guidance from [OpenAI for GPT-6](https://developers.openai.com/api/docs/guides/latest-model) and Anthropic for [Sonnet 5.5](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-sonnet-5-5) and [Opus 5.5](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-opus-5-5). OpenAI presents behaviors observed with Astra as a starting point across GPT-6; these are not established Sol-specific writing traits. The profiles do not guarantee better prose or lower latency.

### Faster one-off requests

For a single ordinary draft, wording edit, or review, paste the prompt for your model and your material **in one message**, without invoking the skill. Use the skill for iterative critique, comparing alternatives, or maintaining writing preferences.

**Codex/GPT:** a compact instruction followed by free-form material.

```text
이번 요청에 스킬 파일은 읽지 말고 제공한 자료로 한국어 글을 작성·수정·검토해줘. 요청한 범위와 형식, 문항의 취지·필수 항목·분량을 지켜. 경험은 판단·행동·확인된 근거로 연결하고 역할·시점·수치·개인/팀 성과를 구분해. 없는 사실·동기·인과를 만들지 말고, 성과를 주장하지 않으면 미측정 사실도 본문에서 생략해. 말투를 살리되 반복과 막연한 역량 선언을 줄여. 검토만 요청했다면 고치지 말고 실제 문제와 선택 제안을 구분해. 초안의 당시 생각은 별도 메모에 없다는 이유만으로 오류로 단정하지 마. 핵심 답이 달라질 때만 묻고 가능하면 결과물부터 보여줘.

[여기에 문항, 메모, 초안 등 쓰고 싶은 내용을 자유롭게 입력]
```

**Claude Code/Claude:** specify the deliverable and scope, and delimit longer source material.

```text
이번에는 한국어 글 한 편을 작성하거나 요청한 범위만 다듬어줘. 내가 원하는 결과와 수정 범위를 먼저 파악하고, 자기소개서라면 문항이 실제로 확인하려는 내용을 경험의 판단·행동·근거로 보여줘. 명시된 답변·사례 수·분량을 지키고, 확인되지 않은 동기·행동·성과를 만들지 마. 성과를 주장하지 않으면 미측정 사실은 본문에서 생략해. 역할·수치·시점과 개인·팀의 기여를 구분해. 말투는 살리고 반복과 막연한 역량 선언을 줄여줘. 검토만 요청했다면 글을 고치지 말고 실제 문제와 선택 가능한 제안을 구분해. 원자료가 초안의 사실을 반박할 때만 오류로 단정하고, 원자료에 빠진 당시 생각은 확인할 내용으로 다뤄. 본문만 요청했다면 글자 수·해설 없이 본문만 보여줘.

<자료>
[문항, 기업 정보, 경험 메모, 초안, 원하는 방향을 자유롭게 입력]
</자료>
```

These are starting points based on [OpenAI's GPT-6 prompting guidance](https://developers.openai.com/api/docs/guides/latest-model) and [Anthropic's Claude prompting guidance](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices). They are not a claim that either model writes better.

## Use edits you liked

Share an edit you accepted or a piece you like, along with what made it work for you. An expression you rejected alongside the version you accepted can help show what to emphasize or leave out. The skill turns the actual change and your reason into a few brief criteria relevant to the current piece. For example, you might prefer showing what you changed before naming a personal strength. When useful, it consults one relevant passage. Facts and experiences from reference pieces stay separate from the new material.

Ask it to summarize an accepted edit and your reason if you want to use them again. The record covers the audience and purpose, a writing criterion, the passage and reason supporting it, and when it applies. Specify a location if you want a file. For later writing, it uses the relevant criteria without reprocessing your entire history.

You can use the skill without reference writing. Your current request takes priority over past preferences. To reuse choices in another conversation, provide the record file or relevant content again. Installing the skill does not automatically save editing history or learn your preferences. Matching your voice and making the content persuasive are checked separately.

## Improve through critique

Ask for an adversarial pass when you want an existing text examined and improved. The skill reads as a skeptical reader: does the text answer the question, do the actions and evidence support its claims, and do the explanations hold together? It starts with the passages where changes would help most, writes actual deletions, combinations, or replacement sentences, and compares them with the original. It then checks whether the revision resolved the identified issues.

```text
$humanize-sepia 아래 글을 독자의 입장에서 비판적으로 검토하고 고쳐줘.
내가 전하려는 말이 잘 드러나는지, 주장에 근거가 충분한지,
앞뒤 설명이 어긋나지 않는지 먼저 살펴봐.
수정한 뒤 지적한 문제가 해결됐는지 다시 확인해줘.
사실과 말투는 유지해줘.
글: …
```

It checks whether a criticism is valid before applying it. For example, feedback that “the result needs numbers” is checked against what the question actually requires. If a confirmed response from colleagues is sufficient, it uses that evidence rather than inventing an unmeasured result.

You can include feedback you have already received. The skill connects it to a particular passage, the reader's difficulty, and an actual revision. Broad comments such as “make it more impressive” do not justify rewriting the whole piece. Even a text without factual errors can benefit from clearer emphasis or connections; the skill can compare an alternative and retain the original when the change does not help. A request for review alone returns feedback without edits, distinguishing problems from optional suggestions.

When you allow changes to the structure, it can compare the judgments or lessons the same material supports. If there is a passage to improve, it writes an alternative before deciding whether to keep the original. Factual accuracy alone does not turn an improvement request into feedback without revision. It uses the relevant evidence to develop one coherent point. Wording-only edits stay within the requested scope. If you ask to see two alternatives, it returns both rather than merging them into one.

If the environment supports a separate reviewer, you can ask for a reader's critique in a fresh context. The reviewer receives the request, source material, and draft rather than the writer's self-assessment. Reviewing in the same context and simulating a reader with AI are distinguished from an actual reader's evaluation.

After revision, it checks both whether the identified problem is resolved and whether important content, facts, and voice remain intact. It accepts useful changes, repairs individual changes that went wrong, and returns to the previous verified draft if the piece became worse overall.

The default is one critique, revision, and verification pass. It repeats only when a significant, fixable problem remains, with up to three revision passes unless you request otherwise. Good text can stay unchanged. If progress stops or an essential fact needs your input, it explains the gap and stops. Neither the number of passes nor a higher self-assigned score establishes writing quality.

The result starts with the text, followed by brief notes on important changes or facts to confirm. Your requested format takes priority. Check the final text against your actual experience and numbers. AI-detector scores are not a measure of writing quality.

## Repository

```text
skills/humanize-sepia/
  SKILL.md
  agents/openai.yaml
  references/
    editing.md
    drafting.md
    candidates.md
    writing-examples.md
    preferences.md
    applications.md
    improving.md
    models/
      claude-sonnet-5-5.md
      claude-opus-5-5.md
      gpt-6.1-sol.md
      gpt-6-astra.md
  LICENSE
README.md
README.ko.md
LICENSE
```

## Inspired by

[Sepia](https://github.com/Nanako0129/sepia) · [humanize-korean](https://github.com/epoko77-ai/im-not-ai)

## License

[MIT](LICENSE).
