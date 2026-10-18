# Humanize Sepia

[English](README.md) · [한국어](README.ko.md)

**A skill for writing and editing Korean from experiences, notes, and drafts.** It helps select relevant material and organize it for your reader while working within your facts and voice. Use it for job applications, business emails, reports, proposals, and research plans.

Version **0.4.1** · Codex / Claude Code · Instructions and examples are primarily Korean. The skill is contained in `skills/humanize-sepia`.

## What you can request

| Task | Example request |
|---|---|
| Write from source material | “Use these notes to write what I want to say.” |
| Edit a draft | “Keep my voice and fix awkward sentences.” |
| Reorganize a piece | “Preserve the facts and intent, and rebuild the flow.” |
| Review without editing | “Identify problem passages and explain why.” |
| Revise through critique | “Check the reasoning and evidence, make needed edits, and verify the result.” |

One skill handles the requested scope. A wording edit does not require multiple drafts or a separate reviewer. For drafting and restructuring, the instructions call for one revision pass after the draft; further iteration or independent review follows your request.

For job applications, the focus is on what the question is trying to assess, supported by your judgments, actions, and evidence. Company and role information can provide context. Required answers, example counts, and length limits remain writing constraints.

## Writing and editing guidance

- Separate required answers from optional source details. Choose evidence that explains the judgment instead of reproducing every note.
- Distinguish your work from colleagues’ roles, review from approval, plans from execution, and actual use from observed effects.
- Preserve provided thoughts and their timing without inventing motivations, outcomes, or causal claims.
- In research writing, distinguish prior findings, the new question, the stated method, and the limits of the conclusions. Avoid unsupported generalizations about research gaps.
- For wording edits, use the original meaning and voice as the reference. For structural edits, preserve necessary facts and conditions. Technical terms and useful repetition can stay.
- Choose voice and format from your current request, then the original or reference text, then channel defaults. A body-only request excludes separate titles and commentary.

Application character counts and byte counts are distinct; the destination’s counting rules take priority. Instructions discourage padding with invented facts or empty promises. Exact length checks depend on the tools available in the host.

## Current evidence and limitations

Limited comparisons using fictional cases produced outputs that preserved facts, roles, approval states, and requested formats. **They did not establish better writing than the model without the skill or version 0.3.3.** Repetition and abstract wording can remain. Preservation of facts and intent is not guaranteed for every input.

Model-specific writing gains and lower latency are not established features. Expression patterns are editing cues, not evidence of AI authorship or a guarantee of passing a detector. Check the final text against your actual experience, numbers, and conditions.

## Install

### Codex

Ask Codex to install the pinned version:

```text
$skill-installer https://github.com/yeomin4242/humanize-sepia/tree/v0.4.1/skills/humanize-sepia
```

For a manual installation, clone the repository and copy the skill folder:

```bash
git clone --branch v0.4.1 --depth 1 https://github.com/yeomin4242/humanize-sepia.git
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
