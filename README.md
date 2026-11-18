# Claude Skills

Sammlung von Claude-Code-Skills. Jeder Skill liegt unter `.claude/skills/<name>/` und wird in jeder Claude-Code-Sitzung mit diesem Repository automatisch geladen.

| Skill | Quelle | Zweck |
|-------|--------|-------|
| `stop-slop` | [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) (MIT) | Entfernt typische KI-Schreibmuster aus Texten |
| `ui-ux-pro-max` | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (MIT) | UI/UX-Wissensdatenbank: Stile, Farbpaletten, Schriftpaare, UX-Regeln, Design-Systeme |
| `design` | ebenda | Logo, Corporate Identity, Icons, Banner, Präsentationen (Logo-Generator braucht eigenen API-Key) |
| `design-system` | ebenda | Design-Tokens, Komponenten-Specs, Folien |
| `brand` | ebenda | Markenstimme, visuelle Identität, Styleguides |
| `ui-styling` | ebenda | shadcn/ui, Tailwind, Canvas-Designs |
| `banner-design` | ebenda | Banner für Social Media, Werbung, Web und Print |
| `slides` | ebenda | HTML-Präsentationen mit Chart.js |
| `task-observer` | [rebelytics/one-skill-to-rule-them-all](https://github.com/rebelytics/one-skill-to-rule-them-all) (CC BY 4.0, Eoghan Henn und Mitwirkende) | Beobachtet Arbeitssitzungen und schlägt Verbesserungen für bestehende und neue Skills vor |
| `find-skills` | [vercel-labs/skills](https://github.com/vercel-labs/skills) (MIT) | Sucht passende Skills auf skills.sh und hilft beim Installieren |
| `tiktok-autopost` | eigener Skill | Postet fertige Clips mit den gespeicherten Standard-Einstellungen auf TikTok (über den Videos-Connector) |

Hinweis zu `ui-ux-pro-max`: Die Suchskripte brauchen Python 3 und werden vom Repo-Root aus aufgerufen (`.claude/skills/ui-ux-pro-max/scripts/search.py`).

Hinweis zu `find-skills`: Mit `npx skills add … -g` installierte Skills landen im Container und sind nach einer Cloud-Sitzung wieder weg. Damit ein Skill dauerhaft bleibt, gehört er in dieses Repo unter `.claude/skills/`.
