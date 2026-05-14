# Postman CSE Implementation Exercise — Submission

## Repos
- Service 1: https://github.com/likitakum/payment-refund-api-onboarding
- Service 2: https://github.com/likitakum/loan-origination-api-onboarding

## What Was Built
Two services fully onboarded into Postman using the CSE-managed 
orchestrator action (postman-cs/postman-api-onboarding-action@v0).

Both workflows ran end-to-end against a real Postman Enterprise 
workspace. No mocked outputs.

Results visible at: postman.com (workspaces [PAY] payment-refund-api 
and [LND] loan-origination-api)

## Why Payments First
- GitHub Actions CI/CD pattern
- Lambda/API Gateway infrastructure  
- OAuth 2.0 + JWT auth
- Strong OpenAPI spec with examples

## Why Lending Second
- ECS/ALB infrastructure (different from payments)
- mTLS + JWT auth profile
- Multipart upload endpoints
- Less detailed spec — surfaces real adaptation questions

## Universal Pattern
- Service repo owns the OpenAPI spec
- CI runner triggers the onboarding action
- Secrets stored in GitHub, never in repo files
- Reruns are idempotent — updates existing assets

## What Changes Per Service
- project-name, domain, domain-code
- spec-url
- env runtime URLs
- auth pattern and credential rotation process
- safe-to-test endpoint list

## Customer Ops Requirements
Platform team must provide:
- CI secrets (POSTMAN_API_KEY, POSTMAN_ACCESS_TOKEN)
- Environment base URLs per service
- Auth credentials per environment
- mTLS certificates for applicable services
- Safe-to-test endpoint rules

Cannot complete without customer access:
- AWS Gateway/ALB/Kubernetes ingress configs
- GitLab CI variables and runners
- Internal network endpoint validation

## AI Usage

AI (Claude) was used to:
- Read and interpret all 3 GitHub Action READMEs
- Generate the GitHub Actions workflow YAML for both services
- Draft this README and the presentation deck

Validated manually by candidate:
- Activated Postman Enterprise trial personally
- Generated POSTMAN_API_KEY and POSTMAN_ACCESS_TOKEN
- Created both GitHub repos and configured all secrets
- Ran both workflows end-to-end against a real Postman workspace
- Debugged permissions error and spec URL 404 in real time
- Verified both workspaces live in Postman UI
- All output is real — no mocked responses or fake screenshots
