# Visual Profile Integration Report

## 1. Generated HTML File Path

`/home/user/llm-research/llm_compression_slides_visual_profile.html`

File size: 112,445 bytes

---

## 2. Final Slide Count

**28 slides** (within the 30-slide maximum)

---

## 3. Slides with Visual Redesign Applied

| Slide | Title | Visual Elements Added |
|-------|-------|-----------------------|
| 1 | Title | (existing, kept as-is) |
| 2 | Scope | takeaway-ribbon added |
| 3 | Cost axes | takeaway-ribbon added |
| 4 | Method map | table + takeaway-ribbon |
| 5 | Quantization | memory ladder, flow-card, metric table, warn-ribbon |
| 6 | QLoRA | 3-card structure (줄이는 것/줄이지 않는 것/필요한 것), cd flow diagram, takeaway-ribbon |
| 7 | Qwen3 teacher access | ladder (3 levels: output/logits/router), table, takeaway-ribbon |
| 8 | KD 4가지 | 4-column table + JSON card (on-policy KD example), warn-ribbon |
| 9 | Agent trajectory KD | before/after split, Reason→Act→Observe→Reason flow diagram, takeaway-ribbon |
| 10 | Structured Agent Distillation | card + JSON card (reason/action split), takeaway-ribbon |
| 11 | Tool schema selection | 2 flow-cards (full→selected / internalize), table, warn-ribbon |
| 12 | Context compression | stacked-bar diagram (Step 1/3/10 context growth), 3-card triage, cd diagram |
| 13 | Serving/runtime | 3-column cards (vLLM/SGLang/CacheGen) each with industry-flow, takeaway-ribbon |
| 14 | Decoding optimization | 4 token-flow diagrams (Speculative/Medusa/EAGLE/Lookahead), MTP native badge |
| 15 | Output length | two-col-compare (long vs short), 4 metric-cards dashboard, warn-ribbon |
| 16 | MoE KD | access ladder (3 levels), compact table (5 papers), warn-ribbon |
| 17 | Cascade | cd flow diagram, table, takeaway-ribbon |
| 18 | General vs Agent LLM | two-col-compare, card, takeaway-ribbon |
| 19 | Profile Agent 4-step workflow | profile-pipeline (4 rows with step/function/KD connection columns) |
| 20 | Profile Agent vs Tool-calling | grid-2 cards, risk-map (4 items), takeaway-ribbon |
| 21 | PURE/RDRec/SLIM bridge | bridge-cards with flow diagrams, warn-ribbon |
| 22 | Workflow decomposition | two-col-compare (통합 vs 분리), card with split table, takeaway-ribbon |
| 23 | PinnerSage/PinFM/LEADRE | 3 industry-pattern-cards with mini-tables (4 fields each) |
| 24 | Industry patterns Section C | 5 industry-pattern-cards + note card + warn card, warn-ribbon |
| 25 | Profile Agent applicability | card + JSON card (decision example), note card, takeaway-ribbon |
| 26 | Metric checklist | table, card, takeaway-ribbon |
| 27 | Full comparison table | table, takeaway-ribbon |
| 28 | Takeaways | 3 cards (모델/KD, 시스템/런타임, Profile Agent), takeaway-ribbon |

---

## 4. What Was Added from profile_agent_kd_strategy.html

### New slides entirely from profile_agent_kd_strategy.html:
- **Slide 19**: Profile Agent 4-step workflow — `profile-pipeline` component with Step 1~4 rows showing KD connection possibilities (response KD/input aggregation / preference KD/PLaD / schema-constrained gen / trajectory KD/on-policy KL)
- **Slide 20**: Profile Agent vs Tool-calling Agent risk comparison — `risk-map` component, explicit separation of tool-call accuracy (not direct risk) vs schema validity/merge-decision/evidence preservation/p95 latency (direct risks)
- **Slide 21**: PURE/RDRec/SLIM bridge — `bridge-card` components with HTML/CSS flow diagrams (no original paper figures), one-liner connections, warning about performance number extrapolation
- **Slide 22**: Workflow decomposition tradeoff — `two-col-compare` (One big call vs Decomposed calls), no conclusion that "Step 1~3 should be merged"
- **Slide 23**: PinnerSage/PinFM/LEADRE — `industry-pattern-card` with 4 fields each (핵심 아이디어/줄이는 비용/연결 가능성/외삽 주의점)

