# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**A skill for writing and editing Korean from experiences, notes, and drafts.** It helps select relevant material and organize it for your reader while working within your facts and voice. Use it for job applications, business emails, reports, proposals, and research plans.

Version **0.5.2** · Codex / Claude Code · Instructions and examples are primarily Korean. The skill is contained in `skills/humanize-sepia`.

## What you can request

| Task | Example request |
|---|---|
| Write from source material | “Use these notes to write what I want to say.” |
| Edit a draft | “Keep my voice and fix awkward sentences.” |
| Reorganize a piece | “Preserve the facts and intent, and rebuild the flow.” |
| Review without editing | “Identify problem passages and explain why.” |
| Revise through critique | “Check the reasoning and evidence, make needed edits, and verify the result.” |

One skill handles the requested scope. A wording edit does not require multiple drafts or a separate reviewer. Writing and editing end with a check of facts, required answers, and format. Critique-based revision uses one review, edit, and verification pass; further iteration or independent review follows your request.

For job applications, the focus is on what the question is trying to assess, supported by your judgments, actions, and evidence. Company and role information can provide context. Required answers, example counts, and length limits remain writing constraints.

## Writing and editing guidance

- Separate required answers from optional source details. Choose evidence that explains the judgment instead of reproducing every note.
- Distinguish your work from colleagues’ roles, review from approval, plans from execution, and actual use from observed effects.
- Preserve provided thoughts and their timing without inventing motivations, outcomes, or causal claims.
- Distinguish general statements of intent from specific work commitments. Preserve provided plans and present requested new approaches as proposals.
- In research writing, distinguish prior findings, the new question, the stated method, and the limits of the conclusions. Avoid unsupported generalizations about research gaps.
- For wording edits, use the original meaning and voice as the reference. For structural edits, preserve necessary facts and conditions. Technical terms and useful repetition can stay.
- Choose voice and format from your current request, then the original or reference text, then channel defaults. A body-only request excludes separate titles and commentary.

Research guidance focuses on the relationship between questions, evidence, and limitations rather than fixed sentence counts. Version 0.4.3 clarifies the timing of presenting materials and asking questions, and avoids deciding ambiguous timing without evidence. For experience-and-learning questions with no required order, it offers an example that places the lesson at the decision change and ends with a confirmed result. Review guidance distinguishes unsupported role or outcome claims from optional wording suggestions.

Version 0.4.4 adds brief model-specific prompt notes for Gemini 3.8 Flash and Gemini 4 Argon, based on Google's prompt guidance and published model behavior. These notes adjust how instructions are framed; they do not establish improved writing quality.

Version 0.5.x reorganizes the wording-polish guidance (`naturalness.md`). Cues such as empty evaluative words, boilerplate conclusions, translationese, and emotional clichés are used to find places to edit, not as a detector. A fix replaces the filler with a concrete fact from your material or removes only that sentence. The guidance avoids inventing later actions or habits, and it keeps salutations, signatures, bullet items, numbered lists, and intentional marks such as dashes and ellipses. When you ask for body text only, it adds no change notes or requests for more material after the body. It also adds a personal-essay default and notes on channel-specific boilerplate. A rule now states that code blocks, diagrams such as Mermaid, images, tables, and figure captions are not removed or rewritten during polishing. It was added after an issue report; a 54-run reproduction across seven models did not show any diagram being deleted, so its effect is not established.

Version 0.5.2 defines "body only" as no title or commentary while keeping the salutation, signature, and closing you supplied (unless you ask to remove them or fix the paragraphs), because several models were dropping them. The core guidance also tells the model to copy a quoted sentence or block quote unchanged and not to turn it into reported speech, including quotes of rules and clauses. The GPT-6 Luna and Gemini 3.8 Flash notes repeat the quote rule, and the Gemini note adds that "not yet measured" must not become "will be measured".

Application character counts and byte counts are distinct; the destination’s counting rules take priority. Instructions discourage padding with invented facts or empty promises. Exact length checks depend on the tools available in the host.

## Current evidence and limitations

Limited comparisons using fictional cases produced outputs that preserved facts, roles, approval states, and requested formats. **They did not establish better writing than the model without the skill or version 0.4.1.** Version 0.4.2 reduces repeated guidance and input length; it has not established a reduction in the number of cases with redundant summaries. Repetition and abstract wording can remain. Preservation of facts and intent is not guaranteed for every input.

