# theodia.flashcards

Flashcard packages for Theodia.

## Repository conventions

Files in this repository follow [`notes/github-repo-naming-standards.md`](https://github.com/ecodiallc/theodia.app/blob/main/notes/github-repo-naming-standards.md):

- **Flashcard packages live at the repository root.** Do not place them in subfolders such as `packages/`.
- **Each package must be a zipped file** at the root, named with sentence-case-dash words + `.flashcards.zip`.
  - Example: `Greek-Beginner-50.flashcards.zip`
- **The archive must contain exactly one JSON file** named with the same sentence-case-dash base + `.flashcards.json`.
  - Example: `Greek-Beginner-50.flashcards.json`
- Do not include loose images, folders, or sidecar files inside the archive.
- `index.json` registers all packages and points to the `.flashcards.zip` path.

## Catalog

<!-- Keep this table in sync with index.json -->

| ID                          | Type       | File                                   | Name                              | Description                                                  |
| --------------------------- | ---------- | -------------------------------------- | --------------------------------- | ------------------------------------------------------------ |
| `greek-beginner-50`         | flashcards | `Greek-Beginner-50.flashcards.zip`     | Popular Greek Words — Beginner Top 50 | The 50 most common Greek words every beginner should know. |
| `popular-verses-top-25-kjv` | flashcards | `Popular-Verses-Top-25.flashcards.zip` | Popular Verses — Top 25 (KJV)     | 25 of the most popular and memorized Bible verses from the King James Version. |

## Installation

Add this repository in **Theodia → Settings → GitHub Repositories** using the repository URL, then install items from **Settings → Manage Resources**.

## File format

### Package archive

```
Greek-Beginner-50.flashcards.zip
└── Greek-Beginner-50.flashcards.json
```

### `index.json`

```json
{
  "version": 1,
  "updatedAt": "2026-10-03T00:00:00.000Z",
  "packages": [
    {
      "id": "greek-beginner-50",
      "type": "flashcards",
      "path": "Greek-Beginner-50.flashcards.zip",
      "name": "Popular Greek Words — Beginner Top 50",
      "description": "The 50 most common Greek words every beginner should know.",
      "language": "el",
      "category": "bible-languages",
      "cardCount": 50,
      "version": "1.0.0"
    },
    {
      "id": "popular-verses-top-25-kjv",
      "type": "flashcards",
      "path": "Popular-Verses-Top-25.flashcards.zip",
      "name": "Popular Verses — Top 25 (KJV)",
      "description": "25 of the most popular and memorized Bible verses from the King James Version.",
      "language": "en",
      "category": "bible-memory",
      "cardCount": 25,
      "version": "1.0.0"
    }
  ]
}
```

### Internal package JSON (`*.flashcards.json`)

The archive must contain exactly one JSON file with this top-level shape. The app validates this structure before importing the deck.

```json
{
  "version": 1,
  "deck": {
    "name": "Popular Greek Words — Beginner Top 50",
    "description": "The 50 most common Greek words every beginner should know.",
    "isReadOnly": true,
    "cards": [
      {
        "reference": "1 John 4:8",
        "front": "ἀγάπη",
        "back": "love; self-giving, unconditional love",
        "contentType": "qna",
        "metadata": {
          "transliteration": "agapē",
          "partOfSpeech": "noun",
          "originalId": "greek-001"
        }
      }
    ]
  }
}
```

Required fields:

| Field                    | Type   | Purpose                                                                                     |
| ------------------------ | ------ | ------------------------------------------------------------------------------------------- |
| `version`                | number | Internal backup format version. Must be `1`.                                                |
| `deck.name`              | string | Display name for the installed deck.                                                        |
| `deck.cards`             | array  | Array of card objects.                                                                      |
| `deck.cards[].reference` | string | Required card reference. Use a verse reference or stable key; the app rejects empty values. |
| `deck.cards[].back`      | string | Required answer / back side of the card.                                                    |

Optional fields:

| Field                       | Type   | Purpose                                                                                                                                                   |
| --------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `deck.description`          | string | Human-readable deck description.                                                                                                                          |
| `deck.isReadOnly`           | bool   | If `true`, the user cannot edit the deck inside the app. Recommended for GitHub-sourced decks.                                                            |
| `deck.cards[].front`        | string | Question / front side of the card.                                                                                                                        |
| `deck.cards[].contentType`  | string | `"verse"` (default), `"qna"`, or another type supported by the app. Use `"qna"` for non-bible language cards so the review screen keeps the `back` text. |
| `deck.cards[].metadata`     | object | Extra structured data such as `transliteration`, `partOfSpeech`, `originalId`, etc.                                                                       |

**Important:**
- Do not put `cards` at the top level. The app importer expects `deck.cards`.
- Every card must have a non-empty `reference`; a bare `id` alone is not sufficient.
- `version` in this JSON is the backup-format version (`1`), not the content version of the deck.

## License

Copyright © Ecodia — https://ecodia.com
