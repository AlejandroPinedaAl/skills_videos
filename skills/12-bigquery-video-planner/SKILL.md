---
name: bigquery-video-planner
description: >
  Master orchestrator skill. Reads business data from BigQuery via consultas_negocio tool,
  classifies the business, maps it to the correct video skill stack, and orchestrates the
  full Video Ad Plan output. Always runs FIRST. All other skills are invoked through this one.
  This is the integration layer between real business data and creative strategy.
---

# BigQuery-to-Video Planner — Master Orchestrator

## Purpose
This skill is the brain of the entire Video Ad Plan system. It takes raw business data from BigQuery and makes all the creative decisions: which frameworks to use, which platforms to prioritize, which hooks are most relevant, and what CTA matches the business's funnel stage.

---

## Step 1 — Read Business Data

Call `consultas_negocio` immediately. Extract and classify:

```
REQUIRED FIELDS:
├── business_name           → name all outputs
├── industry                → determines category approach
├── value_proposition       → core hook material
├── products_services       → determines product vs service classification
├── target_audience         → personalizes all copy
├── brand_voice             → determines tone (formal/casual/energetic)
├── brand_personality       → determines visual style
├── marketing_goals         → determines funnel stage
├── meta_connected          → triggers Meta platform adaptations
├── google_campaigns        → triggers Google platform adaptations
├── active_campaigns        → context for stat-flip hooks
├── total_daily_budget      → context for financial stat hooks
└── completeness_score      → determines how much we can personalize
```

---

## Step 2 — Business Classification

### Type A: Physical Product
**Signals:** products_services describes tangible items, shipment, inventory
**Primary frameworks:** BAB Transformation, UGC Testimonial, Hook Matrix (Product Hero format)
**Hook priority:** Transformation > Pain Point > Social Proof
**Platform priority:** Meta (visual formats) > TikTok (UGC) > Google Shopping

### Type B: Service Business
**Signals:** products_services describes a service, process, consulting, or agency offering
**Primary frameworks:** PAS, Star-Story-Solution, Stat-Flip
**Hook priority:** Pain Point > Stat-Flip > Social Proof
**Platform priority:** Meta > Google Search (video) > TikTok (founder-led)

### Type C: Software / SaaS / Platform
**Signals:** products_services is a platform, app, software, or digital tool
**Primary frameworks:** Faceless Benefit Stack, AIDA, Stat-Flip
**Hook priority:** Stat-Flip > Curiosity Gap > Transformation
**Platform priority:** Google > Meta > TikTok

### Type D: Local Business
**Signals:** geo_targeting is very specific (single city/neighborhood), industry is local service
**Primary frameworks:** PAS, BAB, UGC Testimonial
**Hook priority:** Social Proof > Pain Point > Transformation
**Platform priority:** Meta > TikTok (local reach)

---

## Step 3 — Platform Priority Decision

```
IF meta_connected = true AND google_campaigns > 0:
  → Generate adaptations for BOTH Meta + Google
  → TikTok as bonus if industry fits (consumer-facing)

IF meta_connected = true AND google_campaigns = 0:
  → Focus on Meta (Feed + Stories/Reels)
  → Add TikTok if target_audience skews under 35

IF google_campaigns > 0 AND meta_connected = false:
  → Focus on Google Video (Bumper + Skippable)
  → Add Meta as secondary

IF neither connected:
  → Generate universal plan for Meta as default entry point
  → Note: connect platforms to activate full system
```

---

## Step 4 — Skill Stack Activation

Based on classification, activate this exact skill combination:

### Stack for Type A (Physical Product)
1. **Scene Rhythm** (always first — defines pacing)
2. **BAB Transformation** (primary framework)
3. **Hook Matrix 4x3** (generate testing variants)
4. **UGC Testimonial Engine** (trust layer)
5. **Offer-CTA Closer** (always last)
6. **TikTok Native Hook** (if TikTok active)

### Stack for Type B (Service)
1. **Scene Rhythm** (always first)
2. **PAS Short-Form** (primary framework)
3. **Stat-Flip Proof Hook** (use business data from BigQuery)
4. **Star-Story-Solution UGC** (trust layer)
5. **Hook Matrix 4x3** (variant testing)
6. **Offer-CTA Closer** (always last)

### Stack for Type C (SaaS/Platform)
1. **Scene Rhythm** (always first)
2. **Faceless Benefit Stack** (primary framework)
3. **Stat-Flip Proof Hook** (data-driven hook)
4. **AIDA Short-Form** (consideration layer)
5. **Hook Matrix 4x3** (variant testing)
6. **Offer-CTA Closer** (always last)

---

## Step 5 — Generate the Full Video Ad Plan

Produce the complete plan in this sequence:

```
1. BUSINESS DIAGNOSIS
   - What they sell, who they sell to, their key differentiator
   - Business type classification (A/B/C/D)
   - Active platforms from BigQuery data

2. VIDEO STRATEGY
   - Campaign objective (Awareness / Consideration / Conversion)
   - Primary creative approach (which framework leads)
   - Skills stack being used (list all active skills)

3. SCENE PLAN (5-8 scenes)
   Table: # | Duration | What's On Screen | Script/VO | Why It Sells

4. HOOK VARIANTS (3 for A/B/C testing)
   - Hook A: Pain Point version
   - Hook B: Transformation version
   - Hook C: Stat-Flip or Curiosity Gap version

5. FULL SCRIPT (primary version)
   Complete scene-by-scene script using the primary framework

6. PLATFORM ADAPTATIONS
   For each active platform:
   - Duration adjustment
   - Format specs
   - CTA modification
   - Any visual rule changes

7. PRODUCTION CHECKLIST
   What the business needs to film this TODAY
```

---

## JSON Output Schema (for structured integrations)

When outputting structured data, use this schema:

```json
{
  "business": {
    "name": "",
    "type": "product|service|saas|local",
    "industry": "",
    "target_audience": ""
  },
  "strategy": {
    "objective": "awareness|consideration|conversion",
    "primary_framework": "",
    "skills_activated": []
  },
  "hooks": [
    {"type": "pain_point", "line": ""},
    {"type": "transformation", "line": ""},
    {"type": "stat_flip", "stat": "", "flip": ""}
  ],
  "scenes": [
    {
      "number": 1,
      "duration_seconds": "",
      "scene_type": "hook|context|mechanism|proof|cta",
      "visual": "",
      "script": "",
      "on_screen_text": "",
      "why_it_sells": ""
    }
  ],
  "cta": {
    "verbal": "",
    "on_screen": "",
    "button": "",
    "friction_reducer": "",
    "urgency": ""
  },
  "platform_adaptations": {
    "tiktok": {},
    "meta_feed": {},
    "meta_stories": {},
    "google_bumper": {},
    "google_skippable": {}
  },
  "production_checklist": []
}
```
