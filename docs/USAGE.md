# Playing Mental Math

[Back to the project](../README.md)

## Open the game

Use the hosted game linked from the README, or keep an offline copy:

1. Download the **offline ZIP** linked from the README and extract it.
2. Open **`Mental-Math-20.html`** in a modern web browser. The other file in the ZIP is the license.

You can also download the single HTML file, or choose **Code → Download ZIP** on GitHub, extract the repository and open **`index.html`**. All three options contain the same game. The page contains its own HTML, CSS and JavaScript and uses system fonts. Playing the downloaded file requires no installation, server, account, external library, API or internet connection. JavaScript must be enabled.

## Choose a mode

| Mode | Number rules |
| --- | --- |
| **Add & Subtract** | Both given numbers are integers from −20 to +20, inclusive. Answers can range from −40 to +40. |
| **Multiply & Divide** | Multiplication factors are integers from −10 to +10. For division, the dividend is between −100 and +100, the divisor is a nonzero integer between −10 and +10, and the answer is an exact integer between −10 and +10. |
| **Mixed Challenge** | Addition, subtraction, multiplication and division use the same rules as above. |

Every Multiply & Divide and Mixed round includes at least one division where **both numbers are negative**, for example `−45 ÷ (−5) = 9`. That required question is shuffled into a random position. Division questions are built from a whole-number answer and a nonzero divisor, so division by zero and fractional answers cannot occur.

## A round

Choose a mode card, then select its **Start** button. Type an integer, including a minus sign when needed. Press **Enter** or **Check** to submit it, then **Enter** or **Next** to continue. Feedback appears immediately; a mistake shows the correct answer. The progress indicator and mode label remain visible during the round.

[![A current Add & Subtract question with immediate correction after a demonstration mistake](../media/practice-small.png)](../media/practice.png)

After the last answer, **See Results** shows the mode, correct/wrong totals and a review of **all 20 questions**, submitted answers and correct answers. **Play This Mode Again** starts another round in the same mode. **Choose Another Mode** returns to the picker.

Each round contains **20 questions** without repeating the exact same ordered expression. The other operations are chosen randomly; the game does not promise equal numbers of each operation. A negative second operand is shown in parentheses. The game does not adapt difficulty or explain the calculation steps.

## Scores and celebrations

Each mode has a separate high score, saved-attempt count and history list. Selecting a different card switches the displayed history. An old saved attempt without a mode is treated as Add & Subtract, preserving the original practice history.

The first completed round establishes a score for that mode. A later round that beats that mode's saved best gets a new-high-score message and confetti. Every perfect 20/20 round gets **WOW! PERFECT SCORE!** and confetti. The animation is skipped when the browser reports a preference for reduced motion.

| Saved attempts in the selected mode | A perfect Mixed demonstration round |
| :---: | :---: |
| [![The current mode picker showing two saved Add & Subtract demonstration attempts](../media/history-small.png)](../media/history.png) | [![Mixed Challenge perfect-score results with confetti](../media/perfect-score-small.png)](../media/perfect-score.png) |

*Authentic browser captures using demonstration answers. The example scores are not student results.*

## Where progress is kept

Only **finished rounds** are saved. Each stored attempt contains its mode, completion time, score and submitted answers. The game retains the most recent **200 attempts in total across all modes** in browser `localStorage`. A mode's high score is the best among its retained attempts; it is not a permanent lifetime record after older attempts fall outside that limit.

Keep using the same browser and location to see the same history. A downloaded file and the hosted page have separate storage, and moving or renaming a local file may affect which saved history the browser makes available. Private browsing, blocked storage or clearing site data can also affect persistence. If saving is blocked, the game displays a warning and still lets you play. The game does not upload answers or synchronize them between devices.

**Clear all saved history** asks for confirmation before removing stored attempts for **every mode**, including the displayed high scores. Closing a page during a round does not save or resume that unfinished round.

## If something does not work

- **The page opens as text:** extract the ZIP first and open `Mental-Math-20.html` with a web browser, or use the repository's `index.html`.
- **An answer is rejected:** enter a whole number, such as `-7` using the keyboard's normal minus/hyphen key, or `12`. Decimals, words and empty answers are not accepted. Some phone number keyboards may require switching to the symbols layout to enter a minus sign.
- **A different mode has no scores:** each mode has its own history. Older attempts without a mode appear under Add & Subtract.
- **History is missing:** check that you are using the same browser and copy/location, and that browser storage is allowed. Storage behavior for files opened directly from disk varies between browsers.
- **No confetti:** the animation respects the browser's reduced-motion setting.

## Development notes and checks

The playable GitHub Pages entry point is **`index.html`**. The portfolio presentation is **`README.md`**, with this guide and authentic captures in `media`. The offline ZIP in `downloads` contains the same HTML under the shareable name `Mental-Math-20.html`, plus the existing MIT license. No build step or dependency installation is required.

The original portfolio preparation on **18 October 2026** checked complete addition/subtraction rounds, feedback, replay, celebrations, integer input and saved scores in a real desktop browser. The owner separately reported successful use of the original game with the student.

The **25 October 2026** three-mode update was checked again:

- Synthetic JavaScript checks exercised all three modes, 20-question flow, full review, replay, mode-specific history and high scores, confetti, reduced motion, blocked storage, the 200-attempt limit and compatibility with attempts that have no mode.
- **10,000 generated division questions** met the divisor, dividend and exact-integer-answer restrictions.
- **1,000 generated rounds per mode** contained 20 unique expressions within that mode's number rules. Every Multiply & Divide and Mixed round included double-negative division; shuffled questions appeared across all 20 positions during the checks.
- **Four complete desktop-browser demonstration rounds** covered all three modes, feedback, full results, keyboard input, replay and both celebration messages. Saved scores remained separate by mode after closing and reopening the tab.
- A **390-pixel-wide browser viewport** showed stacked mode cards without horizontal overflow. This checks the responsive layout; physical phone keyboards were not tested.
- The offline ZIP was checked against the playable HTML.

The publication copy retains the existing escaped-hyphen correction to the HTML answer pattern so current browsers enforce integer-only input. The relevant browser behaviour is described in [MDN's HTML pattern reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/pattern).

The test harnesses are development tools and are not needed to run the game. These focused checks do not establish wider cross-browser coverage, direct-file persistence across browsers, persistence after a full browser restart, or mobile-keyboard behaviour. The new modes have been exercised with demonstration answers; the earlier student's feedback concerns the original addition/subtraction game.
