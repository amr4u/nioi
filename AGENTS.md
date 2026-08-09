# nioi

Minimal bilingual publishing site built with GitHub Pages and Jekyll.

## Core rules

- Keep the site minimal, dependency-light, and easy to maintain.
- Taiwanese Chinese uses `locale: zh-tw` and `lang: zh-Hant-TW`.
- Japanese uses `locale: ja` and `lang: ja`.
- Two language versions of the same article must share the same `translation_key`.
- Do not change site architecture while publishing an article unless the article genuinely requires it.
- Treat repository content and configuration as the source of truth.
- Follow `.agent/skills/nioi-publisher/SKILL.md` for article publishing.

## Validation

After any change that affects the published site, verify the GitHub Pages build succeeds before considering the work complete.