Model-specific writing gains and lower latency are not established features. Expression patterns are editing cues, not evidence of AI authorship or a guarantee of passing a detector. Check the final text against your actual experience, numbers, and conditions.

The 0.5.x wording-polish changes were checked only on a subset of fictional cases (one or two runs per case, judged manually by one person) with Claude Sonnet 5.5, Opus 5.5, GPT-6 Astra, GPT-6.1 Sol, GPT-6 Sol, GPT-6 Luna, and Gemini 3.8 Flash (the model note was selected manually). Invented actions, notes after the body, and deleted salutations, signatures, or items occurred less often in those runs, but this is not a statistical conclusion, and it did not establish better writing than the model without the skill or version 0.4.4. With the GPT models no difference from 0.4.4 was visible, and some models turned direct quotations into reported speech, dropped salutations and signatures, or removed a "not measured" sentence under both 0.4.4 and 0.5.x. Gemini 3.8 Flash showed fewer problems (4 of 12 samples versus 8), but the sample is too small to conclude anything. The Gemini 4 Argon note was not tested. Boilerplate can remain.

For 0.5.2, frozen new cases were compared with 0.5.1 on GPT-6 Astra, GPT-6.1 Sol, GPT-6 Sol, and GPT-6 Luna; Gemini 3.8 Flash was checked separately (below). With a body-only request, dropped salutations and signatures fell from 5 of 27 runs to 1 of 27 on the three GPT models checked (GPT-6.1 Sol: 4 of 9 to 0 of 9; the prompts differed slightly between the two measurements). GPT-6 Luna rarely reads the editing notes; on new cases the share of its runs that changed a quoted sentence fell from 14 of 15 to 3 of 15 (all three were rule or clause quotes; measured before one final clause sentence was added), and quotes of rules and clauses stayed the weakest type (3 of 15 runs on a separate clause-only set). Regression checks on Claude Sonnet 5.5 and Opus 5.5 showed no new problems. On Gemini 3.8 Flash, 48 runs (24 pairs of 0.5.1 and 0.5.2 over 12 cases, two runs each, no manual note selection) showed violating runs falling from 8 of 10 to 0 of 10 for quotes, from 4 of 6 to 0 of 6 for salutations, signatures, and closings, and from 4 of 6 to 0 of 6 for turning "not yet measured" into "will be measured"; a request to remove the salutation was still honored (2 of 2 in both versions). **Limits:** the model-specific notes are read only when the host reports the model name. In a Codex test without it, GPT-6 Luna read none of them, so the core rules carry the fix there; Gemini 3.8 Flash read its note in all 24 skill runs through the agy CLI. The core SKILL.md grew to about 2,500 tokens, roughly 15% above 0.4.4. Samples are small (mostly three runs per case) and the judging was done by one person with scripted checks.

Gemini 4 Neon, Hydrogen, and Carbon (thinking level medium, 57 completed runs over 12 cases) showed no quote, salutation, signature, or "not measured" problems with either 0.5.1 or 0.5.2, so no model notes were added for them. Carbon is only partly covered because a number of its runs timed out. Google's official guides for these models mostly describe API behavior (thinking levels, ignored sampling parameters, output limits) and say little about how to write prompts. In a length test (4 cases, two runs each, 41 completed runs), the skill brought the text within 99-100% of the character limit in 7 of 8 runs on Neon and 3 of 8 on Hydrogen, against 0 of 8 for both without the skill, and no run exceeded the limit. When a memo has few facts the text still comes out shorter, because facts take priority over length. Neon sometimes added lesson sentences that were not in the memo. With the skill, Carbon did not finish within 10 minutes in 5 of 7 runs, so it could not be evaluated.

## Install

### Codex

Ask Codex to install the pinned version:

```text
$skill-installer https://github.com/yeomin4242/humanize-sepia/tree/v0.5.2/skills/humanize-sepia
```

For a manual installation, clone the repository and copy the skill folder:

```bash
git clone --branch v0.5.2 --depth 1 https://github.com/yeomin4242/humanize-sepia.git
mkdir -p ~/.agents/skills
cp -R humanize-sepia/skills/humanize-sepia ~/.agents/skills/
```

