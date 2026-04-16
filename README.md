# Quiz CLI

An interactive command-line quiz game for learning JavaScript and Node.js fundamentals.

This project is a small, dependency-free Node.js CLI app that loads quiz questions from a JSON file, lets the user pick a category and question count, and then runs a scored quiz session with explanations and a results summary.

## Features

- Interactive CLI prompts (category selection, question selection, play-again flow)
- Multiple categories (loaded from `data/questions.json`)
- Randomized question order (Fisher–Yates shuffle)
- Score tracking with a final results report and review of missed questions
- Colorized terminal output using ANSI escape codes (no external libraries)
- Modern JavaScript (ES Modules) and async/await

## Project Structure

```text
.
├── index.js
├── package.json
├── data/
│   └── questions.json
└── src/
    ├── colors.js
    ├── input.js
    └── quiz.js
```

### Key Files

- `index.js` — Application entry point. Loads questions, shows the banner, handles category/count selection, and runs the main game loop.
- `data/questions.json` — Question bank grouped by category.
- `src/quiz.js` — Core quiz logic (`Quiz` class): shuffling, asking questions, scoring, progress bar, and results.
- `src/input.js` — Readline-based input helpers (`select`, `confirm`, `pressEnter`, etc.).
- `src/colors.js` — Minimal ANSI color utilities for terminal output.

## Getting Started

### Prerequisites

- Node.js **>= 18** (required by `package.json`)

### Installation

```bash
git clone https://github.com/fedextm/test-app.git
cd test-app
npm install
```

> Note: This project has no runtime dependencies, but `npm install` is still useful for creating a lockfile and ensuring a consistent environment.

### Run

```bash
npm start
```

Or run directly:

```bash
node index.js
```

## Usage Examples

1. Start the app:

   ```bash
   npm start
   ```

2. In the terminal you will:
   - Choose a category (e.g., “JavaScript Basics”, “Node.js Fundamentals”, “General Programming”)
   - Choose how many questions to answer (All / 3 / 5 depending on availability)
   - Answer each question by entering the option number
   - Review your score and any missed questions
   - Choose whether to play again

## Customizing Questions

Edit `data/questions.json` to add categories or questions.

### JSON Format

- `categories` is an object keyed by a category id.
- Each category contains:
  - `name`: Display name
  - `questions`: Array of question objects

Each question object supports:

- `question` (string)
- `options` (string[])
- `answer` (number) — **0-based** index into `options`
- `explanation` (string, optional)

Example:

```json
{
  "question": "What keyword is used to declare a constant in JavaScript?",
  "options": ["var", "let", "const", "define"],
  "answer": 2,
  "explanation": "The 'const' keyword declares a block-scoped constant that cannot be reassigned."
}
```

## Scripts

From `package.json`:

- `npm start` — Runs the CLI (`node index.js`)
- `npm test` — Runs Node’s built-in test runner (`node --test`)

## Notes

- The quiz selects the first *N* questions from the chosen category before shuffling. To change selection logic (e.g., sample random questions from the full pool), update `index.js` and/or `src/quiz.js`.
- The repository currently contains a `.DS_Store` file (macOS metadata). It’s safe to remove and typically should be ignored via `.gitignore`.

## License

MIT