### Content integrated into existing slides:
- **Slide 7**: Added off-policy/on-policy Qwen3 Technical Report context from the profile_agent_kd_strategy.html Qwen3 TR section
- **Slide 10**: Added Structured Agent Distillation content from arXiv:2505.13820 (검증됨)
- **Slide 28**: Added Profile Agent takeaway block noting tool-call accuracy distinction and industry patterns as reference only

---

## 5. Section C Industry Patterns Reflected

All 5 industry patterns from Section C of profile_agent_kd_strategy.html are shown in **Slide 24**:

1. **Offline teacher labeling** → Qwen3-235B로 Step별 학습 데이터 또는 rationale offline 생성 검토
2. **Small online student** → online path에 작은 student 또는 rule/schema decision 가능성
3. **Latency-sensitive / latency-tolerant 분리** → 실시간 profile update vs 비동기 profile cleanup/batch review 분리 가능성
4. **Request-level deduplication** → 같은 user context를 반복 처리하지 않고 candidate 비교 단계 재사용
5. **Post-training denoising** → LLM을 profile noise/conflict/expired note 정리에 한정

Evidence sources cited per pattern: Pinterest Search (CIKM 2024), LEADRE (VLDB 2025), Pinterest DCAT, CF Post-training Denoising (arXiv:2601.18009).

Bottom ribbon explicitly labels these as "운영 패턴 참고 자료" not design decisions, with "별도 검증 필요."

---

## 6. Visual Elements from llm_compression_papers.html Used

- **General vs Agent LLM comparison table** (Slide 18): the `diff-table` structure from llm_compression_papers.html overview section was adapted into a `two-col-compare` component. Includes: evaluation criteria, asymmetry of compression impact, KD target, cost structure, format adherence, action space.
- **ACBench numbers** (quantization: 1~3% loss, KD: 70%→43.6% collapse) — placed in **speaker notes only** as instructed, not in slide body.
- **Paper development insight cards** content: reasoning KD ≠ agent KD, quantization safer than KD for tool-use, data design notes — integrated into Slide 18 and speaker notes.
- **5-phase development timeline** concept: reflected in the method map (Slide 4) organized as model → agent workflow → system/runtime layers, labeled as "문제의식의 발전 흐름" concept.

---

## 7. New Diagram/Card/JSON/Token-flow Types Added

| Component | CSS Class | Used In Slides |
|-----------|-----------|----------------|
| Bottom takeaway ribbon | `.takeaway-ribbon`, `.warn-ribbon` | 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28 |
| Metric dashboard cards | `.metric-card` | 15 |
| Flow diagram cards | `.flow-card` | 5, 11 |
| Access level ladder | `.ladder`, `.ladder-step` | 7, 16 |
| Token-flow diagrams | `.tflow`, `.tflow-row`, `.tflow-box` | 14 |
| JSON example cards | `.json-card`, `.json-block` | 8, 10, 25 |
| Compact comparison table | `.mini-table` | 23 |
| Profile pipeline grid | `.profile-pipeline` | 19 |
| Bridge cards with flow | `.bridge-card` | 21 |
| Industry pattern cards | `.industry-pattern-card` | 23, 24 |
| Industry flow mini | `.industry-flow` | 13 |
| Risk mapping grid | `.risk-map` | 20 |
| Two-column compare | `.two-col-compare` | 15, 18, 22 |
| Stacked context bar | `.stacked-bar`, `.sb-row` | 12 |

---

## 8. Speaker Notes Toggle Maintained

**Yes.** All features preserved:
- `N` key toggles speaker notes
- `?notes=1` URL parameter shows notes by default on load
- Notes: ON / Notes: OFF indicator at bottom right
- Print/PDF mode renders notes after each slide
- `ArrowRight` / `PageDown` / `Space` = next slide
- `ArrowLeft` / `PageUp` = previous slide
- `P` key triggers print

---

## 9. Slides That Remain Text-Heavy and Why

| Slide | Reason |
|-------|--------|
| Slide 4 (Method map) | A 6-row summary table is inherently the right format for a taxonomy map. Adding diagrams would reduce clarity. |
| Slide 26 (Metric checklist) | The 4-axis evaluation table is information-dense by design; the table format is appropriate for a checklist reference slide. |
| Slide 27 (Full comparison) | An 8-row comparison table is the correct format for a side-by-side method summary; converting to diagrams would lose the parallel structure. |

All three have `takeaway-ribbon` at the bottom to anchor key messages visually.
