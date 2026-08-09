# nioi-publisher

Publish bilingual articles to the `nioi` GitHub Pages site.

## Scope

Use this skill only when publishing or updating articles in `nioi`. Do not use it to redesign the site unless explicitly requested.

## Source of truth

Before publishing, read the current repository structure and relevant layouts/configuration. Repository state overrides examples in this skill if they diverge.

## Language contract

Each article is normally published in two versions:

- Taiwanese Chinese: `locale: zh-tw`, `lang: zh-Hant-TW`
- Japanese: `locale: ja`, `lang: ja`

Both versions of the same article must use the same `translation_key`.

Taiwanese Chinese is the source version unless the user explicitly says otherwise.

The Japanese version should preserve the same argument, meaning, structure, and tone, but should be rewritten as natural Japanese rather than translated mechanically sentence by sentence.

Do not add kana readings to normal Japanese articles unless the article is specifically intended as language-learning material or the user asks for them.

## File and URL contract

Articles live under `_posts/` and use Jekyll front matter.

Use stable, readable ASCII slugs.

For Taiwanese Chinese:

```yaml
---
layout: post
title: "文章標題"
date: YYYY-MM-DD
locale: zh-tw
lang: zh-Hant-TW
translation_key: stable-article-key
permalink: /zh-tw/article-slug/
---
```

For Japanese:

```yaml
---
layout: post
title: "記事タイトル"
date: YYYY-MM-DD
locale: ja
lang: ja
translation_key: stable-article-key
permalink: /ja/article-slug/
---
```

Use the same publication date for both language versions unless the user intentionally wants separate publication dates.

## Mermaid contract

Mermaid diagrams are supported conditionally.

- Keep diagram source in standard fenced Markdown blocks using ` ```mermaid `.
- If an article contains any Mermaid block, add `mermaid: true` to that article's front matter.
- Apply `mermaid: true` independently to each language version that contains Mermaid.
- Do not add `mermaid: true` to articles without Mermaid diagrams.
- Do not replace Mermaid source with generated SVG during routine publishing; keep the Markdown portable.

Example:

```yaml
mermaid: true
```

## Publishing workflow

1. Confirm the article content to publish from the current conversation or supplied source.
2. Produce or finalize the Taiwanese Chinese version.
3. Produce the Japanese version with equivalent meaning and natural Japanese expression.
4. Choose one stable `translation_key` for both versions.
5. Detect whether each version contains Mermaid and set `mermaid: true` where required.
6. Create or update both `_posts/*.md` files.
7. Do not modify unrelated site files during routine publishing.
8. Commit changes to `main` unless the user explicitly requests another branch or review flow.
9. Verify the GitHub Pages build completes successfully.
10. Verify the expected public URLs for both language versions.
11. For Mermaid articles, verify the published page renders diagrams rather than showing raw Mermaid code when verification is available.
12. Report the published Taiwanese Chinese and Japanese URLs, plus any build or rendering failure or limitation.

## Update workflow

When editing an existing article:

- Find both versions using `translation_key` before modifying content.
- Preserve existing permalinks unless there is a strong reason to change them.
- Keep both versions semantically aligned when the edit changes meaning.
- A language-specific correction may update only one version if meaning remains equivalent.
- Add or remove `mermaid: true` if Mermaid usage changes.

## Completion criteria

Publishing is complete only when:

- Both expected language files exist unless the user explicitly requested one language only.
- `locale`, `lang`, `translation_key`, and `permalink` are correct.
- The paired versions share the same `translation_key`.
- `mermaid: true` is present exactly where Mermaid diagrams are used.
- The site architecture was not changed unnecessarily.
- GitHub Pages reports a successful build.
- The final response includes both public URLs.

If the Pages build fails, do not claim publication succeeded. Report the failure and diagnose it from the available build information.
