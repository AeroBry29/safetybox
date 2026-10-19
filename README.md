# SH&W Chapter Matching Game — individual play

A static game for GitHub Pages. No Apps Script, rooms, administrator, login, names, avatars, shared timer or leaderboard. Each browser runs its own game and calculates its own score.

## Player flow

Play now → instructions → I'm ready → 3…2…1 → game → score and board review → reveal correct answers.

The default timer is 10 minutes. The timer begins after the countdown, continues when the tab is hidden and ends the game automatically. Players can finish early using Finish game and confirmation. Refreshing the same tab restores the game and its original deadline when session storage is available. Play again begins a fresh, shuffled game.

Place a note by dragging or by selecting it and then clicking/tapping a board. Keyboard players can select a note with Enter and then Tab to a board and press Enter. On phones, hold briefly to start a drag; tap-to-place is also available. Notes stay visible on their boards and can be moved again. Expand View trash to move a card out of the trash. Return selected to pile puts it back among the unplaced notes. Next unplaced note cycles the pile without placing anything.

Correct regular card on its chapter: +1. Wrong chapter, unplaced or regular card in trash: 0. Distractor in trash: 0. Distractor on a chapter board: −2. Unplaced distractor: 0. Scores may be negative. Maximum score is the number of regular cards. Results show green correct placements, red incorrect placements and gray unplaced notes. Revealing answers groups all notes under the correct destinations while retaining the result colors.

## Timer and sound settings

Open the gear beside AIRBUS. Enter **safetybox** to unlock the duration field, set 1–120 whole minutes, and Save duration. The eye button shows/hides the password. Sound effects and background music are in the same dialog; music is off initially. Audio is synthesized locally and has no external media downloads.

Duration changes are saved only in this browser on this device, and apply to future games. They do not change an active game's deadline or anyone else's device. If browser storage is unavailable the selection lasts only for the open page. To change the default for newly visiting devices, edit `defaultMinutes` in config.js and publish the change; devices with a saved preference keep it. No centralized setting service exists in this edition.

The password is a convenience gate, not secure authentication: GitHub Pages serves the source code to the browser. A technical user can inspect the password and answers. This game is for practice, not a tamper-proof assessment. Scores are not uploaded or collected.

## Replace the sample scenarios

This package contains **16 sample scenarios**, not your approved work-sheet content. Do this before workplace use:

1. In Google Sheets, select the `Script` tab containing the matching-game data.
2. Download that tab as CSV (File → Download → Comma-separated values).
3. Rename the downloaded file **cards.csv**, and replace the included cards.csv in the website repository.
4. Keep the exact five headers in A1:E1:

   `Chapter Ref,Chapter Name,Concept,Card #,Post-it Card Scenario`

5. Every regular row needs all five values. Use `Distractor` in Chapter Ref for trash cards; their Chapter Name and Concept can be blank. Card # must be unique. Rows for the same Chapter Ref must use exactly the same chapter name and concept.
6. Keep Chapter Ref as text in your spreadsheet, especially values such as `7.1`, `7.2`, `7.10`. They are sorted naturally, not converted to decimal numbers. If your spreadsheet converts `7.10` to `7.1`, correct the cell before exporting.
7. In config.js, set `sampleContent: false` to remove the sample-content banner.

You can continue maintaining your data in Sheets; export and replace cards.csv whenever it changes. This is a snapshot, not a live connection to Google Sheets. CSV fields containing commas, line breaks or quotes must be properly quoted—Sheets' CSV export handles this. Blank rows are ignored. The game displays useful errors for bad headers, missing fields, duplicate IDs or inconsistent chapters.

New sessions use the latest CSV. A resumed game retains its original data snapshot. Choose Play again after finishing to use freshly loaded data.

## Deploy to GitHub Pages

1. Extract the ZIP. Create a GitHub repository, for example **shw-matching-game**, using the repository visibility and GitHub plan permitted by your organization. GitHub Free supports Pages from public repositories. Only upload workplace content approved for your chosen hosting/access arrangement; a standard Pages site is publicly accessible.
2. Open the repository → **Add file → Upload files**. Upload **the contents** of this folder, not the ZIP and not an extra outer folder. Commit the files to `main`.
3. The root must contain lowercase **index.html**, plus **styles.css**, **app.js**, **config.js**, **cards.csv** and **.nojekyll**. README.md is optional. Do not upload Code.gs or the old Apps Script Index.html.
4. Open repository **Settings → Pages**. Under Build and deployment, set Source to **Deploy from a branch**. Choose **main** and **/ (root)**, then **Save**.
5. Wait for the deployment to finish. GitHub Pages will show the site link, normally `https://YOUR-USERNAME.github.io/shw-matching-game/`. Use the Pages link, not the repository/file-preview link.
6. Test the link on a phone and desktop: Play now → instructions → I'm ready → countdown. Check placement, editing a posted note, trash and results. Open the gear and test the password and a shorter duration. Restore 10 minutes afterwards if desired.

Updates: edit or upload replacement files to `main` and commit. Pages republishes the site. Reload to get the changed application. Finish an existing saved game before testing new content, or open a fresh private window.

Official references:
- [Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## Files and local preview

- index.html: page structure and settings dialogs.
- app.js: gameplay, scoring, timer, CSV reader and local audio.
- styles.css: responsive layout; change `--yellow` to adjust the theme.
- config.js: title, default timer, password, CSV filename and sample banner.
- cards.csv: editable chapter/scenario database.
- .nojekyll: static-site publishing marker.

No build, package install, API key or backend is needed. For a local preview, run a web server in this folder, for example `python -m http.server 8000`, then open `http://localhost:8000`. Double-clicking index.html may fail because browsers restrict fetching the CSV from file URLs.

Brand text and all game resources are local; the page does not depend on an external logo, font or music host. No game is published by extracting this package; follow the deployment steps above.

## Verification

Local browser checks passed for the Play/instructions/countdown flow, password and saved duration, desktop dragging and tap placement, posted-card moves, distractor penalties, CSV quoting and decimal-style reference sorting, refresh/resume and deadline expiry, answer boards, phone-width overflow and finish confirmation. No browser JavaScript errors were recorded. Visual previews were inspected on desktop and phone widths. The package has not been published or tested on your GitHub/work network.

