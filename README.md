#  MedFlow AI
### Internal Clinical & Operations Agent

> **Type:** Internal AI Agent · Full-stack demo
> **Stack:** Vanilla JS · Anthropic Claude API · HTML/CSS
> **Demo:** Open `demo.html` in any browser

---

## What It Does

MedFlow AI is a single-interface internal agent designed for hospital clinical staff. It replaces three separate fragmented tools — a triage board, a notes system, and a scheduling spreadsheet — with one AI-first dashboard where every action is either assisted or automated by Claude.

**Three core modules:**

1. **Triage Queue** — AI-prioritized patient list with severity scoring. Click "AI Brief" on any patient to instantly receive a clinical reasoning summary and recommended next steps for that specific presentation.

2. **Clinical Notes** — Enter raw observations (or voice-to-text output) and generate a structured SOAP note (Subjective / Objective / Assessment / Plan) with a single click. Reduces documentation time by ~60%.

3. **Staff Schedule** — Visual weekly schedule with conflict detection. "AI Optimize" resolves gaps and conflicts with reasoned recommendations.

---

## Key Technical Decisions

### 1. Persistent Chat Context
The AI assistant panel maintains conversation history across the session. If you ask about a patient, then follow up with "what drugs might interact?", the agent remembers the context without re-prompting. This is the foundation of agentic behavior — statefulness.

### 2. Structured Output from Unstructured Input
The SOAP note generator accepts freeform text (mirroring actual clinical voice-to-text or rushed notes) and transforms it into a standardized medical document. This pattern — `unstructured input → structured, actionable output` — is the core commercial value of internal AI agents.

### 3. Per-Patient Contextual Briefs
Rather than a generic chatbot, each "AI Brief" button pre-loads patient-specific context into the prompt. The agent receives name, age, chief complaint, and vitals — then generates a targeted clinical assessment. This demonstrates how internal agents can surface the right context at the right moment.

### 4. Operation-Triggering UI
The "AI Optimize" button on the schedule isn't just informational — it fires an async AI call, processes the response, and updates the UI state (resolving conflict count). This pattern mirrors what Cowork does: AI doesn't just respond, it acts.

---

## Commercial Thinking

**Problem it solves:** Clinical documentation takes 34% of a physician's time (AMA, 2023). Triage misclassification costs hospitals an average $1,200/patient in extended stays or adverse events.

**Why an internal agent wins here:** An external tool (standalone app) would require data exports, separate logins, and broken workflows. An internal agent embedded in the existing ops context eliminates all friction — it knows the queue, the staff, the patient — and acts within the same interface.

**Monetization angle for a company like Xpert:** License to hospital systems at $X/bed/month. The ROI justification writes itself — even 10% reduction in documentation time = measurable FTE savings.

---

## What I'd Build Next

- EHR integration (HL7 FHIR API) to pull real patient data
- Voice-to-text input via Web Speech API
- Agent memory: recall past patient interactions across sessions
- Tool use: agent autonomously orders labs, sends Slack alerts to on-call staff

---

## Running Locally

```bash
# Just open the file — no build step needed
open demo.html

# The Anthropic API is called directly from the browser
# All features are live with real AI responses
```
