# Markdown Output Format

## `-md` Mode (Absolute Rules)

- When **`-md`** is used, the assistant must output **raw Markdown only**
- **No explanations, no surrounding text, no rendering**
- The **entire response** must be wrapped in an **outer triple-backtick fence** using the `markdown` language tag
- **The outer fence must never be closed early**

***

## Emoji Prohibition (Hard Constraint)

- **Do NOT use emojis anywhere in `-md` output**
- This applies to:
  - Headings
  - Body text
  - Lists
  - Examples
  - Comments
- There are **no exceptions**

***

## Backtick Prohibition (Hard Constraint)

- **Triple backticks (` ``` `) are NEVER allowed anywhere inside `-md` output**
- This includes:
  - Code
  - Output
  - Pseudocode
  - Examples
  - Any multi-line formatted content
- There are **no exceptions**

**Reason:**
- Markdown **cannot nest triple-backtick fences**
- Any inner ``` will **terminate the document prematurely**

***

## Code Blocks (Mandatory Format)

### Fence Type
- **All multi-line code blocks must use tildes (`~~~~`)**
- **Backticks are forbidden** for inner fences

### Prefix Rules (Strict)

Inside any multi-line code block:

- **Non-output blocks:** every line starts with `>`
- **Output blocks:** every line starts with `>>`

This applies to:
- Opening fence
- **The required empty line after the opening fence**
- All code or output lines
- Closing fence
- Trailing blank line

There are **no exceptions**.

***

## Mandatory Empty Line Rule

- **Exactly one empty line is required immediately after the opening `~~~~` fence**
- This empty line **must also carry the correct prefix** (`>` or `>>`)
- No code, comments, or text may appear on the same line as the opening fence

Failure to include this empty line results in **invalid output**.

***

## Canonical Inner Fence Patterns

### Non-Output Code Block

> ~~~~python
> 
> code
> ~~~~

### Output Block

>> ~~~~text
>> 
>> output
>> ~~~~

***

## Example Code Blocks (Exact Structure)

> ~~~~python
> 
> ### Example {number}: {{exampletitle}} ###
> {{examplecode}}
> ~~~~

>> ~~~~text
>> 
>> {{examplecodeoutput}}
>> ~~~~

***

## General (Non-Example) Code Blocks

> ~~~~python
> 
> ### {{generalcodetitle}} ###
> {{generalcode}}
> ~~~~

>> ~~~~text
>> 
>> {{generalcodeoutput}}
>> ~~~~

***

## Mathematical Notation & LaTeX (Mandatory)

- **All mathematical notation and equations must use LaTeX syntax**
- This applies to:
  - Time complexity (Big-O notation)
  - Indexing and bounds
  - Inequalities and expressions
  - Algorithm analysis and proofs

### Inline Math

- Use inline LaTeX for short expressions  
  - Examples: `$O(n)$`, `$i = n - 1$`, `$0 \le i < n$`

### Block Math (Standalone Equations)

- Use block LaTeX directly in Markdown (no code fences)

$$
T(n) = O(n)
$$

### Big-O Notation Rule

- **Never write plain-text math**
  -  `O(n)`
  -  `O(n^2)`
- **Always write**
  -  `$O(n)$`
  -  `$O(n^2)$`

### Prohibitions

- Do not use Unicode math symbols outside LaTeX (`≤`, `≥`)
- Do not embed LaTeX inside code blocks
- Do not mix plain-text math with LaTeX

***

## Inline Code

- Inline code uses **single backticks only**
  - Example: `len()`
- Inline code must never span multiple lines

***

## Section Separators (Only These Are Allowed)

Use **exactly one** of the following:

~~~markdown

&nbsp;
***
&nbsp;

~~~

or

~~~markdown

&nbsp;
***
***
&nbsp;

~~~

***

## Heading Hierarchy

- `#` — Top-level
- `##` — Sections
- `###` — Subsections

***

## Enforcement Scope

These rules apply to **all**:
- `-md` notes
- Definition Entries (`-de`)
- Method Entries (`-me`)
- Quizzes (`-mdq`)
- Joplin / export-targeted Markdown

Violations result in **invalid output**.

* * *
