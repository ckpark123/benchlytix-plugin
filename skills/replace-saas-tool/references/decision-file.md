# Decision file

Write one only when the user asks for it. When file tools are available, write it to
`benchlytix-decision-<goal>-<date>.md` in the working folder, where <goal> is `query.goal` and <date> is today's
date (YYYY-MM-DD). Without file tools, give the same content as one Markdown block.

Markdown only. Every line comes from the tool answers, with its date and link, in the same words as the answer.
The file follows the answer's rule for prices: never a price without its limit note.

```markdown
# <query.goal_title>: options to replace <query.paid_tool.name>

Source: <cite.text>, as of <as_of>. Links: <goal_url> <calculator_url>

## List price
<figure_text lines verbatim, each followed by its limit_note quoted, or no_figure_line; total_lines verbatim for two or more tools; based_on lines>
<paid_tool_prices sentence lines verbatim, each followed by its limit_note quoted when present, read on checked_at>

## Options (in the order BenchLytix lists them)
<order_note>

| Option | Evidence | Licence | Last default-branch commit | Hosting reference |
|---|---|---|---|---|
| <name> | <evidence label in words> | <licence_class> <licence_spdx> | <default_branch_commit_at> | <plan> <monthly> EUR, reference, not a total |

Only when the user named apps to keep, add a column "Apps you named it keeps": <matched_count>, missing
<coverage.missing>, read <crawled_at>.

## What you lose
<coverage.missing, editorial known gaps, hidden with reasons>

## Not checked by BenchLytix
<left_out; listed_untested options>

## Your constraint
<only when the user stated one: the one recommendation line from SKILL.md step 4>
```
