# Hermes_skill

Własne skille dla [Hermes Agent](https://github.com/NousResearch/hermes-agent).

| Skill | Opis |
|---|---|
| `skills/email/poczta-firmowa` | Czytanie firmowej skrzynki (IMAP) przez himalaya v2, tylko odczyt |
| `skills/email/imap-readonly` | Uniwersalna, angielska wersja powyższego (do publikacji, np. na Agensi); instrukcja w `references/SETUP.md` |

## Instalacja — Windows (natywny Hermes)

Hermes na Windowsie trzyma dane w `%LOCALAPPDATA%\hermes`, więc skill trafia do
`%LOCALAPPDATA%\hermes\skills\email\poczta-firmowa\SKILL.md`. W Git Bash:

```bash
git clone https://github.com/roberttomecki/hermes_skill ~/hermes_skill
mkdir -p "$LOCALAPPDATA/hermes/skills/email"
cp -r ~/hermes_skill/skills/email/poczta-firmowa "$LOCALAPPDATA/hermes/skills/email/"
```

Po `git pull` powtórz `cp -r`.

## Instalacja (WSL / Linux)

```bash
git clone https://github.com/roberttomecki/hermes_skill ~/hermes_skill
mkdir -p ~/.hermes/skills/email
ln -s ~/hermes_skill/skills/email/poczta-firmowa ~/.hermes/skills/email/poczta-firmowa
```

Dowiązanie (`ln -s`) sprawia, że po `git -C ~/hermes_skill pull` Hermes od razu widzi nową wersję.
