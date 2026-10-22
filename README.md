# Pocket Blocks

A self-contained, touch-first block-clearing arcade game inspired by Ferry Halim's **Bauns**. This is an independent recreation with original code and graphics, not the original Flash game or an exact port. It contains no original SWF, music, or extracted art.

## Publish on GitHub Pages

1. Sign in at https://github.com and create a new **public** repository named `pocket-blocks`. If you're on an iPhone, using GitHub in Safari is easiest; request the desktop website if a control is missing.
2. Open the repository and choose **Add file → Upload files** (or **uploading an existing file** in an empty repository).
3. Upload `index.html` to the top level of the repository, then **Commit changes**. The filename must be exactly `index.html`, with no extra `.txt` extension. This single file is the whole game. You may also upload this README and `.nojekyll` if convenient; neither is needed to play.
4. Open the repository's **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**. Select branch **main**, folder **/(root)**, then **Save**.
5. Wait for GitHub to finish publishing, then open the address shown on the Pages settings screen. It will normally look like `https://YOUR-USERNAME.github.io/pocket-blocks/`.
6. On your iPhone, open that address in Safari. Optionally use **Share → Add to Home Screen**. This is a shortcut to the hosted game; offline availability is not guaranteed.

Official instructions: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site

If you downloaded the ZIP on iPhone, tap it in the Files app to extract it first. Upload the extracted **index.html**, not the ZIP. You don't need a paid GitHub account for Pages from a public repository.

## Play

- Touch the ball or its generous pickup halo, pull downward and sideways, then release. The tether is fixed at the original `(105,280)` board coordinate. The ball rests at the original `(106,300)` coordinate and returns there after every shot.
- The release position determines the landing position by reflection across the tether: `(landingX,landingY) = (210-releaseX,560-releaseY)` in the original 210 × 545 board coordinates. Pull farther down to land farther up. Pull right to land left.
- The ball is pulled within the original rectangle: x=20…190 and y=298…523. Touching an empty part of the board does not move it. A tap or interrupted touch cancels and returns it home.
- Airborne shots pass over intervening blocks. Only the final landing cell is hit; empty target cells miss. The flight uses the original 16 two-frame movement steps at 25 fps (1.28 seconds), with smooth visual interpolation and an added visual lift/shadow.
- Each landing hit removes the connected color group, even if it contains only one block. A group of N blocks scores `N × N × 10` points.
- A flashing block cycles through colors. Hitting it changes the remaining board to its displayed color.
- A numbered bomb begins at 9. Hitting it blasts the 5 × 5 area centered on it; affected color groups and bombs can cause further clearing. Both special types count down once every two seconds, and turn into ordinary colored blocks if they expire.
- The board uses the original 210 × 545 proportions. Its aiming grid reproduces the original vector outline, line width, yellow color, and alpha: horizontal line centers at y=330.35, 405.35, and 479.35; center vertical line at x=105. All positions scale uniformly with the board.
- Clearing the board earns 1,000 extra points and starts a fresh board.
- **Classic:** new blocks arrive every 8 seconds at first, gradually speeding up to every 3.5 seconds. Keep stacks under the top line.
- **Relaxed:** new blocks arrive every three completed shots, with no timer.
- Pause any time. Switching away from the page pauses automatically. Sound is off initially.
- Best scores are saved separately for both modes in this browser when local storage is available. No accounts or server are needed.
- Keyboard: click the game area, use left/right to aim, up/down to adjust power, Space to shoot, and P to pause/resume.

## Technical notes

Everything is in `index.html`: HTML, CSS, JavaScript, canvas graphics, and optional synthesized sound. There are no third-party dependencies, fonts, analytics, or network requests. Responsive layout, Pointer Events with pointer capture, a generous hit target, and `touch-action: none` address the missed-grab and page-scroll problems common in older mouse-driven games. Mouse and pen inputs work too.

Gameplay and balancing are recreated rather than copied exactly from Bauns. A real iPhone Safari playtest is still recommended. GitHub publication must be completed in your own account; no repository has been created or published for you.

## Verification

JavaScript syntax validation and automated checks pass for the original tether and resting coordinates, original drag limits, six reference pull-to-landing positions, offset pickup, cancellation, flying over intervening blocks, landing on an interior block, missing an empty cell, returning home after hits and misses, pause/resume, flashing recolor, countdown expiry, 5 × 5 bombs, new rows, game over, restarting, and drawing the scene. Physical iPhone Safari testing has not been performed.

## Revision 2

Replaced the substitute star and instant burst blocks with flashing recolor and countdown bomb blocks, and matched the aiming grid geometry and styling to the original game file. Original SWF files, art, and sound are not included. The remaining game is still an independent recreation; matching these features does not certify that all original physics, timing, visuals, or scoring are identical.

To update an existing GitHub Pages repository, replace its top-level `index.html` with this version and commit. Keep the current Pages settings. Wait for the deployment to finish, then reload Safari. If you still see the old version, close and reopen the page.

## Revision 3

Restored the fixed tether and resting point, the original pull rectangle and mirrored landing calculation, and landing-cell lookup. Removed horizontal repositioning, collisions with nearer blocks during flight, wall bouncing, and variable return positions. Block drawing and landing lookup now share the original cell geometry. The existing aiming grid and special blocks remain. This is still an independent recreation rather than a complete verified port of all original game behavior.
