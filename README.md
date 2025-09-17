```markdown
# Prompting ChatGPT-5 as a DevOps Engineer  
Complete guide, templates, and examples for turning any LLM into your senior infrastructure-automation partner.

---

## 📋 What This Repo Contains
- **Core prompting framework** – how to frame role, task, inputs, constraints, and expected outputs so the model behaves like a battle-tested DevOps engineer.  
- **Component-by-component checklists** – IaC, networking, security, CI/CD, observability, software config, cost-optimisation, multi-cloud, compliance, DR.  
- **Copy-paste prompt library** – four production-grade examples (AWS 3-tier web app, GKE + Prometheus, secure GitLab pipeline, AWS DR plan) with full deliverables lists.  
- **README template** – this file – so every generated project is immediately usable by the next human or AI.

---

## 🚀 Quick-Start – “I Need Infrastructure Now”
1. Fork / clone this repo.  
2. Open `prompts/` → pick the scenario that matches your stack.  
3. Replace the bracketed `[variables]` with your real values.  
4. Paste the final prompt into ChatGPT-5 (or any LLM) → receive Terraform, Ansible, GitHub Actions, Grafana dashboards, runbooks, etc.  
5. Commit the generated code, open PR, run `terraform plan`, merge, done.

---

## 🧠 Prompt Anatomy (copy & save as `prompt-template.md`)
```markdown
ROLE  
You are a Senior DevOps Engineer, 10 yrs exp, expert in {cloud}, {iac}, {k8s}, security & cost optimisation.

TASK  
Design, secure, and automate a production-grade {workload} on {cloud}.

INPUTS  
- App: {language}, {arch}, {traffic}, {SLA}  
- Stack: {cloud}, {iac}, {ci-cd}, {registry}, {observability}  
- Constraints: {budget}, {compliance}, {region}, {HA}  

EXPECTED OUTPUTS  
1. Modular {iac} scripts (state-backend, variables, envs).  
2. CI/CD pipeline file with security & quality gates.  
3. Monitoring stack (Prom, Grafana, alerts-as-code).  
4. README with deploy, test, rollback, and cost-report steps.  
5. DR runbook (RTO/RPO) + draw.io diagram XML.
```

---

## 📁 Folder Layout After Generation
```
infra/
├─ terraform/
│  ├─ vpc/
│  ├─ compute/
│  ├─ security/
│  └─ backend.tf
├─ ansible/
│  └─ playbooks/
├─ k8s/
│  └─ manifests/
├─ .github/workflows/  or  .gitlab-ci.yml
├─ monitoring/
│  ├─ prometheus/
│  ├─ grafana/  (dashboards JSON)
│  └─ alerts/
├─ docs/
│  ├─ RUNBOOK.md
│  ├─ COST.md
│  └─ architecture.png
└─ README.md  ← this file
```

---

## 🔒 Security & Compliance First
- Every generated template already embeds:  
  – Encryption at rest & in transit  
  – Security groups / NACLs least-privilege  
  – IAM roles per service, no wildcard `*`  
  – SAST/DAST/container scan stages in CI/CD  
  – CIS benchmark-ready Terraform modules  
- Swap the placeholder compliance stanza (`SOC2`, `HIPAA`, `PCI`) and re-prompt → instant compliant config.

---

## 💰 Cost Optimisation Built-In
- Spot / preemptible instances for stateless workloads.  
- GP3 / HDD tiers for infrequent data.  
- Auto-scaling with target utilisation 70 %.  
- Monthly budget alerts via CloudWatch / GCP Budget API.  
- Right-sizing Lambda after 7-day metrics.

---

## 🧪 Testing Your Generated Code
```bash
# 1. Lint
tflint && terraform validate
# 2. Security scan
checkov -d terraform/
# 3. Cost diff
infracost breakdown --path terraform/
# 4. Dry-run
terraform plan
# 5. OPA policy test
conftest verify
```

---

## 🔄 Drift & Lifecycle
- State locked in S3 + DynamoDB (AWS) / GCS + Firestore (GCP) / Azure Blob + Table.  
- Weekly `terraform plan` in CI to detect drift → open issue automatically.  
- Ansible playbook `--check` mode every 6 h; report on config drift in Slack.

---

## 🗂️ Prompt Library Index
| File | Scenario | Technologies | Output |
|------|----------|--------------|--------|
| `prompts/aws-scalable-webapp.md` | 3-tier web, 10 k CCU | AWS, Terraform, GitHub Actions, CloudWatch, Grafana | Full IaC + CI/CD + dashboards |
| `prompts/gke-monitoring.md` | Microservices on GKE | GKE, Prometheus, Grafana, Fluentd, EFK | Regional cluster, EFK, dashboards |
| `prompts/secure-cicd-nodejs.md` | Secure pipeline | GitLab CI, Trivy, SonarQube, K8s canary | `.gitlab-ci.yml`, manifests, gates |
| `prompts/aws-dr-plan.md` | DR for e-commerce | AWS, RDS, S3, Terraform | Pilot-light infra, runbooks, RTO 4 h |

---

## 🚑 Troubleshooting Tips
- **Output too big?** Ask the model to split into “phase-1 core” and “phase-2 observability” prompts.  
- **State lock timeout?** Model will generate `-lock-timeout=10m` flag + DynamoDB TTL.  
- **Need multi-cloud?** Provide both AWS & Azure provider blocks → model outputs `providers.tf` for each.  
- **Old TF version?** Add constraint: “Use Terraform ≥ 1.5 with optional object attributes.”

---

## 🤝 Contributing
1. Add a new scenario under `prompts/`.  
2. Include: prompt, sample vars file, and screenshot of generated plan.  
3. PR must pass `tflint`, `shellcheck`, `markdownlint`.

---

## 📄 Licence
MIT – generated code is yours, no strings attached.

---

## 📞 Support / Chat
Discussions enabled on GitHub. Tag `@bot` if you want the AI to re-generate stale modules.

Happy shipping! 🚀
```
