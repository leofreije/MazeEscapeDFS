# Developer Log (DEVLOG.md)
## Expression Format Detector + Stack Evaluator (Spring 2026)

Minimum **6 entries** required.

Each entry must document learning and reasoning. Fabricated bugs are not expected.

---

## Allowed Entry Types
Each entry may be one of the following:

1) **Bug Fix Entry**
- The issue encountered.
- Error messages or symptoms.
- Attempts made.
- Final resolution.

2) **Edge Case / Testing Entry**
- A failure discovered through testing.
- The specific input/state that caused it.
- The change you made to handle it correctly.

3) **Engineering Decision Entry (up to 2 allowed)**
- A design decision you made.
- An alternative approach you considered.
- Why you chose one approach over another (tradeoffs).

---

### Entry 1
**Date:** 2026-04-19

**Entry Type:** Engineering Decision

**Task worked on:** Planning DFS Implementation with Pseudocode

**Issue or decision:** This was a difficult part of the design process, as I needed to decide how to structure the DFS function without actually fully writing code.

**Error message / symptom (if applicable):** N/A

**What I tried:** I considered creating helper methods for tracking the parents.

**Fix / resolution (or final decision):** I chose to use to same format of parameters as the template called of DFS in main in the same order. This makes the function avoid global variables and be consistent with the template.

**Commit(s):** Commit #2: DFS Pseudocode

---

### Entry 2
**Date:** 2026-04-20

**Entry Type:** Bug Fix Entry

**Task worked on:** Adding DFS base cases

**Issue or decision:** DFS was not stopping correctly and sometimes caused crashes.

**Error message / symptom (if applicable):** Segmentation fault when accessing invalid indices

**What I tried:** I added a test debug prints and hardcoded some values that would make the current cell go out of bounds

**Fix / resolution (or final decision):** I already had the checks for r >= maze.size() and c >= maze[0].size(), but I added r < 0 and c < 0. This addition ensured that the cells that went out of bounds by being too small were marked as false.

**Commit(s):** Commit #3: DFS Base Case Implementation

---

### Entry 3
**Date:** 2026-04-23

**Entry Type:** Bug Fix Entry

**Task worked on:** DFS visited tracking

**Issue or decision:** DFS had infinite recursion in some cases

**Error message / symptom (if applicable):** The program crashed

**What I tried:** I originally tried to check whether cells were being marked as visited after the recursion.

**Fix / resolution (or final decision):** I moved the statement "visited[r][c] = true;" to before the recursion but after the base cases. This correct prevented revisiting the same cells.

**Commit(s):** Commit #4: Added visited tracking in DFS

---

### Entry 4
**Date:** 2026-04-27

**Entry Type:** 

**Task worked on:** Find next row and column

**Issue or decision:** Edge Case / Testing Entry

**Error message / symptom (if applicable):** DFS returned false even though a path existed

**What I tried:** I tested with small mazes and then added temporary print statements to verify traversal.

**Fix / resolution (or final decision):** For each direction, I added "int next_r = r + dr[i];" and "int next_c = c + dc[i];" and ensure that these cell position are valid.

**Commit(s):** Commit #5: Added DFS traversal with dr & dc arrays

---

### Entry 5
**Date:** 2026-05-03

**Entry Type:** Bug Fix Entry

**Task worked on:** Parent Tracking in DFS

**Issue or decision:** printPath() did not output the correct path

**Error message / symptom (if applicable):** The incorrect path was printed when testing

**What I tried:** I checked the values in parent_r and parent_c vectors.

**Fix / resolution (or final decision):** I found that parent values ("parent_r[next_r][next_c] = r;" & "parent_c[next_r][next_c] = c;") needed to be assigned before the recursive DFS call. 

**Commit(s):** Commit #6: Added parent tracking in DFS

---

### Entry 6
**Date:** 2026-05-04

**Entry Type:** Testing 

**Task worked on:** Testing DFS behavior when no valid path exists

**Issue or decision:** I decided to test if I had considered all edge cases. 

**Error message / symptom (if applicable):** During some test runs, I could not tell if DFS was failing correctly or just stopping early due to a logic issue.

**What I tried:** I hard coded a maze that does not have a valid path and used temporary debug prints.

**Fix / resolution (or final decision):** I confirmed that DFS correctly explores possible paths and removed the debug prints and hardcoded maze.

**Commit(s):** Commit #9: Testing & Cleanup
