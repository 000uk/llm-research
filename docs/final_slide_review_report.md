# Final Slide Review Report

## 1. Generated Files

- **HTML file:** `/home/user/llm-research/llm_compression_slides_final_reviewed.html`
- **Report file:** `/home/user/llm-research/docs/final_slide_review_report.md`

---

## 2. Final Slide Count

**24 slides** (within 30-slide limit)

| # | Title | Tag |
|---|-------|-----|
| 1 | Title — Qwen3-235B 의존도를 줄이기 위한 LLM 경량화 방법론 조사 | — |
| 2 | 발표 범위: 다루는 것 / 다루지 않는 것 | 발표 범위 |
| 3 | "줄인다"의 의미: 서로 다른 비용 축 | 개념 정리 |
| 4 | 방법론 map: 어느 비용 축을 줄이나 | 전체 map |
| 5 | Quantization — GPTQ/AWQ | Part 1 · 모델 자체 |
| 6 | QLoRA — task adaptation | Part 1 · 모델 자체 |
| 7 | Qwen3 teacher → student: off-policy / on-policy | Part 2 · KD |
| 8 | KD 4가지 + On-policy JSON 예시 | Part 2 · KD |
| 9 | 일반 KD ≠ agent workflow 보존 | Part 2 · Agent KD |
| 10 | Structured Agent Distillation — [REASON]/[ACT] + JSON | Part 2 · Agent KD |
| 11 | Tool schema overhead ≠ tool selection | Part 3 · Tool |
| 12 | Context compression — AgentDiet/ACON | Part 3 · Context |
| 13 | vLLM · SGLang · CacheGen | Part 4 · Runtime |
| 14 | Decoding optimization + token-flow 다이어그램 4종 | Part 4 · Decoding |
| 15 | Output length — generation stability | Part 4 · Generation |
| 16 | Cascade / fallback | Part 5 · System |
| 17 | MoE teacher distillation 비교표 | Part 2 · MoE KD |
| 18 | Teacher 접근 권한별 KD 선택지 요약 | Part 2 · KD 권한 |
| 19 | Domain Bridge ① — User profile / recommender | Part 6 · Domain Bridge |
| 20 | Domain Bridge ② — Workflow decomposition | Part 6 · Domain Bridge |
| 21 | 경량화 평가: quality와 cost 분리 | Part 7 · 평가 |
| 22 | 전체 방법론 비교표 | Part 7 · 비교 |
| 23 | Profile Agent 연결점 + synthetic JSON | Part 7 · 적용 가능성 |
| 24 | Takeaways | Part 7 · 정리 |

---

## 3. Enhanced Slides (vs. polished version)

### Slide 5 — Quantization
- **추가:** 시각적 layered bar 다이어그램 (FP16/INT8/INT4 메모리 비교)
- **추가:** 2열 평가 지표 비교 테이블 (General quality metric vs Agent metric)
- **강화:** PPL 유지 ≠ schema validity ≠ action accuracy 3개 항목으로 분리 명시
- **강화:** calibration 분포 주의 문구 추가

### Slide 6 — QLoRA
- **강화:** "줄이는 것 / 줄이지 않는 것" 구분에 inference call count 구별 명시
- **강화:** 235B 자체는 별도로 존재한다는 명시 추가
- **강화:** cd-row에 adapter merge 단계 추가

### Slide 7 — Qwen3 teacher
- **추가:** off-policy 한계 항목 (train/serve mismatch) 명시
- **강화:** teacher 접근 테이블에 output/logits/router 각 케이스를 더 명확히 기술

### Slide 8 — KD taxonomy
- **추가:** On-policy KD synthetic JSON 예시 (student_output + teacher KL signal)
- **강화:** 테이블과 JSON 예시를 grid-2로 병렬 배치
- **추가:** "이 예시가 보여주는 포인트" json-point 텍스트

### Slide 9 — Agent trajectory KD
- **강화:** before/after 구분에 실패 모드 설명 강화
- **강화:** cd-row에 각 단계 small 설명 텍스트 추가

### Slide 10 — Structured Agent Distillation
- **추가:** [REASON]/[ACT] JSON 예시 (merge action 포함) — 요구사항에 명시된 예시 그대로 반영
- **추가:** "재해석 필요" / "별도 검증 필요" badge 추가
- **강화:** grid-2로 문제정의와 JSON 예시 병렬 배치

