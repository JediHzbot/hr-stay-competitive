---
name: hr-stay-competitive
description: Generate, maintain, and audit the daily "技能升级" competitiveness review workflow for AI commercial applications. Use when Codex needs to create or update `技能升级-YYYY年MM月DD日.md` files inside `D:\BaiduSyncdisk\个人PPT\Stay competitive`, generate 6 daily judgment questions, collect user answers in `我的意见：`, evaluate those answers against current public information, or set up and repair the related 09:20/09:40/10:00/16:00 automations.
---

# Hr Stay Competitive

Use this skill for the single-file "技能升级" workflow.

## File Contract

- Work only in `D:\BaiduSyncdisk\个人PPT\Stay competitive` for daily main files.
- Use exactly one main file per day: `技能升级-YYYY年MM月DD日.md`.
- Use the title `技能升级` and the date line `日期：YYYY年MM月DD日`.
- Keep daily files in UTF-8 with BOM so Windows tools can read Chinese text reliably.
- Do not create duplicate markdown files, copies, variants, archive files, or subfolder outputs for this workflow.
- Do not create or depend on a separate answer file such as `技能升级-答复.md`.
- Treat the `我的意见：` line under each question as the canonical place for the user's answer.

## Daily Workflow

1. Generate the daily file before 10:00 using current public information about AI commercial applications.
2. Deduplicate against the previous 7 calendar days before asking the user anything.
3. Ask the user the 6 questions at 10:00 in the current thread.
4. At 16:00, collect answers from the main file first, then from the thread only if the main file has no answers at all.
5. If any of Q1 through Q6 is missing or ambiguous, remind the user and stop instead of writing a partial analysis.
6. If all answers are present, fill or refresh the `我的意见：` lines first, then update the analysis sections in place.

## Question Generation Rules

- Research current public information before writing. Prefer official announcements, regulator or government materials, company releases, major consultancies, major financial media, and credible industry media.
- Focus on concrete commercialization, deployment, revenue, customer adoption, partnerships, growth, or regulatory impact.
- Generate exactly 6 dynamic judgment questions.
- For each question, include:
  - `问题：`
  - `背景：`
  - `为什么重要：`
  - `来源：` with source names only and no links
  - `我的意见：` left empty until the user answers
- Keep the question section concise and decision-oriented.
- Do not include full URLs anywhere in the question-generation section.

## Answer Collection Rules

- Prefer answer source order:
  1. Non-empty user-written content already present on today's `我的意见：` lines.
  2. The current thread, from a user message that clearly answers Q1 through Q6. Accept `Q1` and `q1` style labels case-insensitively.
- Ignore placeholder text, empty answer lines, and boilerplate filler.
- If the main file contains some answers but not all 6, treat it as incomplete and remind the user. Do not silently merge partial main-file answers with thread answers.
- If the main file contains no answers at all, thread answers may be used as fallback.

## Analysis Layout

- After answers are complete, maintain exactly these analysis headings and keep each at most once:
  - `## 结论速览`
  - `## 原始回复`
  - `## 逐题评判`
  - `## 综合总评`
- In `## 结论速览`, use a compact markdown table with columns:
  - `题号`
  - `你的回答`
  - `我的结论`
  - `简短判断`
- In `## 原始回复`, preserve the user's wording under `### Q1` through `### Q6`.
- In `## 逐题评判`, for each question use one subsection and include exactly:
  - `你的回答：`
  - `我的结论：`
  - `依据：`
  - `大陆落地修正：`
- In `依据：`, use short bullet links to the strongest public sources.
- In `## 综合总评`, summarize:
  - the user's decision style
  - the two most important corrections
  - 2 to 3 action-oriented takeaways for China mainland commercialization

## Validation Rules

- Check China statutory working day status before generating, asking, or following up.
- Deduplicate against the most recent 7 daily files in the same folder.
- Treat content as too repetitive when the same companies, the same cases, or substantially the same judgment angles dominate the new questions, especially if 3 or more questions materially overlap with the most recent prior file.
- Preserve any existing `我的意见：` answers during 09:40 dedup refreshes.
- Replace existing analysis section bodies in place instead of appending duplicates.
- Preserve the question section's no-link rule even when the analysis section includes source links.

## Automation Contract

Use these names and schedules when repairing or recreating the workflow:

- `Stay competitive / 技能升级 / 09:20 生成`
- `Stay competitive / 技能升级 / 09:40 去重`
- `Stay competitive / 技能升级 / 10:00 16:00 跟进`

Keep the main file directory fixed as `D:\BaiduSyncdisk\个人PPT\Stay competitive`.

## Reference

Read [references/file-layout.md](references/file-layout.md) when you need the exact section order, idempotent replacement boundaries, or the canonical daily file layout.
