# AI Agent Technical Architecture & Pipelines

**Project**: FinArva AI — Next-Gen Agent Experience for GroMo  
**Lead Product Strategist**: Ayush Shah  
**Team**: PERCEPTRONS (Ayush Shah, Aarya Pawar, Geethansh Rathore, Isha, Rajdeep Nayak)  

---

## 1. TransparAI Autonomous Payout Pipeline

```
[ Financial Partner Webhook ]
        │ (e.g. HDFC / Axis / SBI Bank Lead Sanction Event)
        ▼
[ Ingestion API Gateway (FastAPI / Express) ]
        │
        ▼
[ Resilient Message Broker Queue (RabbitMQ / Redis) ]
        │
        ├────────────────────────────────────────────────────────┐
        ▼                                                        ▼
[ Deterministic Verification Engine ]              [ Computer Vision Extraction ]
  • Regex Engine for PAN (ABCDE1234F)                • Google Cloud Vision OCR Engine
  • IFSC Routing & Bank Code Match                   • Auto-extracts account number & beneficiary name
  • Duplicate Lead Detection                         • Image quality & tampering risk score
        │                                                        │
        └───────────────────────────┬────────────────────────────┘
                                    ▼
                     [ Machine Learning Risk Scorer ]
                                    │
               ┌────────────────────┴────────────────────┐
               ▼                                         ▼
      [ Low Risk / Match ]                     [ High Risk / Mismatch ]
               │                                         │
    • Update Database Record                  • Automated Event-Triggered SMS / WhatsApp
    • Auto-append to Finance Payout Batch      • Precise Rejection Reason & 1-Click Retake Link
    • Status: "Awaiting Disbursal"             • Push to Human Escalation Queue if 2nd retry fails
               │
               ▼
[ Real-Time Mobile Tracker UI: Confirmation ➔ Verification ➔ Awaiting Disbursal ➔ Paid ]
```

---

## 2. GroMoGuide Multilingual WhatsApp Voice & Text Architecture

```
[ WhatsApp User (Voice Note / Audio / Text in Hindi/Marathi/English) ]
                            │
                            ▼
           [ Meta WhatsApp Cloud Business API Webhook ]
                            │
                            ▼
          [ Audio Transcoding & Speech-to-Text ]
            (Whisper API with Indian Accents)
                            │
                            ▼
         [ LLM Orchestrator & Intent Extraction ]
                            │
            ┌───────────────┴───────────────┐
            ▼                               ▼
[ Policy / Transaction Query ]      [ Complex Claim / Grievance ]
            │                               │
[ NL-to-SQL Translator ]            [ Smart Escalation Engine ]
            │                               │
[ MySQL / Seller DB Query ]         [ Handoff to GP with Context ]
            │
            ▼
[ Localized Voice / Text Synthesis ]
            │
            ▼
[ Instant WhatsApp Response (< 3s) ]
```

---

## 3. FinFit Advisor Dynamic Lead Profiler Flow
- **Conversational Lead Capture**: Embeds responsive micro-forms in regional languages.
- **Dynamic Scoring**:
  $$\text{Eligibility Score} = f(\text{Monthly Income}, \text{Credit Score}, \text{Age}, \text{Pre-existing Loans})$$
- **Product Matchmaker**: Returns top 2 high-approval financial products, increasing conversion by **3.2x**.
