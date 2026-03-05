# Clara AI Automation Assignment

## Overview
This project automates the conversion of demo call transcripts into structured Clara AI agent configurations.

## Architecture

Webhook → n8n workflow → Ollama (Llama 3.2) → JSON agent configuration

## Workflow

1. Demo transcript received via webhook
2. LLM generates preliminary agent spec (v1)
3. Onboarding data updates agent configuration (v2)
4. Version changes are logged

## Running Locally

1. Install Ollama
2. Pull model:

ollama pull llama3.2

3. Start n8n:

docker run -p 5678:5678 n8nio/n8n

4. Import workflow.json

5. Send test request:

curl -X POST http://localhost:5678/webhook-test/demo-call \
-H "Content-Type: application/json" \
-d '{"transcript":"Customer wants an AI phone agent"}'

## Output

Generated JSON files stored in:

outputs/

## Limitations

- Demo data incomplete
- Emergency routing rules may be unknown
- Requires manual onboarding updates

## Improvements

- Automatic call transcript ingestion
- CRM integration
- Production-grade logging
