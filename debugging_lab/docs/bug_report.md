# Lemon Clicker Bug Report

**Name:** Kiame McCartha
**Tickets solved:** <!-- e.g. 1, 2, 3, 5, 6 (at least five) -->

Copy the template below once for each ticket you solved. 

---

## Ticket <1>: <Stats always say "Stats unavailable">

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:**
The bug was in the file, MenuScreenController.ts
in the function, private async loadStatsFromServer(): Promise<LeaderboardStats>

**What was wrong:**

### Fix

<!-- What did you change, and why does that change fix the problem? -->

The fetch call was calling fetch("/api/stat"); instead of fetch("/api/stats");
There was an 's' missing.

### How did you find it?
I looked in my devtools where all the fetches are being called, and it led me to the function
where the stats are


#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**


#### Backward tracing

<!-- Start from the symptom you saw and work backwards, one step at a time,
     until you reach the buggy line. For each step, note where you looked
     and what you saw there. Add steps as needed. -->

1. **Symptom:** <!-- what you saw, e.g. text on screen, console error -->
2. **Traced back to:** <!-- where that came from, e.g. a function, a request in the Network tab, a server log -->
3. **Traced back to:**
4. **Buggy code:** <!-- the file, function and line where the trace ended -->

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

1. I saw "stats unavailable" where I was supposed to see stats
2. I first went to where the string "stats unavailable was being called"
3. Then went to my devtools and saww all the fetches
4. a line of code in was spelled wrong

### Confirming the fix

<!-- How did you confirm the problem is gone? -->
I reloaded the game, and I saw the desired output


## Ticket <2>: <Best score always shows 0>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:**
The bug was in the file, index.ts
in the function, app.get("/api/stats", (_req, res) =>

**What was wrong:**

### Fix

<!-- What did you change, and why does that change fix the problem? -->

The function was updating the best score if the score was lower. Since you can't get a lower
score than 0, the best score remained 0. I had to change the function so that the best score 
gets updated whenever the score is greater than the previous best score.

### How did you find it?



#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

"If the 0 value is in the variable "best", the error must be in the calculation of "best""
this led me to identifying the buggy code because I knew exactly what to look for.


#### Backward tracing

<!-- Start from the symptom you saw and work backwards, one step at a time,
     until you reach the buggy line. For each step, note where you looked
     and what you saw there. Add steps as needed. -->

1. **Symptom:** <!-- what you saw, e.g. text on screen, console error -->
2. **Traced back to:** <!-- where that came from, e.g. a function, a request in the Network tab, a server log -->
3. **Traced back to:**
4. **Buggy code:** <!-- the file, function and line where the trace ended -->

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->


### Confirming the fix

<!-- How did you confirm the problem is gone? -->
I reloaded the game, and I saw the desired output

## Ticket <3>: <The lemon only lands in four spots>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:**
The bug was in the file, GameScreenView.ts
in the function, randomizeLemonPosition(): void

**What was wrong:**

### Fix

<!-- What did you change, and why does that change fix the problem? -->

The function was rounding the random position of the lemon, which just left 4 options for the lemon to move. I had to remove Math.Random in order to alow more spaces on the screen for the lemon to move.

### How did you find it?



#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

"If the issue was what I was seeing in the gameplay, the issue must be in the GameScreenView.ts file". When I checked the file, I looked for the function that was randomizing the position, and fixed the error.


#### Backward tracing

<!-- Start from the symptom you saw and work backwards, one step at a time,
     until you reach the buggy line. For each step, note where you looked
     and what you saw there. Add steps as needed. -->

1. **Symptom:** <!-- what you saw, e.g. text on screen, console error -->
2. **Traced back to:** <!-- where that came from, e.g. a function, a request in the Network tab, a server log -->
3. **Traced back to:**
4. **Buggy code:** <!-- the file, function and line where the trace ended -->

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->


### Confirming the fix

<!-- How did you confirm the problem is gone? -->
I reloaded the game, and I saw the desired output compared to the way the gameplay was functioning before I made the changes.


## Ticket <4>: <Stuck on the Game Over screen>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:**
The bug was in the file, GameScreenController.ts
in the function, private endGame(): void

**What was wrong:**

### Fix

<!-- What did you change, and why does that change fix the problem? -->

In the function, this.stopTimer(); wasn't being called because there were no parenthesis after. Because the timer wasn't stoping, the timer was staying at 0, and kept reloading the game over screen. I had to add the parenthesis after in order to call the function

### How did you find it?



#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**


#### Backward tracing

<!-- Start from the symptom you saw and work backwards, one step at a time,
     until you reach the buggy line. For each step, note where you looked
     and what you saw there. Add steps as needed. -->

1. **Symptom:** <!-- what you saw, e.g. text on screen, console error -->
2. **Traced back to:** <!-- where that came from, e.g. a function, a request in the Network tab, a server log -->
3. **Traced back to:**
4. **Buggy code:** <!-- the file, function and line where the trace ended -->

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

1. The page kept reloading the game over screen, and even when pressing play again, the screen would automatically reload to the game over screen
2. This led me to checking the stopTimer function to check if it was working properly, which it was. 
3. So I then checked which other methods were using stopTimer, which led me to the endGame() method 
4. the stopTimer() function wasn't being called correctly


### Confirming the fix

<!-- How did you confirm the problem is gone? -->
I reloaded the game, and I was able to play the game again without it automatically reloading the game over screen again.

## Ticket <5>: <Leaderboard dates show "undefined">

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:**
The bug was in the files, ResultsScreenView.ts and ResultsScreenModel.ts
in the functions updateLeaderboard(entries: LeaderboardEntry[]): void
and export type LeaderboardEntry =

**What was wrong:**

### Fix

<!-- What did you change, and why does that change fix the problem? -->

In both functions, they don't use the correct variable for the dates as the one used in the index.ts. Because of this, I had to change both files so that the correct variable is used
### How did you find it?



#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**


#### Backward tracing

<!-- Start from the symptom you saw and work backwards, one step at a time,
     until you reach the buggy line. For each step, note where you looked
     and what you saw there. Add steps as needed. -->

1. **Symptom:** <!-- what you saw, e.g. text on screen, console error -->
2. **Traced back to:** <!-- where that came from, e.g. a function, a request in the Network tab, a server log -->
3. **Traced back to:**
4. **Buggy code:** <!-- the file, function and line where the trace ended -->

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

1. The page kept showing dates as "undefined" instead of actual dates
2. This led me to checking the variable for time in the index.ts 
3. I checked for which methods were using time, and found out that the ones that did were using timestamp instead of time. 
4. I had to rename the variables in those 2 functions to match the variable holding the dates in the index.ts


### Confirming the fix

<!-- How did you confirm the problem is gone? -->
I reloaded the game, and when the game ended, I was able to see the correct timestamps
