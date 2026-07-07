## Formatting Spec Prompt (extra-excercises)

Use this as the *system prompt / editing checklist* when cleaning up `notes/extra-excercises/_chNN.qmd` files.


### Scope & guardrails

- Keep edits small and local (prefer fixing a few “Try It” blocks per pass).
  As one error in a long block means rejecting all the edits and repeating.
- Do **not** add the book title header (`# OpenStax Introductory Statistics 2e`) to chapters other than Chapter 1.
- Preserve the meaning/content; only restructure for consistent Quarto formatting and renderability.
- Any deviations are likely going to increase editing time and effort so the goal is to offer many small edits after one pass of the file. (I've split it into 13 parts for this reason) use File _ch01.qmd can be used as a reference!

### Headings

- Chapter heading format: `## Chapter N. …` (period after the chapter number).
- Section heading format: `### Section K. …` (period after the section number).
- Avoid bare lines like `Section 4. …` — convert them to proper `### …` headings.

### Exercises (“Try It” blocks)

Convert each Try It / exercise into a fenced div + a collapsible solution callout.

**Exercise block**

```markdown
::: {#exr-try-<id>}
<exercise text only>
:::
```

- Use a stable id like `#exr-try-4-7` (match chapter numbering when possible).
- The exercise div should include only the prompt/question and any tables/figures needed for the question.

**Solution block** (must come *after* the exercise div is closed)

```markdown
::: {.callout-tip collapse="true"}
#### Solution

<solution text>
:::
```

- Always use `#### Solution` (not `## Solution`).
- Ensure fenced div nesting is correct: the exercise div must be closed before starting the callout.

### Confirmation workflow (prompt vs solution)

- Treat the **exercise prompt** and the **solution** as two separate concerns.
- When converting a Try It block:
	- Preserve the prompt text first (exercise div), then preserve the solution text (callout), without trying to “fix” the solution unless explicitly requested.
- When reporting progress back to the user, confirm these separately:
	- **Prompt confirmed**: prompt text preserved and renders correctly.
	- **Solution confirmed**: solution wrapped/structured correctly and renders correctly.

### Regarding code for execution

I don't like running code I haven't coded.
Keep requests to a minimum.
supply a brief header with the codes intent if short.
if longer a short summary.


### Lists

- Prefer consistent Markdown lists. Avoid indenting list items so far that they become code blocks.
- For solutions, use `-   ` bullets (as in Chapter 1) when listing multiple items.

### Tables

- Prefer clean Markdown tables.
- If a table should have a caption/id, use Pandoc caption syntax:
	- `: Caption {#tbl-some-id .striped .hover}`

### Rendering hygiene

- Eliminate stray `:::` / unbalanced fences.
- Remove orphaned/partial code fences.
- After a batch of edits, run `quarto render notes/extra-excercises/_chNN.qmd` and fix any “Div unclosed” warnings.

---

### Second Pass

1. Fix text math to latex
2. Also in many places math was discarded during conversion
3. In many places calculation for scientific calculator are suggested - replace with R code 

### Third pass  - will be done in a later pass.

1. setup blocks will be added as needed
2. data list and tables will next be converted from markdown to tibbles and rendered using kable
3. these will be used in the solution which will have a tabset with r and python code.

