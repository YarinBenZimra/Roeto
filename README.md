# Roeto Automation Assignment

**Submitted by: Yarin Benzimra**

This repository documents the full implementation of all 5 required tasks:
Roeto setup, mock data generation, three working Make scenarios, AI integration, and a new automation product proposal.

---

## 📑 Table of Contents

- [Part 1 – Roeto Account Setup](#part-1--roeto-account-setup)
- [Part 2 – Build & Import 120 Mock Clients](#part-2--build--import-120-mock-clients)
  - [Method Used](#method-used)
  - [Why This Approach?](#why-this-approach)
- [Part 3 – Three Working Make Scenarios](#part-3--three-working-make-scenarios)
  - [Scenario 1 – Automated Lead Qualification & Task Routing Engine](#-scenario-1--automated-lead-qualification--task-routing-engine)
  - [Scenario 2 – Kobi AI Assistant](#-scenario-2--kobi-ai-assistant)
  - [Scenario 3 – AI Revenue Intelligence Engine](#-scenario-3--ai-revenue-intelligence-engine)
- [Part 4 – AI Integration (Prompt Design & Use Case)](#part-4--ai-integration-prompt-design--use-case)
  - [Use Case](#use-case)
  - [Prompt Design](#prompt-design)
  - [Estimated Cost](#estimated-cost)
  - [Risks & Fallback](#risks--fallback)
- [Part 5 – New Automation Proposal](#part-5--new-automation-proposal)
  - [RoetoBot AI – SMS AI Onboarding Assistant for Mislaka](#roetobot-ai--sms-ai-onboarding-assistant-for-mislaka)

---

# Part 1 – Roeto Account Setup

**Actions performed:**

- Registered at: [https://roeto.co.il](https://roeto.co.il)
- Generated API key via: `Settings → API Keys`
- Connected Roeto to Make.com using the official Roeto Make app (no raw HTTP calls)

**Result:**

- Active Roeto account
- Working API key
- Successful connection to Make.com
- All scenarios built using the official Roeto Make integration

---

# Part 2 – Build & Import 120 Mock Clients

## Method Used

To generate 120 realistic client records:

1. I extracted the official Excel template from Roeto:
   - Clients → “Add Multiple Clients +++” → “Download Template”

2. Copied the exact column headers.
3. Prompted OpenAI to generate a CSV file containing **120 realistic client records** with:
   - All fields filled
   - No placeholder data
   - Consistent formatting

4. Validated the CSV manually.
5. Converted CSV → Excel.
6. Uploaded the file into Roeto.
7. Verified that all records were successfully imported.

## Why This Approach?

- For ~120 records, AI generation is:
  - Fast
  - Accurate
  - Cost-effective (single API call)

- If the requirement had been thousands of records:
  - I would have built a chunk-based generation script
  - Generated multiple batches
  - Merged files programmatically

**Result:**
120 fully populated, realistic client records successfully uploaded into Roeto.

---

# Part 3 – Three Working Make Scenarios

All scenarios:

- Use the official Roeto Make app
- Contain 3+ active nodes
- Successfully executed
- Have public View-mode share links

---
### 🎥 Loom Walkthrough
👉 [Watch the full demo here](https://www.loom.com/share/e8648cadf2714f15987680cf37b41467)
---

## 📝 Scenario 1 – Automated Lead Qualification & Task Routing Engine

**CRM Integration Flow | Contact Form**

### Summary

An automation that:

- Receives leads from a contact form
- Checks if the client already exists in Roeto
- Creates a new task or updates an existing one
- Prevents duplicates and ensures structured task routing

### Documentation

Full technical breakdown:
[https://docs.google.com/document/d/1XfFgixQTTO3imER7VOFUlJK0YICYjHnCvwDnV5K1NFY/edit?usp=sharing](https://docs.google.com/document/d/1XfFgixQTTO3imER7VOFUlJK0YICYjHnCvwDnV5K1NFY/edit?usp=sharing)

### Public Make Link

[https://eu2.make.com/public/shared-scenario/uaGHrcKeXqu/scenario-1-automated-lead-qu](https://eu2.make.com/public/shared-scenario/uaGHrcKeXqu/scenario-1-automated-lead-qu)

---

## 🤖 Scenario 2 – Kobi AI Assistant

**Telegram ↔ Roeto Smart Task Automation**

### Summary

“Kobi” is an AI Telegram assistant for pension agent Yarin Benzimra.

It:

- Answers client questions via AI
- Identifies clients
- Creates tasks in Roeto when needed
- Bridges messaging with structured CRM workflows

### Documentation

[https://docs.google.com/document/d/1H19z0x7_6pO-3w08x9IN5jtJLoTFRRBtFeRh5TVoQPo/edit?usp=sharing](https://docs.google.com/document/d/1H19z0x7_6pO-3w08x9IN5jtJLoTFRRBtFeRh5TVoQPo/edit?usp=sharing)

### Public Make Link

[https://eu2.make.com/public/shared-scenario/VEvhJqGJB4E/scenario-2-kobi-ai-assistant](https://eu2.make.com/public/shared-scenario/VEvhJqGJB4E/scenario-2-kobi-ai-assistant)

---

## 🧠 Scenario 3 – AI Revenue Intelligence Engine

**Roeto → Google Sheets → OpenAI → Roeto**

### Summary

An automation that:

- Pulls active clients from Roeto
- Syncs them to Google Sheets
- Uses OpenAI to classify:
  - Potential revenue opportunity
  - Birthday trigger

- Generates personalized marketing or greeting messages
- Creates a structured task in Roeto

### Documentation

[https://docs.google.com/document/d/1g1ReDapTivZNExdGpMJ-oZyj2hgcz6vzCWCNJqaiIko/edit?usp=sharing](https://docs.google.com/document/d/1g1ReDapTivZNExdGpMJ-oZyj2hgcz6vzCWCNJqaiIko/edit?usp=sharing)

### Public Make Link

[https://eu2.make.com/public/shared-scenario/S0oKzXz0uNO/scenario-3-ai-revenue-intelligence](https://eu2.make.com/public/shared-scenario/S0oKzXz0uNO/scenario-3-ai-revenue-intelligence)

---

# Part 4 – AI Integration (Prompt Design & Use Case)

AI was integrated in:

- Scenario 2 (Kobi Assistant)
- Scenario 3 (Revenue Intelligence Engine)

## Use Case

The AI solves structured decision-making problems:

- Classifying clients based on data signals
- Generating contextual task suggestions
- Producing personalized outreach messages
- Avoiding manual CRM review

## Prompt Design

The AI was instructed to return structured JSON only, for example here is the structure in Scenario 3:

```json
{
  "type": "potential" | "birthday",
  "message": "generated message text"
}
```

Design principles:

- Deterministic output format
- Business-rule driven logic
- No free text responses
- Compatible with Make JSON parsing

## Estimated Cost

Using GPT-4.1-mini:

- Approx. ~$0.002–$0.005 per run
- Monthly cost depends on execution frequency
- Designed to minimize token usage

## Risks & Fallback

Potential Issues:

- Model fallback
- Malformed JSON
- API downtime

Mitigation:

- JSON validation step in Make
- Error handling route

---

# Part 5 – New Automation Proposal

## RoetoBot AI – SMS AI Onboarding Assistant for Mislaka

### Motivation

RoetoBot AI transforms a slow, manual onboarding process into a structured, intelligent SMS-based flow that automatically collects missing client data.

It reduces operational workload, shortens time-to-consultation, and improves the client experience using state-based automation.

### Full Spec Document

[https://docs.google.com/document/d/1FM_0TnFiZXLbElbA8f_pKZfn7DKYtbYUg8ZC1WEc8P4/edit?usp=sharing](https://docs.google.com/document/d/1FM_0TnFiZXLbElbA8f_pKZfn7DKYtbYUg8ZC1WEc8P4/edit?usp=sharing)
