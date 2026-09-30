# 비교 평가 / Evaluation

## 한국어

스킬 없이 쓴 글보다 더 잘 쓴다는 우위는 아직 확인하지 못했다. 기능을 지원한다는 것과 그 기능이 글의 품질을 높인다는 것은 별도로 확인한다.

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
