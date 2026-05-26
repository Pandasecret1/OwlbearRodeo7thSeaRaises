Raises Calculator — Owlbear Rodeo Extension
A d10 dice pool raise calculator for Owlbear Rodeo. Input any number of d10 dice and instantly see the optimal grouping to maximise raises.
Features
Optimal Raise Calculation — Finds the best possible grouping via dynamic programming (exact for ≤16 dice, greedy for larger pools)
Manual or Auto Roll — Roll directly in the extension or enter your own die results
Reroll Lowest Die — Rerolls the lowest die and keeps the better result
Fifteen Rule — Groups totalling 15+ count as 2 raises
10s Explode — Rolling a 10 adds an extra die (chains infinitely)
All options combinable
Files
```
raises-calculator/
├── manifest.json   ← OBR extension manifest
├── icon.svg        ← Toolbar icon
├── index.html      ← Full extension UI (self-contained)
└── README.md
```
Installation
Option A — Host it yourself (recommended)
Upload all three files (`manifest.json`, `icon.svg`, `index.html`) to any static web host (GitHub Pages, Netlify, Vercel, etc.).
Make sure `manifest.json` is accessible at e.g. `https://yourdomain.com/raises-calculator/manifest.json`
In Owlbear Rodeo, open your Profile → Add Extension and paste that URL.
Enable the extension when creating or editing a room.
Option B — Local dev with Vite / any dev server
```bash
cd raises-calculator
npx serve .
# Extension will be at http://localhost:3000
# Use http://localhost:3000/manifest.json as install URL
```
> **Note:** Owlbear Rodeo requires extensions to be served over HTTPS in production. For local testing it accepts `localhost`.
How Raises Work
Rule	Effect
Default	Any group of dice summing to ≥ 10 = 1 raise. Extra beyond 10 is wasted.
Fifteen Rule	A group summing to ≥ 15 = 2 raises
10s Explode	Any 10 rolled → roll another d10 (added to pool, can chain)
Reroll Lowest	After initial roll, the single lowest die is rerolled; higher result kept
Solver Algorithm
For pools of ≤ 16 dice, the extension uses a bitmask dynamic programming approach that guarantees the globally optimal grouping.
For 17+ dice, it uses a fast greedy search that finds a near-optimal solution efficiently.