For project-local use, place it at `.agents/skills/humanize-sepia` in the project.

### Claude Code

From the same cloned repository, copy the skill to your personal skill directory:

```bash
mkdir -p ~/.claude/skills
cp -R humanize-sepia/skills/humanize-sepia ~/.claude/skills/
```

For project-local use, place it at `.claude/skills/humanize-sepia`.

If personal and project copies share the same name, ask for the actual `SKILL.md` path and version to confirm which copy was loaded.

**When updating, move the existing skill folder to a backup location before replacing it.** Avoid copying a new folder inside an existing installation. If you use both tools, keep both copies on the same version.

## Use

Invoke `$humanize-sepia` in Codex or `/humanize-sepia` in Claude Code and describe what you need. **There is no required input template or order.** Include your reader, direction, question, source material, experience, or draft as needed.

This example uses a fictional experience. In Claude Code, replace the invocation with `/humanize-sepia`.

```text
$humanize-sepia

온라인 장터의 판매자 지원 직무에 지원하려고 해.
문항은 “기존 방식과 다르게 접근해 문제를 해결한 경험”이야.

아르바이트하던 매장에서는 직원마다 안내가 달라 손님이 다시 묻곤 했어.
자주 들어오는 질문과 답변을 표로 정리했고, 매니저가 확인한 뒤
교대 동료들과 함께 사용했어. 동료 두 명은 답변을 찾기 편해졌다고 했어.
문의가 얼마나 줄었는지는 세어 보지 않았어.

동료들이 함께 참고할 기준을 만든 과정을 보여 주고 싶어.
초안의 “혁신적인 개선을 이루었다”는 표현은 너무 거창해 보여.
내가 한 일이 드러나게 담담한 말투로, 공백 포함 500자 이내로 써줘.
```

You can specify a narrow edit or ask for a review:

```text
$humanize-sepia 내용과 말투는 유지하고 두 번째 문단만 짧게 다듬어줘.
숫자와 인용문은 바꾸지 말아줘.
글: …
```

```text
$humanize-sepia 글은 고치지 말고, 독자가 이해하기 어려운 부분을 짚어줘.
실제 오류와 선택적으로 바꿀 부분을 나눠 알려줘.
글: …
```

```text
$humanize-sepia 논리와 근거를 비판적으로 검토하고 필요한 부분을 고쳐줘.
수정 후에는 지적한 문제가 해결됐는지와 사실·조건이 유지됐는지 확인해줘.
글: …
```

Earlier writing or an edit you liked can provide a reference. Explain what you preferred to help choose guidance for the current piece. Installing the skill does not automatically save preferences or edit history. Provide relevant records again when using another conversation.

### Model profiles

Profiles are included for Sonnet 5.5, Opus 5.5, GPT-6.1 Sol, GPT-6 Sol, GPT-6 Luna, and GPT-6 Astra. **When the host provides the exact current model name, the instructions select one matching profile.** Unknown or unlisted models use the shared guidance. This is an instruction-selection rule, not guaranteed automatic detection in every environment.

You can also request a profile explicitly, such as `모델 지침: gpt-6.1-sol`. This does not change the execution model or reasoning effort. Both Sol versions share a profile. To check selection, ask for only the applied profile and the basis for choosing it.

## Repository

The root contains the two READMEs and license. The installable skill is in `skills/humanize-sepia`. `SKILL.md` links shared guidance to task-specific references. `references/` holds writing, editing, review, and channel guidance; `agents/openai.yaml` provides Codex display metadata.

## Inspired by

[Sepia](https://github.com/Nanako0129/sepia) · [humanize-korean](https://github.com/epoko77-ai/im-not-ai) · [stop-slop](https://github.com/hardikpandya/stop-slop) · [no-ai-slop](https://github.com/petergyang/no-ai-slop) · [unslop](https://github.com/cursor/plugins) · [Humanizer](https://github.com/blader/humanizer) · [humanizer-skill](https://github.com/aboudjem/humanizer-skill) · [anti-ai-slop-writing](https://github.com/jalaalrd/anti-ai-slop-writing) · [humanize](https://github.com/aashaexo/soundshuman) · [Slopbeth](https://github.com/ehmo/slopkit) · [Deslop](https://github.com/stephenturner/skills)

## License

[MIT](LICENSE).
