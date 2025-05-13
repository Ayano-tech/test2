# 🤖 Auto-Issue Tagger Bot

A GitHub App that automatically classifies new issues and assigns labels using OpenAI GPT.  
This project helps OSS maintainers and dev teams streamline issue triage.

GitHubのIssueをAIで自動分類し、適切なラベルを付けるGitHubアプリです。  
OSSや開発チームの運用負荷を減らし、Issue対応の効率化を支援します。

---

## 🚀 Features / 機能概要

- Detect `issues.opened` events via GitHub Webhook
- Analyze issue content using OpenAI GPT
- Auto-assign appropriate labels (e.g. `bug`, `feature`, `question`)
- Optional: Keyword-based rule support
- Optional: Slack notification and dashboard integration

---

## 🧠 Architecture / アーキテクチャ概要

| Component | Description |
|----------|-------------|
| GitHub Webhook | Detects new issues |
| OpenAI API | Classifies content using GPT |
| GitHub REST API | Applies selected labels |
| Optional Slack API | Sends label suggestions or logs |

---

## 🔧 Usage / 使い方

### Step 1: Install GitHub App  
Install the app on the target repository.

### Step 2: Get OpenAI API Key  
Visit [OpenAI](https://platform.openai.com/) and obtain your API key.

### Step 3: Set Environment Variables  
`.env` file:
```env
OPENAI_API_KEY=sk-xxxxxxxxxxxx
GITHUB_APP_ID=xxxx
GITHUB_PRIVATE_KEY=-----BEGIN RSA PRIVATE KEY-----
...
