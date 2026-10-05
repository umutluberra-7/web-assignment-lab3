# University Course Management System

Run with `npm start` (or `node main.js`). Requires Node 14+; ES modules are enabled via `"type": "module"` in `package.json`.

## File organization
- `models.js` – `Student` class. `id` is defined with `Object.defineProperty` (`writable: false`, `configurable: false`). Has `addCourse` and `getAverage`.
- `database.js` – `fetchStudents(callback)` waits 2 seconds with `setTimeout`, then passes the raw data to the callback.
- `analytics.js` – `calculateClassAverage`, `findTopStudent` (uses `reduce`), and the higher-order `filterStudents`.
- `main.js` – entry point: fetches data, builds `Student` instances, tests immutability, prints the report.

## Challenges
- ES modules run in strict mode, so assigning to a read-only property throws a `TypeError` instead of failing silently. `main.js` wraps the attempt in `try/catch`.
- Getting `import`/`export` working in Node required `"type": "module"`.
- The sample output lists Zeynep as top student, but Ali's average (87.5) is higher than Zeynep's (82.5), so the program correctly prints Ali.
