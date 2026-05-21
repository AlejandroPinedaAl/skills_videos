---
name: stat-flip-proof-hook
description: >
  Stat → Reframe → Solution framework. Opens with a real data point, flips its interpretation
  to reframe the viewer's problem, then delivers the solution. Use for B2B, SaaS, agencies,
  consulting, or any business where data credibility drives trust. Most powerful when combined
  with BigQuery data from the business's own metrics or industry benchmarks.
---

# Stat-Flip Proof Hook

## Framework Logic
Numbers stop the scroll. A surprising stat creates cognitive dissonance — the viewer needs to resolve the contradiction. The "flip" reframes the problem in a way that makes the solution obvious. This framework works especially well when the stat comes from the viewer's own industry or situation.

**Unique advantage for SaleADS:** BigQuery provides real business data (ROAS, CPM, active campaigns, budget). Use this data directly as the opening stat — it's more powerful than any industry benchmark.

---

## Structure (15-second version)

```
STAT       0 – 3s
├── One number — specific, credible, slightly shocking
├── Must be true or true-adjacent (don't invent stats)
├── Industry benchmarks, platform averages, or internal data
└── Examples:
    "El 73% de los negocios que hacen publicidad digital no miden su ROAS."
    "Un CPM de $45K en TikTok está consumiendo tu presupuesto sin saberlo."
    "El 80% de los leads no compra en el primer contacto."

FLIP       3 – 8s
├── Reframe the stat — change what it means
├── The flip should feel like a revelation, not an accusation
├── Move from "this is a bad number" to "this means something specific is broken"
└── Examples:
    "No significa que los ads no funcionen. Significa que el creativo está mal."
    "Eso no son leads malos. Es que tu seguimiento no está configurado para convertir."
    "No estás fracasando. Estás optimizando sin datos."

SOLUTION   8 – 13s
├── What specifically fixes the thing the flip identified
├── Product/service as the mechanism
└── Example: "SaleADS lee esos datos y regenera automáticamente el creativo
             que está convirtiendo para negocios como el tuyo."

CTA        13 – 15s
└── Action tied to fixing the specific problem identified
```

---

## Stat Sources (Priority Order)

1. **BigQuery data from the specific business** — most powerful (personalized)
2. **Platform averages** — Meta, TikTok, Google official benchmarks
3. **Industry conversion rates** — specific to their category
4. **General digital marketing benchmarks**

## Using BigQuery Data as Stats
When `consultas_negocio` returns data, extract stats like:
- `total_daily_budget` → "Estás invirtiendo $[X] al día en publicidad..."
- `active_campaigns` / `total_campaigns` → ratio of active vs total
- `completeness_score` → if low, use as the stat
- `meta_campaigns` + `google_campaigns` → cross-platform spread

Example with real data:
```
Stat: "Tienes [X] campañas activas de [Y] que creaste. El [Z]% no está generando."
Flip: "No significa que el canal falle — significa que los creativos necesitan rotación."
Solution: "SaleADS analiza cuáles están convirtiendo y genera nuevas variantes automáticamente."
```

---

## Flip Formulas

| Problem Type | Flip Pattern |
|---|---|
| Bad metric | "No significa [wrong conclusion]. Significa [right diagnosis]." |
| Low conversion | "No es el canal. Es el mensaje." |
| Wasted budget | "No estás pagando demasiado. Estás pagando por lo incorrecto." |
| No results | "No falló el producto. Falló la segmentación." |
| Time waste | "No necesitas más horas. Necesitas un sistema." |

---

## Script Output Template

```
[TITLE]: Stat-Flip – [Business Name] – [Platform] – [Duration]s

STAT (0-Xs): "[number + context]"
SOURCE: [where this stat comes from — be ready to back it up]
VISUAL: [text-heavy frame, bold number on screen]
ON-SCREEN: "[stat as large text]"

FLIP (X-Xs): "[reframe — what it really means]"
VISUAL: [cut to problem-symptom visual]
ON-SCREEN: "[reframe phrase]"

SOLUTION (X-Xs): "[mechanism that fixes the real problem]"
VISUAL: [product/dashboard/result]
ON-SCREEN: "[solution claim]"

CTA (X-Xs): "[action tied to the insight]"
ON-SCREEN: [CTA text]
BUTTON: "[button copy]"
```
