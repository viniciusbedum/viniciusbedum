# Make your own chat

This repository is an animated intro chat for a GitHub profile README. Six short messages type in, one after the other. You can use it and adapt it as you like. It is MIT licensed.

## Step by step

1. Fork this repository.
2. Rename the fork to your GitHub username. The README only becomes your profile when the repository is named `username/username`. GitHub only lets you do this if you don't already have a repository with that name. If you do, create a new repository with that name and copy `chat.svg` and the image line of `README.md` into it.
3. Open `chat.svg`, click **Code**, then the pencil icon to edit.
4. Replace the text inside each `<tspan>` (lines 22 to 32). Each bubble is one `<rect class="b">` followed by its `<text>`. The "About me" label is the line with `class="l"`.
5. In `README.md`, replace the `mailto:` link with your own email or any URL.
6. Commit the changes.
7. Open your profile. GitHub can take a few minutes to refresh the image cache.

## Warning: text can overflow the bubble

**A bubble does not grow by itself.** Its width is fixed in the `width` of its `<rect class="b">`.

- Longer text than the bubble: it runs past the border.
- Shorter text: empty space is left on the right.

How to fix it:

- Change the `width` of that bubble's `<rect>` until the text has the same space on both sides (about 12px each).
- Rule of thumb: about 6px per character (font at 12px) plus 24px. This is an approximation. Always check the preview.
- If you change the widest bubble, change `width` and `viewBox` of the `<svg>` on line 1 too, so the margin stays 24px on both sides.
- For two lines, use one `<tspan>` per line, each with its own `y` (18px apart). Make the `<rect>` taller (`height="50"` instead of `32`) and move the bubbles below it down.

```xml
<text>
  <tspan x="36.5" y="169.7">First line of the message,</tspan>
  <tspan x="36.5" y="187.7">second line of the message.</tspan>
</text>
```

The **Preview** tab, next to **Edit**, shows the final state of the bubbles: sizes, spacing and text. It does not show the animation, only the last frame. Open it after every edit, before committing.

## Fonts and glyphs

The embedded font covers basic Latin and the Latin-1 accents (á, ç, ñ, ü and so on). Other alphabets fall back to a system font.

## Prompt for an AI assistant

Paste this into any AI assistant, then paste the full content of `chat.svg` below it.

```text
You will edit an animated SVG chat (chat.svg) used in a GitHub profile README. Replace its texts with mine and fix the layout so nothing overflows.

How the file works:
- Each chat bubble is a <rect class="b" x y width height rx> followed by a <text> with one <tspan> per line. Two-line bubbles have two <tspan> elements with different y values and a taller <rect>.
- The small gray label at the top (class="l") is the chat title.
- Animation is done with CSS classes: .tN is the "typing" dots group and .mN is the message group, each with its own animation-delay in the <style> block.
- The font is Inter Light (weight 300) at 12px, embedded as base64 in @font-face. Do not touch it.
- The canvas has 24px margins on the left and right. Text has 12px inner padding inside each bubble. A one-line bubble is 32px tall, a two-line bubble is 50px tall with 18px between lines, and bubbles are 10px apart.

What I want:
- Use my messages, in order: [MESSAGES]
- The link in the README will be: [LINK] (only mention it in the text if I put it in a message)

Rules:
1. Recalculate the width of each <rect class="b"> as the text width in Inter 300 at 12px plus 24px. For two-line bubbles, use the longer line.
2. Recalculate the height of two-line bubbles and the y positions of every bubble, typing dots and tspan below it so spacing stays consistent.
3. Recalculate the width and viewBox of the <svg> so there are exactly 24px of margin on the left and right of the widest bubble, and the height fits the last bubble plus 24px.
4. Keep all classes, animations and the base64 font unchanged. If I give more or fewer messages, add or remove the matching .tN/.mN groups and CSS rules. Each message starts about 2.9s after the previous one, and its typing indicator (1.5s) plays right before it. Increase the delays accordingly.
5. Do not invent content. Use only what I gave you.
6. Return only the complete chat.svg in one code block, nothing else.
```

## License

MIT, see `LICENSE`. Inter is licensed under the SIL Open Font License 1.1.

Enjoy!
