# theodia.flashcards

Flashcard packages for Theodia.

## Repository conventions

- **Flashcard packages live at the repository root.** Do not place them in subfolders such as `packages/`.
- **Each package must be a zipped file** named `{id}.flashcards.zip`.
- The archive should contain a single JSON file named `{id}.flashcards.json`.
- `index.json` registers all packages and points to the zip path.

## File format

### Package archive

```
greek-beginner-50.flashcards.zip
└── greek-beginner-50.flashcards.json
```

### `index.json`

```json
{
  "version": 1,
  "updatedAt": "2026-10-03T00:00:00.000Z",
  "packages": [
    {
      "id": "greek-beginner-50",
      "name": "Popular Greek Words — Beginner Top 50",
      "description": "...",
      "language": "el",
      "category": "bible-languages",
      "cardCount": 50,
      "path": "greek-beginner-50.flashcards.zip",
      "version": 1,
      "updatedAt": "2026-10-03"
    }
  ]
}
```

### Package JSON (`*.flashcards.json`)

```json
{
  "id": "greek-beginner-50",
  "name": "...",
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
