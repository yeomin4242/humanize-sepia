# 비교 평가 / Evaluation

## 한국어

스킬 없이 쓴 글보다 더 잘 쓴다는 우위는 아직 확인하지 못했다. 기능을 지원한다는 것과 그 기능이 글의 품질을 높인다는 것은 별도로 확인한다.

### Astra low 실행 시간 재측정 — 2026-09-30

0.2.1 설치본을 고정하고 기존 속도 비교에 쓰지 않은 6개 사례(작문 3·검토 2·윤문 1)를 `gpt-6-astra` low에서 조건별 두 번씩 새 문맥으로 실행했다. CLI 호출의 벽시계 시간 중앙값은 일반 스킬 파일 읽기 **24.69초**, 동일한 전체 지침의 첫 메시지 제공 **13.06초**, README의 빠른 요청문 **13.51초**였다. 같은 사례·반복 번호에서 두 직접 제공 방식은 각각 **12/12회** 일반 스킬보다 빨랐다. 누적 입력은 차례로 460,976·185,270·169,694토큰이었고 파일 읽기는 12·0·0회였다. 전체 지침 직접 제공과 짧은 요청문 사이의 속도 우위는 확인되지 않았다.

세 조건 모두 12/12회 분량을 지키고 구체적인 행동·성과를 지어내지 않았다. 다만 자료가 부족한 고객 불편 작문 C03에서 필요한 추가 확인사항을 본문 밖에 적은 비율은 일반 스킬과 빠른 요청문이 각각 1/2, 전체 지침 직접 제공이 0/2였다. 이 품질 약점과 소수 사례·캐시·동시 실행의 영향을 감안해야 한다. 결과는 **도구 읽기 없는 경로의 이 CLI 환경에서의 시간 차이**이며, 표준 `$humanize-sepia` 호출이나 실제 앱의 보편적인 속도 개선을 뜻하지 않는다.

### 0.2.1 실행 시간 점검 — 2026-09-30

같은 0.2.0 지침을 읽는 조건에서 `gpt-6-astra` low와 `gpt-5.6-luna` low를 작문 4건·검토 1건·윤문 1건으로 비교했다. `gpt-6-luna`는 이 계정의 Codex CLI에서 지원되지 않아 실제 비교에 쓰지 못했다. 중앙값은 Astra 27.40초, Luna 18.85초였지만 Luna의 복잡한 자소서 2건에는 자료에 없는 **이후의 습관**과 **점포 방문·점주의 말을 들은 행동**이 각각 들어갔다. 단순 윤문 한 건의 시간은 14.34초와 14.17초로 비슷했다. 따라서 빠른 모델을 작문 전체의 기본값으로 바꾸지 않았다. 검토 한 건의 속도 차이만으로도 모델별 품질·속도 우위를 일반화하지 않는다.

다음으로 `gpt-6-astra` low에서 동일한 지침과 사례 4건을 비교했다. 일반 스킬처럼 `SKILL.md`를 도구로 읽은 조건은 파일 읽기 4회, 실행 시간 중앙값 21.04초, 누적 입력 137,566토큰이었다. 전체 지침을 첫 메시지에 직접 넣은 조건은 파일 읽기 없이 15.29초, 61,714토큰이었다. 이어서 일회성 작업용으로 줄인 최종 요청문은 같은 4건에서 15.30초, 56,630토큰이었다. 세 조건 모두 지정 분량·형식과 확인 가능한 사실을 지켰고, 수동 점검에서 뚜렷한 품질 차이는 없었다. 짧은 요청문의 초기판에서 근거 없는 대비 표현을 발견해 수정했다. 최종판은 복잡한 작문 2건에서도 조건을 지켰지만 개발 중 본 사례라 독립 평가로 세지 않는다. 설치된 스킬 발견을 켠 별도 CLI 확인 1건에서도 최종 요청문은 파일 읽기 없이 끝났다.

