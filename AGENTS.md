# Loglens Agent Guidelines

When working on the Loglens project, AI agents MUST adhere to the following core criteria:

1. **Standalone Architecture:**
   - Loglens must remain a single, self-contained HTML page (`index.html`) that can be executed directly from a local filesystem.
   - Do NOT introduce build steps, package managers (npm, yarn, bun), or local backend servers (Node, Express, Python) unless explicitly requested and approved by the user.
   - All CSS and Javascript MUST reside within the `index.html` file (or strictly client-side relative imports that do not require compilation).

2. **Lightweight & Fast:**
   - Keep the codebase light. Avoid importing massive external libraries via CDN unless absolutely necessary (e.g., Vue or React are prohibited for this vanilla app; stick to vanilla DOM manipulation).
   - The UI should load instantaneously.

3. **Read-Only Operations:**
   - Loglens is an inspector. The code MUST NEVER attempt to write, modify, delete, or alter any `.jsonl` or log files it is reading.
   - Use the `mode: 'read'` flag strictly when utilizing the File System Access API.

4. **Code Clarity and Modularization:**
   - Even though it is a single file, Javascript and CSS should be kept highly organized and modularized. 
   - Group related functions together (e.g., File Access logic, UI Rendering logic, JSON Parsing logic, Event Listeners).
   - Use clear variable names and encapsulate complex logic within well-named functions.
   - Maintain the existing GitHub Flavored Markdown (GFM) formatting for documentation.

5. **Aesthetics:**
   - Maintain the modern, clean, dark/light theme provided.
   - Do not use generic browser defaults.
