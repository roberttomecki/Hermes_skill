# Hermes_skill

Własne skille dla [Hermes Agent](https://github.com/NousResearch/hermes-agent).

| Skill | Opis |
|---|---|
| `skills/email/poczta-firmowa` | Czytanie firmowej skrzynki (IMAP) przez himalaya v2, tylko odczyt |

## Instalacja (WSL / Linux)

```bash
git clone https://github.com/roberttomecki/hermes_skill ~/hermes_skill
mkdir -p ~/.hermes/skills/email
ln -s ~/hermes_skill/skills/email/poczta-firmowa ~/.hermes/skills/email/poczta-firmowa
```

Dowiązanie (`ln -s`) sprawia, że po `git -C ~/hermes_skill pull` Hermes od razu widzi nową wersję.
