# 🧾 PRD: Auto-Issue Tagger Bot

## 1. Overview

Auto-Issue Tagger Bot is a GitHub App that uses OpenAI’s GPT API to analyze newly opened GitHub Issues and automatically assign appropriate labels.  
The goal is to reduce the manual workload of OSS maintainers and improve triaging efficiency in large or active repositories.

---

## 2. Goals

- Automatically classify issues based on natural language content
- Assign GitHub labels like `bug`, `feature`, `question`, etc.
- Improve issue management consistency
- Reduce manual triage overhead

---

## 3. Target Users

| Role | Pain Point | Benefit |
|------|------------|---------|
| OSS Maintainers | Too many unlabeled issues | Save time via auto-labeling |
| Team Leads | Inconsistent issue triage | Ensure tagging consistency |
| New Contributors | Unsure how to tag | Immediate auto-classification |

---

## 4. Core Features

| Feature | Description |
|---------|-------------|
| 🔔 Webhook Event Detection | Listen to `issues.opened` events |
| 🧠 AI Labeling | Use OpenAI GPT to analyze the issue content |
| 🏷️ Label Assignment | Apply the label using GitHub REST API |
| ⚙️ Rule-Based Supplement (optional) | Keyword-triggered fallback logic |
| 💬 Slack Notification (optional) | Post label suggestions to a channel |
| 🧪 Test Mode | Suggest labels via comment instead of applying (safe test)

---

## 5. User Stories

### 👨‍💻 Maintainer
> “As a maintainer, I want new issues to be labeled automatically so I can focus on solving them instead of classifying them.”

### 👩‍💻 Developer
> “As a contributor, I want to see what kind of issue I'm opening so I know how it fits into the project.”

---

## 6. MVP Scope

- GitHub App registration and installation
- Webhook setup for `issues.opened`
- Integration with OpenAI GPT API (e.g., `gpt-4`)
- Mapping GPT output to GitHub labels
- Label application via REST API
- `.env` config for keys

---

## 7. Non-Functional Requirements

- Secure handling of GitHub and OpenAI credentials
- Latency under 5s per issue
- Logging of AI outputs for transparency
- Deployable to Heroku/Vercel or GitHub Actions (TBD)

---

## 8. External Services

| Service | Use |
|---------|-----|
| GitHub API | Issue detection and label application |
| GitHub Webhooks | Event trigger mechanism |
| OpenAI API | Content classification |
| Slack API (optional) | Notification of classifications |

---

## 9. Success Metrics

- ✅ 80%+ labeling accuracy (manual review)
- ⏱ 50% reduction in triage time
- 📈 70%+ user retention after 2-week pilot
- 🧪 < 3 false positives per 100 issues

---

## 10. Architecture (Simplified)


---

## 11. Future Enhancements

- Labeling for Pull Requests and Discussions
- Admin UI to edit rules and view label stats
- Localization support (Japanese, etc.)
- Confidence score display or manual override
- GitHub Actions integration (workflow-level control)

---

## 12. Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| Misclassification | Test mode with preview comment |
| API Rate Limits | Caching or batching calls |
| AI model bias | Fine-tuned prompts or custom models |
| Language limitations | Explicit prompt and fallback rules |

---

## 13. Timeline

| Week | Task |
|------|------|
| 1 | Setup GitHub App, Webhook |
| 2 | Integrate OpenAI API |
| 3 | Add labeling logic and .env support |
| 4 | Testing, Feedback, Optional Slack link |

---

## 14. Team Roles

| Role | Responsibility |
|------|----------------|
| PM | Planning, backlog |
| Dev | GitHub API & GPT integration |
| Prompt Engineer | GPT tuning and accuracy validation |
| QA | Accuracy & performance testing |
| (Optional) UX | Admin UI or dashboard

---

## 15. References

- [Probot Framework](https://probot.github.io/)
- [OpenAI Docs](https://platform.openai.com/docs/)
- [GitHub Webhook Events](https://docs.github.com/en/webhooks/webhook-events-and-payloads)
- [Octokit GitHub SDK](https://github.com/octokit/octokit.js)

