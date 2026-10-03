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

| ID               | Type       | File                                  | Name                                   | Description                                                        |
| ---------------- | ---------- | ------------------------------------- | -------------------------------------- | ------------------------------------------------------------------ |
| `greek-beginner-50` | flashcards | `Greek-Beginner-50.flashcards.zip` | Popular Greek Words — Beginner Top 50 | The 50 most common Greek words every beginner should know. |

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
    }
  ]
}
```

### Package JSON (`*.flashcards.json`)

```json
{
  "id": "greek-beginner-50",
  "name": "Popular Greek Words — Beginner Top 50",
  "description": "...",
  "language": "el",
  "category": "bible-languages",
  "version": 1,
  "createdAt": "2026-10-03",
  "cardCount": 50,
  "cards": [
    {
      "id": "greek-001",
      "front": "ἀγάπη",
      "back": "love; self-giving, unconditional love",
      "transliteration": "agapē",
      "partOfSpeech": "noun",
      "exampleRef": "1 John 4:8"
    }
  ]
}
```

Required card fields: `id`, `front`, `back`. Optional fields such as `transliteration`, `partOfSpeech`, and `exampleRef` may be included as appropriate for the language or topic.

## License

Copyright © Ecodia — https://ecodia.com
