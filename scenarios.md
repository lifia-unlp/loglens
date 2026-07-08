# Use Case Scenarios (Cockburn Style)

## Scenario 1: Debugging an Active AI Session
**Primary Actor:** AI Developer / User
**Goal in Context:** To inspect the real-time internal state and tool executions of a currently running AI session in OpenCode or Antigravity.
**Scope:** Loglens Application
**Level:** User Goal
**Preconditions:** The user is actively running an AI session that logs to a local `transcript.jsonl` file.

**Main Success Scenario:**
1. The user opens `Loglens (index.html)` in their web browser.
2. The user clicks "Select Brain Folder".
3. The browser prompts the user to grant read access to a directory.
4. The user selects the `~/.gemini/antigravity/brain/` directory and confirms access.
5. Loglens scans the subdirectories, extracting conversation titles and modification dates.
6. A modal appears listing the conversations, with the active session appearing at the top (most recently modified).
7. The user clicks the active session.
8. Loglens loads the current state of the conversation and displays the list of messages on the left sidebar.
9. Loglens displays a blinking red indicator to denote "Live Sync" is active.
10. The AI generates new steps and appends them to the file on disk.
11. Loglens detects the file modification and automatically loads the new messages into the sidebar.
12. The user selects a new message to inspect its raw JSON and tool arguments.

**Extensions (Alternative Flows):**
- *3a. The user denies permission:* Loglens displays an error or fails gracefully. The user can fall back to the "Open Single File" method or static file input.
- *5a. The directory does not contain valid Antigravity log structures:* Loglens displays an empty state in the modal informing the user that no transcripts were found.

---

## Scenario 2: Reviewing Historical Tool Calls
**Primary Actor:** AI Developer / User
**Goal in Context:** To review the precise JSON arguments of a tool call made by the AI a week ago to understand why it failed.
**Scope:** Loglens Application
**Level:** Subfunction
**Preconditions:** The browser supports File System Access APIs.

**Main Success Scenario:**
1. The user opens Loglens.
2. The user uses the "Select Brain Folder" feature to load historical transcripts.
3. The user identifies the specific past conversation based on its extracted title and date.
4. The user clicks the conversation to load it.
5. The user utilizes the "Type Filter" dropdown to select `ACTION` or `TOOL_CALL`.
6. The sidebar filters out all standard text messages, leaving only tool executions.
7. The user clicks on the specific tool call in question.
8. The right panel displays the parsed tool call details and the raw, syntax-highlighted JSON data.
9. The user reads the exact arguments passed to the tool.

---

## Scenario 3: Sharing the App with a Colleague
**Primary Actor:** Developer
**Goal in Context:** To send the Loglens tool to a colleague who doesn't have a development environment set up.
**Scope:** File System / Network
**Level:** Summary
**Preconditions:** None.

**Main Success Scenario:**
1. The developer copies `index.html` from their local repository.
2. The developer sends the file via Slack or email to the colleague.
3. The colleague downloads `index.html` to their desktop.
4. The colleague double clicks the file.
5. It opens in Chrome and works immediately, without requiring npm installs or a local web server.