### Slide 14 — Decoding optimization
- **추가:** 4종 token-flow 다이어그램 (HTML/CSS, 외부 이미지 없음):
  - Speculative Decoding: Draft → 후보 → Target 병렬 검증 → 수락 prefix
  - Medusa: Backbone hidden → multi-head tree 구조 → tree-based 검증
  - EAGLE: hidden feature → feature predictor → token projection → target 검증
  - Lookahead: n-gram pool → 병렬 실행 → 다수 token 확정
- **추가:** 각 다이어그램에 핵심 문구 (tflow-key)
- **강화:** MTP 주의 문구를 별도 card로 분리

### Slide 15 — Output length
- **추가:** "Even if model is smaller, long context still costs money" 직접 인용
- **강화:** MoE quantization 논문이 EOS_rate를 직접 다루지 않는다는 주의 명시

### Slide 17 — MoE KD
- **추가:** 접근 권한별 선택지 요약 note 카드
- **강화:** "전체를 MoE 구조 설명으로 확장하지 않는다" 명시

### Slide 23 — Profile Agent applicability
- **추가:** synthetic JSON 의사결정 예시 (signal → profile_update → action)
- **추가:** "별도 검증 필요" badge
- **강화:** "확정 설계 아님" 언어를 더 명시적으로 기술
- **추가:** tool-free workflow 재해석 note card 추가

---

## 4. Paper Evidence / arXiv References Verified in Speaker Notes

| 슬라이드 | 근거 논문/문서 |
|---------|--------------|
| Slide 5 | GPTQ (Frantar et al., 2022), AWQ (Lin et al., 2023) |
| Slide 6 | QLoRA (Dettmers et al., 2023) |
| Slide 7 | Qwen3 Technical Report (Qwen Team, 2025) |
| Slide 8 | GKD (Agarwal et al., 2024), Hinton et al. 2015 계열, Preference KD/PLaD |
| Slide 9 | AgentTraj-L (Liu et al., 2024), FireAct (Chen et al., 2023) |
| Slide 10 | Structured Agent Distillation (Lu et al., 2024 계열) |
| Slide 11 | Internalizing Tool Knowledge (Qin et al., 2023 계열), Less is More |
| Slide 12 | AgentDiet (Lu et al., 2024 계열), ACON |
| Slide 13 | vLLM (Kwon et al., 2023 SOSP), SGLang (Zheng et al., 2024), CacheGen (Liu et al., 2024) |
| Slide 14 | Speculative Decoding (Leviathan et al., 2023), Medusa (Cai et al., 2024), EAGLE (Li et al., 2024), Lookahead (Fu et al., 2024) |
| Slide 16 | FrugalGPT (Chen et al., 2023 계열) |
| Slide 17 | Every Expert Matters (Zuo et al., 2022), B-Distill, Sparse MoE Students, MoEKD for Code Models, Qwen3 Technical Report |
| Slide 19 | PURE, RDRec, SLIM, PinnerSage, PinFM, LEADRE |
| Slide 20 | Decomposed Prompting (Khot et al., 2022), PromptChainer (Wu et al., 2022), R³ Prompting |

---

## 5. JSON Examples Added/Enhanced

| 슬라이드 | JSON 예시 유형 | 마킹 |
|---------|--------------|------|
| Slide 8 | On-policy KD 학습 데이터 예시 (student_output + teacher KL signal) | synthetic example |
| Slide 10 | [REASON]/[ACT] 분리 예시 (merge action, target_note_id) | synthetic example |
| Slide 23 | Profile Agent 의사결정 예시 (signal → profile_update → action) | synthetic example |

모든 JSON 예시:
- 8~12줄 이내
- 실제 사용자 데이터 없음 (synthetic)
- "이 예시가 보여주는 포인트" json-point 텍스트 첨부

---

## 6. Token-flow Diagrams Added

모두 HTML/CSS 기반 (외부 이미지 없음, tflow-* CSS 클래스 새로 정의):

| 다이어그램 | 슬라이드 | 핵심 문구 |
|-----------|---------|----------|
| Speculative Decoding | Slide 14 | "Draft가 앞서 쓰고, target이 한 번에 검증" |
| Medusa | Slide 14 | "별도 draft model 대신 다중 decoding head 사용" |
| EAGLE | Slide 14 | "token이 아닌 feature를 예측해 speculative sampling" |
| Lookahead | Slide 14 | "draft model 없이 병렬 decoding" |

