# Daily File Layout

Use this exact structure for the daily main file:

1. `# 技能升级`
2. `日期：YYYY年MM月DD日`
3. `## 今日简报`
4. `## 问题 1` through `## 问题 6`
5. Under each question:
   - `问题：`
   - `背景：`
   - `为什么重要：`
   - `来源：`
   - `我的意见：`
6. Post-answer analysis area:
   - `## 结论速览`
   - `## 原始回复`
   - `## 逐题评判`
   - `## 综合总评`

## Idempotent Update Rule

- Keep only one copy of each analysis heading.
- Refresh bodies in place when headings already exist.
- Never append a second `## 结论速览`, `## 原始回复`, `## 逐题评判`, or `## 综合总评`.

## Question Preservation Rule

- Keep the original question text, backgrounds, and source-name-only lines intact during afternoon updates.
- Update only `我的意见：` and the post-answer analysis area during answer-processing runs.
