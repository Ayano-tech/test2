# 🧩 Data Model: Auto-Issue Tagger Bot

## 1. IssueEvent

Triggered by `issues.opened` Webhook payload.

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | GitHub internal event ID |
| `repository` | object | Info about the repo where issue was created |
| `issue_number` | integer | Unique issue number |
| `issue_title` | string | Title of the issue |
| `issue_body` | string | Full body text of the issue |
| `created_at` | string (ISO 8601) | Timestamp of issue creation |
| `author` | string | Username of the issue creator |

---

## 2. ClassificationResult

Result of the GPT classification process.

| Field | Type | Description |
|-------|------|-------------|
| `issue_number` | integer | GitHub issue number (FK) |
| `suggested_labels` | string[] | Array of suggested label strings (e.g. `['bug']`) |
| `confidence_score` | number (0.0–1.0) | Optional score from AI response or future model |
| `classification_prompt` | string | Prompt used for the OpenAI classification |
| `raw_ai_output` | string | Full JSON or text response from OpenAI (debug log) |
| `timestamp` | string (ISO 8601) | Time classification was generated |

---

## 3. AppliedLabel

Record of labels applied to GitHub.

| Field | Type | Description |
|-------|------|-------------|
| `issue_number` | integer | GitHub issue number (FK) |
| `label` | string | Label applied (e.g. `feature`, `bug`) |
| `applied_by` | string | `bot` or `manual` |
| `applied_at` | string (ISO 8601) | Timestamp of label application |

---

## 4. RuleMapping (Optional: Rule-based support)

Stores keyword-based rules defined by users.

| Field | Type | Description |
|-------|------|-------------|
| `keyword` | string | Keyword or phrase to match in issue body |
| `label` | string | Label to apply when matched |
| `priority` | integer | Order of rule execution |
| `created_by` | string | Username or admin who defined rule |

---

## 5. AppConfig (Optional: User Settings)

| Field | Type | Description |
|-------|------|-------------|
| `repository_id` | string | GitHub repository ID |
| `mode` | string | `live`, `test`, `dry-run` |
| `notify_via_slack` | boolean | Whether to send notifications to Slack |
| `language` | string | Language used for classification (`en`, `ja`, etc.) |
| `created_at` | string | Settings creation date |

