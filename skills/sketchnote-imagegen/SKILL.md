---
name: sketchnote-imagegen
description: Summarize longform articles into image-generation briefs for sketchnote-style visual notes. Use when is asked to read an article, markdown post, draft, or URL and create or prepare a matching illustration, cover image, article summary image, visual note, whiteboard note, or image prompt in a sketchnote / marker / light watercolor style.
---

# Article Sketchnote Image

## Purpose

Turn an article into a concise visual-note brief, then use the existing image generation workflow when the user wants an actual image.

Prefer this for blog posts, technical notes, reading notes, and article cover/supporting images. Keep the article's intent and structure, but translate it into a readable visual layout instead of a dense infographic.

## Workflow

1. Read the article source first.
   - For local Markdown, preserve front matter, headings, image references, links, code terms, and the article's existing emphasis.
   - For URLs or PDFs, use the appropriate reading workflow before summarizing.
2. Extract the visual story.
   - Identify 3 to 6 main sections or ideas.
   - Keep concrete nouns, short labels, and technical terms that need to appear visually.
   - Drop long explanations, rhetorical transitions, repeated conclusions, and paragraph-level detail.
3. Decide the output form.
   - If the user asks to generate an image, invoke other imagegen skills to generate images after preparing the brief.
   - If the user only asks for preparation, return the summary and final image prompt.
   - If the image is for the current Hugo blog, save the generated asset in the article bundle or a clearly related project path, then update the Markdown only when requested or clearly implied.
4. Compose the prompt with stable defaults.
   - Style: sketchnote whiteboard visual note.
   - Background: warm off-white / cream paper, not pure white.
   - Medium: hand-drawn marker line art with light watercolor washes.
   - Layout: airy grouped modules, arrows, small icons, readable Chinese labels.
   - Density: avoid packing the whole article into one image.
5. Validate before finishing.
   - Check that the prompt does not ask for too much text.
   - Check that labels are short enough for image generation.
   - Check that the visual hierarchy follows the article, not a generic template.
   - For project-bound assets, report the final path and the prompt used.

## Summarizing Rules

Use concise Chinese by default when the article is Chinese.

Prefer:
- short phrases over full sentences
- section-level ideas over paragraph summaries
- article-specific symbols over generic business icons
- 3 to 6 visual groups over many small boxes
- a light opening note only when it helps the composition

Avoid:
- textbook explanations
- labels that say "this article will explain..." or similar meta-writing
- dense paragraphs inside the image
- corporate slide or dashboard style
- photorealism, glossy 3D, dark backgrounds, neon gradients
- overclaiming conclusions not present in the article

## Prompt Template

Use this as the base prompt and adapt the bracketed parts:

```text
Use case: infographic-diagram
Asset type: article sketchnote visual note
Primary request: Create a sketchnote-style visual note for this article summary.

Article theme: [short theme]
Visual groups:
1. [group title]: [2-4 key labels]
2. [group title]: [2-4 key labels]
3. [group title]: [2-4 key labels]
4. [group title]: [2-4 key labels]

Style/medium: sketchnote whiteboard visual note, hand-drawn marker line art, light watercolor washes.
Scene/backdrop: warm off-white paper background, clean and calm.
Composition/framing: airy layout with 3 to 6 grouped modules, simple arrows, small hand-drawn icons, balanced whitespace, readable hierarchy.
Text: short Chinese handwritten-style labels only; keep all text brief and legible.
Color palette: black and charcoal marker lines, muted blue, soft green, pale yellow, light coral accents.
Constraints: preserve the article's actual meaning; do not add unrelated claims; avoid dense paragraphs.
Avoid: photorealism, glossy 3D, corporate infographic style, dark background, neon colors, tiny unreadable text, watermark.
```