추가 시각 요소:
- Slide 5: layered bar (FP16/INT8/INT4 메모리 비율)
- 전체: cd-row 개념 다이어그램 (기존 유지·강화)

---

## 7. "확인 필요" / "별도 검증 필요" 항목

| 슬라이드 | 항목 |
|---------|------|
| Slide 5 | Quantization calibration 분포가 agent prompt·JSON 분포와 다를 경우 |
| Slide 5 | schema validity, action accuracy, p95 latency — PPL과 독립적 측정 필요 |
| Slide 7 | Qwen3 Technical Report 학습 조건이 우리 도메인 분포와 일치하는지 원문 조건에서 확인 |
| Slide 8 | logit 접근 권한 여부 — Logit KD·On-policy KL 가능 여부 확인 먼저 |
| Slide 10 | Profile Agent에서 [ACT] → schema/merge/routing decision 재해석 성능 영향 |
| Slide 11 | tool router recall@K · precision@K 동시 측정 필요 |
| Slide 13 | CacheGen: 긴 shared context 반복 재사용 구조 유무 확인 필요 |
| Slide 14 | MTP: target model native support 확인. Qwen3-235B 즉시 적용 단정 금지 |
| Slide 14 | Medusa/EAGLE: target model 수정 권한 확인 필요 |
| Slide 17 | router/expert 접근 가능성 확인 후 MoE-aware KD 후보 논의 가능 |
| Slide 19/20 | Domain Bridge 사례 → Profile Agent 적용 전 separate verification 필요 |
| Slide 23 | synthetic JSON 예시 — 실제 Profile Agent action 타입 적합성 별도 검증 필요 |
| Slide 23 | tool-free workflow → tool-call ACT 재해석 자체가 별도 검증 항목 |

---

## 8. Speaker Notes Implementation

**토글 방법:**
- 키보드 `N` 키: speaker notes ON/OFF 토글
- 하단 chrome 버튼 "notes" 클릭: 동일 토글
- URL `?notes=1`: 페이지 로드 시 notes 기본 ON

**표시 방식:**
- 화면 모드: `body.notes-visible section.slide.active aside.speaker-notes { display: block; }` — 현재 활성 슬라이드의 notes만 표시
- 위치: 슬라이드 하단, 고정 오버레이 (max-height: 32vh)
- 스타일: 다크 배경 (#0f172a), 스크롤 가능
- Notes ON/OFF 상태 indicator: 우측 하단 고정 (`.notes-status`)
  - OFF: 어두운 반투명 / ON: 파란 배경

**인쇄/PDF:**
- `@media print` 에서 `aside.speaker-notes { display: block; }` — 모든 슬라이드의 notes가 슬라이드 직후 인쇄됨

**Speaker notes 형식 (모든 슬라이드 동일):**
```html
<aside class="speaker-notes">
  <h4>Speaker notes</h4>
  <ul>
    <li><strong>카테고리:</strong> ...</li>
    <li><strong>근거:</strong> ...</li>
    <li><strong>해석:</strong> ...</li>
    <li><strong>Qwen3 연결:</strong> ...</li>
    <li><strong>별도 검증 필요:</strong> ...</li>
  </ul>
</aside>
```

각 슬라이드 notes 포함 항목:
- 카테고리: 논문 기반 방법론 / 도메인 참고 사례 / 시스템 패턴 / serving/runtime / decoding optimization / 우리 workflow로의 해석
- 근거: 논문명 또는 공식 문서
- 해석: presenter를 위한 핵심 설명 (2-5문장)
- Qwen3 연결: Qwen3-235B 관련 연결점
- 별도 검증 필요: 해당되는 슬라이드만

---

## 9. 기술 사항

- 외부 라이브러리 없음 (0개)
- 외부 이미지 링크 없음 (0개)
- 슬라이드 네비게이션 유지: ArrowRight/PageDown/Space (다음), ArrowLeft/PageUp (이전), N (notes), P (print), Home/End
- 16:9 stage 유지 (`min(96vw, calc(96vh * 16/9))`)
- `?slide=N` 또는 `#N` URL deep-link 지원
- 총 슬라이드 수 자동 계산 (`slides.length`)