이 결과에 따라 [README의 빠른 1회 요청](README.ko.md#빠른-1회-요청)을 선택지로 추가했다. 이는 **스킬을 호출하지 않고** 핵심 기준을 직접 제공하는 방식이다. 일반 `$humanize-sepia` 호출의 실행 시간이 개선됐다는 뜻은 아니다. 각 조건을 사례당 한 번 실행했고 캐시·출력량도 달라, 시간·토큰 수치는 이 CLI 환경의 예비 관찰로만 해석한다. 0.2.1의 스킬 본문은 버전 번호 외에 바꾸지 않았다.

### 기본 지침의 입력량·시간 점검 — 2026-09-30

기본 `SKILL.md`를 3,515바이트에서 2,825바이트로 줄였다(19.6%). 일상 작업의 핵심 기준과 일곱 참고 자료의 조건부 경로는 유지했다. 작문 2건·검토 1건·표현 윤문 1건에서 수정 전·후 지침을 같은 모델(`gpt-6-astra`, low), 같은 도구 읽기 방식으로 각각 한 번씩 실행했다. 네 사례 모두 스킬 파일을 한 번 읽고 추가 자료는 읽지 않았다.

두 조건의 결과는 모두 지정 분량·출력 형식과 확인 가능한 사실을 지켰다. 작문·검토 결과의 실질적 품질 우위는 판별되지 않았고, 윤문 결과는 동일했다. 이는 소수 사례의 수동 점검이며 독립된 독자 선호 평가가 아니다. 누적 입력은 156,158→155,310토큰으로 848토큰(0.54%) 줄었다. 총 실행 시간은 117.05→101.88초였지만 중앙값은 26.75→27.68초였다. 캐시 입력량도 조건 간 달랐다. 따라서 시간이나 실제 청구 비용이 줄었다고 결론내릴 수 없다. 앞선 스킬 없음·스킬 사용 비교에서 확인된 도구 호출 비용은 이 축약으로 제거되지 않는다.

### 0.2.0 반영 점검 — 2026-09-29

같은 모델(gpt-6-astra, low)로 새 가상 사례 6건을 스킬 없음·수정 전·개선본에서 각각 한 번 작성했다. 자유 입력 4건과 가상 선호 조건 2건이며, 실제 사람의 채택 자료는 사용하지 않았다. 과제별 보조 기준은 생성 전에 고정했고 익명 AI 판정은 두 순서로 수행했다.

| 비교 | 개선본 우위 | 상대 우위 | 동률 | 비교 제외 |
| --- | ---: | ---: | ---: | ---: |
| 개선본 vs 수정 전 | 0 | 0 | 6 | 0 |
| 개선본 vs 스킬 없음 | 0 | 0 | 5 | 1 |

스킬 없는 한 본문에는 자료에 없는 시선 이동 행동이 추가됐다는 지적이 있어 품질 비교에서 제외했다. 사실 보존의 차이를 작문 승리로 세지 않았다. 기존 가상 예시 한 쌍을 추가로 제공한 두 사례도 예시 없는 개선본과 동률이었다. 작성 기준 정리 시험에서는 수정 전과 개선본 모두 두 글의 목적을 구분해 300자 이내로 기록했다.

본문 18개와 예시 제공 본문 2개, 기준 기록 2개는 모두 분량·출력 조건을 지켰다. 일반 작성의 평균 누적 입력은 수정 전 31,078에서 개선본 33,837로 8.9% 늘었고, 평균 시간은 18.3초에서 20.0초였다. 한 개선본 실행의 누적 입력이 다른 실행보다 높았으며 이를 제외하지 않았다. 기본 지침은 1,556자에서 1,630자로 늘었다. 문서 크기와 누적 입력은 서로 다른 측정값이다.

이 점검으로 작문 우위나 비용 절감은 확인하지 못했다. 작성 기준 활용과 기록 기능, 평가 절차를 반영한 결과이며 보편적 성능 향상을 주장하지 않는다.

### 비교 조건

- 경험과 초안을 자유롭게 적은 요청, 정리된 요청, 수정 범위가 제한된 요청을 포함한다. 같은 경험을 두 입력 형태로 시험해도 독립 사례 두 개로 세지 않는다.
- 같은 모델·설정·원자료·선호 자료·출력 조건으로 스킬 없음, 이전 버전, 개선안을 새 문맥에서 비교한다. 유효한 글을 다시 생성해 유리한 결과만 고르지 않는다.
- 출력이나 후보 지침을 보기 전에 요청과 자료로 과제별 기준을 정한다. 공통 기준과 함께 사용하며 특정 표현·문단 구조를 정답으로 강제하지 않는다.
- 사실과 명시 조건을 먼저 검사하고, 글의 전달력과 자연스러움은 따로 비교한다. 사실·조건에 중대한 문제가 있는 쌍은 품질 우위 집계에서 제외한다.
- 방법 이름과 작성 과정을 숨겨 비교한다. 순서 교환은 위치 영향을 확인하는 수단이며, 같은 글의 반복 판정을 새로운 사례로 세지 않는다.

### 수정 취향과 예시

실제 채택한 수정과 이유를 사용하면 출처와 적용 범위를 남긴다. 모델이 만든 예시나 가상의 선호를 실제 사람의 선택으로 보고하지 않는다. 말투가 취향에 가까워진 것과 글 전체의 설득력이 좋아진 것을 구분한다.

예시의 추가 효과를 보려면 예시 없음, 관련 가상 예시 한 쌍, 실제 선택에서 뽑은 작성 기준을 따로 비교한다. 실제 선택 자료가 없는 조건은 실행하지 않으며 가상 자료로 대신한 경우에는 기능 시험으로 표시한다. 모든 조건에 동등한 사실·선호 정보를 제공해 추가 정보의 효과를 스킬의 작문 능력으로 세지 않는다.

실제 선택 자료가 확보되면 문단쌍과 적절한 동률쌍으로 AI 판정과 사람 판단의 일치 여부를 확인한다. 그 검증 전의 AI 판정은 예비 관찰로 표시한다. 인위적으로 넣은 사실 오류를 찾는 검사는 사실 검사 능력을 확인할 뿐 사람의 작문 선호를 검증하지 않는다. 평가 기준은 글을 생성한 뒤 바꿔 이전 결과를 승리로 다시 세지 않는다.

### 작성 비용

일반 작성은 한 번 생성하는 조건부터 비교한다. 기준 정리·갱신, 추가 후보 생성·검토, 판정 비용은 따로 기록한다. 호출 수가 같아도 입력량과 작성 시간이 같다는 뜻은 아니다.

입력·캐시 입력·출력·시간·자료 읽기 횟수를 함께 기록한다. 도구 사용 후 다시 전송되는 문맥을 포함한 누적 입력은 스킬 문서 자체의 크기와 다르다. 작은 표본의 시간이나 캐시 차이로 일반적인 속도·청구 금액 절감을 주장하지 않는다.

### 결과 해석

소수의 가상 사례와 AI 판정은 기능 점검과 다음 실험의 근거로 사용한다. 보편적인 작문 우위, 실제 사용자 취향 학습, 사람 평가의 승률로 확대하지 않는다. 차이가 작으면 동률을 허용하고, 어떤 입력과 목적에서 무엇이 나아졌는지와 추가 비용을 함께 기록한다.

## English

A writing-quality advantage over using no skill has not been established. Supporting a behavior and improving the final writing are separate claims.

### Astra low latency recheck — 2026-09-30

The installed 0.2.1 skill was frozen and six cases outside the earlier speed comparison (three drafts, two reviews, one light edit) were run twice per condition in fresh contexts with `gpt-6-astra` at low reasoning effort. Median end-to-end CLI time was **24.69 seconds** for reading `SKILL.md`, **13.06 seconds** for supplying the same full instructions in the first message, and **13.51 seconds** for the README one-off prompt. Both direct-delivery paths beat the skill read in **12/12 matched runs**. Cumulative input was 460,976, 185,270, and 169,694 tokens respectively; file reads were 12, 0, and 0. The shorter prompt did not establish a speed advantage over directly supplying the full instructions.

All conditions met the length bounds in 12/12 runs and avoided inventing specific actions or outcomes. In the under-specified customer-complaint case C03, however, a needed follow-up fact was noted outside the draft in only 1/2 skill runs, 1/2 one-off runs, and 0/2 full-inline runs. This quality gap and the small sample, cache variation, and concurrent execution limit the finding. The result measures these CLI delivery paths, not a speedup of standard `$humanize-sepia` invocation or a universal app latency claim.

### 0.2.1 latency check — 2026-09-30

With the same 0.2.0 skill, six cases (four drafts, one review, one light edit) compared `gpt-6-astra` low with `gpt-5.6-luna` low. This account's Codex CLI rejected `gpt-6-luna`, so it was not part of the comparison. Median elapsed time was 27.40 seconds for Astra and 18.85 seconds for Luna. However, Luna introduced an unprovided later habit in one complex application essay and an unprovided store visit and conversation in another. The light edit took 14.34 versus 14.17 seconds. We did not switch the default writing model. One faster review does not establish a general model advantage.

Four matched cases then compared three delivery paths with `gpt-6-astra` low. Reading the complete `SKILL.md` via a tool took a median 21.04 seconds and 137,566 cumulative input tokens, including four file reads. Placing the same full instructions in the first message took 15.29 seconds and 61,714 tokens without file reads. The final shorter one-off prompt took 15.30 seconds and 56,630 tokens. Every output met the stated length, format, and factual constraints; manual inspection found no material quality difference. An unsupported contrast in an early short-prompt draft prompted a wording change. The final prompt also met the criteria on two complex writing cases, though these were seen during development and are not independent reader evaluations. One additional CLI check with installed-skill discovery enabled completed without a file read.

The [one-off prompt](README.md#faster-one-off-requests) is optional and **does not invoke the skill**. Standard `$humanize-sepia` latency was not improved. Each condition ran once per case; cache use and output length also varied, so these are preliminary observations in this CLI environment. The 0.2.1 skill body is unchanged apart from its version number.

### Entry instruction cost check — 2026-09-30

The entry `SKILL.md` was shortened from 3,515 to 2,825 bytes (19.6%), retaining the core guidance and conditional routes to all seven references. Two drafting cases, one review, and one light edit were each run once before and after the change with the same model (`gpt-6-astra`, low) and the same tool-read procedure. Every run read its entry file once and no reference files.

All outputs met the stated length, format, and factual constraints. No material writing-quality difference was established in the drafting or review pairs; the edit outputs were identical. This was a small manual check, not an independent reader-preference study. Cumulative input fell from 156,158 to 155,310 tokens (848 tokens, 0.54%). Total elapsed time fell from 117.05 to 101.88 seconds, while median time rose from 26.75 to 27.68 seconds. Cached input differed across conditions. These results do not establish lower latency or billed cost. Shortening the file does not remove the tool-read overhead seen in earlier no-skill comparisons.

### 0.2.0 update check — 2026-09-29

Six new fictional cases were generated once per condition using gpt-6-astra at low effort: no skill, before the update, and after the update. Four cases used free-form inputs and two contained explicitly fictional preferences. Input-only task criteria were frozen before generation. Blind AI comparisons were performed in both presentation orders.

The updated skill tied with the previous version in all six cases. Against no skill, five cases tied and one was excluded because an unsupported gaze-shifting action was added to the essay. This preservation difference was not counted as a writing-quality win. Supplying one relevant fictional example pair on two reused cases also produced ties. Both versions summarized a fictional preference record within 300 characters while keeping the two writing purposes separate.

All 18 main texts, two example-assisted texts, and two preference records met their length and output constraints. Mean cumulative generation input increased from 31,078 to 33,837 tokens (+8.9%); mean elapsed time increased from 18.3 to 20.0 seconds. One updated run had higher cumulative input and was retained. The entrypoint grew from 1,556 to 1,630 characters. These observations establish neither a quality advantage nor a cost reduction. Actual human-choice testing and judge agreement with human preferences were not evaluated.

Compare free-form and organized requests, including edits with a limited scope. Give every condition the same facts, preference information, output constraints, model, and settings in fresh contexts. Freeze task-specific criteria from the request before seeing outputs or candidate instructions, retain common criteria, and allow different good structures. Keep valid generations rather than rerunning them to select favorable results.

Check facts and explicit constraints separately from communication quality. Exclude pairs with material fact or constraint failures from quality-win counts. Hide method names and writing processes. Reverse presentation order, but do not count repeated judgments or two input forms of the same experience as independent cases.

Distinguish actual accepted edits from fictional preferences and model-generated examples. Compare relevant examples and short preference criteria with an example-free condition only when equivalent information is available. Do not substitute synthetic fixtures for missing human choices. Matching a preferred voice does not establish greater persuasiveness. When human-choice data is available, check AI judgments against those choices and appropriate ties. Until then, label AI judgments as preliminary observations. Detecting planted factual errors is a different test.

Start with one generation per ordinary writing task. Report preference preparation and updates, additional drafting or review, and evaluation costs separately. Record cumulative input, cached input, output, elapsed time, and reference reads. Equal call counts do not imply equal cost, and cumulative input after tool calls is not the size of the skill text. Small fictional samples and AI judgments support limited observations, not universal quality, latency, or billing claims.
