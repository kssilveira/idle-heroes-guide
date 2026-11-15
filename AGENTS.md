# Agent Context & Maintenance Guide (`Idle Heroes F2P Guide`)

This document provides complete domain, structural, and technical context for AI coding agents working on this repository. Keep this repository strictly free of any proprietary, internal, or machine-specific paths/credentials.

---

## 1. Overview & Editorial Philosophy

`README.md` is a streamlined, single-path Free-to-Play (F2P) *Idle Heroes* progression guide from **Day 1 (0 Heroes)** to **6 Transcendence Heroes**:

> **Eloise → GSSW (1st Trans) → LFA + SQH (2nd Trans) → PDE (3rd Trans) → TBB (4th Trans) → DGN (5th Trans) → LBRM (6th Trans)**

### Core Simplification Rules
1. **Strictly Single-Path & Deterministic:** Never add branching routes, "situational" hero swaps, alternative Transcendence orders (e.g., `HHA` was intentionally excluded), or alternative artifact lists (e.g., `Ruyi Scepter`, `Antlers Cane`, and `Magic Source` were intentionally excluded).
2. **One Fixed Enable Setup per Role:** Never add situational Enable swap notes. All heroes permanently use `4` (**CC Purify**) in `E3` and `2` (**Unbending Will**) in `E5`.
3. **Unified Stage Tables (`Stage 0`–`Stage 7`):** Every stage uses a single 11-column table listing the 6 **Active Lineup** heroes (`Pos 1`–`Pos 6`) first, followed by off-field **Cloud Island Tenants** (`—`).
4. **Unicode Arrows Only:** Always use Unicode `→` in prose and tables (never LaTeX `$\rightarrow$`, which fails to render inside GitHub Markdown tables).

---

## 2. Repository Structure & Asset Sources

- `README.md`: The complete guide with inline HTML `<img>` icons embedded across all tables and checklists.
- `assets/heroes/` (`23` PNGs — `78×78` gold-framed hero portraits with top-left faction badges):
  - **Upstream Source:** `https://raw.githubusercontent.com/HowLongBean/idleheroes.github.io/main/Cloud/Tenant/<upstream_name>.png`
  - **Filename Mapping (`local` ← `upstream`):**
    - Non-Transcendence (`16`): `eloise.png`, `ignis.png`, `waldeck.png`, `tix.png`, `carrie.png`, `onkirimaru.png`, `jahra.png`, `drake.png`, `mockman.png`, `sun-wukong.png` (`wukong.png`), `aspen.png`, `queen.png`, `elena.png`, `betty.png`, `natalie.png` (`natalia.png`), `melissa.png`.
    - Transcendence (`7`): `gssw.png` (`wukong_trans.png`), `lfa.png` (`aspen_trans.png`), `sqh.png` (`queen_trans.png`), `pde.png` (`elena_trans.png`), `tbb.png` (`betty_trans.png`), `dgn.png` (`natalia_trans.png`), `lbrm.png` (`melissa_trans.png`).
    - *Note for future additions:* `holmes.png` (`Holmes Young`) and `rogan.png` (`Rogan`) exist in the exact same upstream `Cloud/Tenant/` directory with matching dimensions and borders.
- `assets/factions/` (`7` PNGs — `shadow.png`, `abyss.png`, `fortress.png`, `forest.png`, `dark.png`, `light.png`, `transcendence.png`):
  - **Upstream Source:** `https://raw.githubusercontent.com/Ramulica/Idle-Heroes-F2P-Perspective/main/frontend/src/assets/stats/factions/<faction>.png`
- `assets/artifacts/` (`4` PNGs):
  - **Upstream Source:** `https://raw.githubusercontent.com/Ramulica/Idle-Heroes-F2P-Perspective/main/frontend/src/assets/stats/artifacts/<arti-id>.png`
  - **Filename Mapping (`local` ← `upstream`):**
    - `golden-crown.png` ← `arti-10.png`
    - `melodic-strings.png` ← `arti-12.png`
    - `demon-bell.png` ← `arti-06.png`
    - `illusive-mirror.png` ← `arti-25.png`

### Inline Image Sizing Conventions in `README.md`
Standard Markdown `![]()` cannot control image dimensions inside GitHub tables; always use `<img src="assets/..." width="..." align="absmiddle">`:
- **Quick Reference Table:** `width="28"` for hero portraits, `width="20"` for `Base Faction` icons, `width="18"` for `transcendence.png` in the `Acronym` column.
- **Master Progression Timeline:** `width="22"` for all inline hero portraits.
- **Master Artifact Build Order:** `width="26"` for artifact icons, `width="22"` for hero portraits.
- **Stage-by-Stage Tables (`Stage 0`–`Stage 7`):**
  - Primary hero portrait: `width="26"`
  - Base hero portrait inside parentheses (on Transcendence rows): `width="18"`
  - Faction badge inside parentheses: `width="16"`
  - Artifact icon in the `Artifact` column: `width="24"`
- **Summary Priority Checklists:** `width="20"` for hero portraits.

---

## 3. Verified In-Game Mechanics & Data Invariants

### Lineup Positioning & Suicide Supports
- **`Pos 1`:** Main Tank-Carry (`Eloise` in Stages 0–2; `LFA` in Stages 3–7).
- **`Pos 2`:** `Ignis (9*)` in Stages 0–4 (kept at `9*` Level 100 with no gear/stone/artifact so she dies in Round 1 and feeds 100 Energy + 100% Control Immunity directly to `Pos 1`).
- **`Pos 3`:** `Waldeck (9*)` in Stages 0–2 (kept at `9*` Level 100 naked so he dies in Round 1 and buffs Attack/bleeds for `Eloise`). Retired starting at Stage 3.

### Cloud Island Tenant Slots
- **Eloise (Homeowner in Stages 1–2):**
  - `Slot 1`: `Onkirimaru` (Shadow)
  - `Slot 2`: `Jahra` (Shadow)
  - `Slot 3`: `Tix` (Shadow)
  - `Slot 4`: `Carrie` (Dark)
- **LFA (Permanent Homeowner in Stages 3–7):**
  - `Slot 1`: `Drake` (Dark)
  - `Slot 2`: `SQH` (Transcendence — Queen / Abyss)
  - `Slot 3`: `Onkirimaru` (Shadow — carried over from Eloise's house)
  - `Slot 4`: `PDE` (Transcendence — Elena / Dark; `Mockman` is used as a temporary Dark tenant in Stage 3)

### Enables (`E1`–`E5`)
Exact in-game UI slot order:
- **`E1` & `E4`:** `1` = `+12% HP`, `2` = `+8% Atk`, `3` = `+6% HP, +4% Atk, +20 Spd`
- **`E2`:** `1` = `-15% Crit Dmg Received`, `2` = `+12% Extra Dmg`, `3` = `+15% Healed Effect`
- **`E3`:** `1` = Heal Self (`15%` missing HP), `2` = Self Atk (`+1.2%` per hero), `3` = Mark Purify, `4` = **CC Purify**, `5` = DoT Purify, `6` = Attr Reduction Purify
- **`E5`:** `1` = Self HP on Crit or `+30%` Dmg (*Balanced Strike*), `2` = **Fatal Damage Shield** (*Unbending Will*)

Locked presets used across all tables:
- **`2-2-4-2-2`:** Carry & Pure Tenants (`LFA`, `GSSW`, `Onkirimaru`, `Jahra`, `Tix`, `Carrie`, `Drake`, `Mockman`)
- **`3-1-4-3-2`:** Speed Supports (`SQH`, `PDE`, `DGN`, `LBRM`)
- **`1-1-4-1-2`:** Tank-Carry & CC (`Eloise`, `TBB`)

### Void Imprints
- Selectable Void Imprint nodes **only exist for Transcendence heroes** (non-Transcendence heroes have fixed imprint stat nodes and show `—` in the `Void Imprints` column; non-Trans tenants remain at `V0 (E5)` so all Stellar Shards go into Transcendence heroes).
- **Carry (`GSSW`, `LFA`):** `Crit Dmg / Holy Dmg / Precision`
- **Supports (`SQH`, `PDE`, `TBB`, `DGN`, `LBRM`):** `Dmg Red / Armor / Block`

### Artifact & Speed Order Rules
- **Master Artifact Order (`7` steps):**
  1. `1× Base Golden Crown` (`Eloise`, Stages 0–2)
  2. `1× Splendid Melodic Strings` (`Tix` Stage 1 → `GSSW` Stage 2 → `LFA` Stages 3–7)
  3. `1st Splendid Demon Bell` (`SQH`, Stages 3–7)
  4. `2nd Splendid Demon Bell` (`PDE`, Stages 4–7)
  5. `1× Splendid Illusive Mirror` (`TBB`, Stages 5–7)
  6. `3rd Splendid Demon Bell` (`DGN`, Stages 6–7)
  7. `4th Splendid Demon Bell` (`LBRM`, Stage 7)
- **Round 1 Speed Order:** Every Speed-stone Demon Bell support (`SQH` in Stage 3; `SQH, PDE` in Stages 4–5; `SQH, PDE, DGN` in Stage 6; `SQH, PDE, DGN, LBRM` in Stage 7) must be faster than `LFA` (`> LFA`) to feed energy and stack buffs before `LFA` casts his Active. `TBB`'s speed does not matter because her `1* Core` + `Splendid Illusive Mirror` starts her at 100 Energy and triggers AoE Twine passively after the first action of Round 1.

### Sublimation, Core of Origin & Destiny Transition (`DT`) Math
- **Sublimation Essence:** `45,000` per node (`180,000` per 4-node branch; `720,000` for `4/4/4/4` Full Sublimation).
- **Core of Origin Shards:**
  - `1* Primary Core` = **`100` Core Shards** (`2×` 50-shard chests)
  - `3* Noble Core` = **`400` Core Shards** (`8×` 50-shard chests total)
- **Destiny Transition (`DT`) Prerequisites:** Requires **`T5 (Lvl 120)`** + **`4/4/4/4` Full Sublimation** + **`3* Noble Core`**.
  - `1st DT`: `LFA` (Stage 5)
  - `2nd DT`: `SQH` (Stage 6)
  - `3rd DT`: `PDE` (Stage 7)

---

## 4. Pending Enhancement: Tree of Origin Glory Challenges & Seal Land 20

The user asked how to integrate the **Tree of Origin Glory Challenges** and **all 6 Seal Land 20 clears** with the simplest logic and fewest new heroes. Below is the verified design awaiting the user's confirmation on two small choices before editing `README.md`.

### Verified Mechanics & Upgrade Costs
1. **No Transcendence Heroes Allowed in Either System:**
   - Both **Tree of Origin Glory Challenges** and **Seal Land 1–20** strictly require **non-Transcendence base-faction heroes** (`Shadow`, `Abyss`, `Fortress`, `Forest`, `Light`, `Dark`). Transcendence heroes only unlock in Seal Land `21+`.
2. **Active Tree of Origin Locks Direct Transcendence:**
   - A base hero can be transcended directly with `V1`–`V4` Void Imprints intact, but **cannot** click *Transcend* while any **Tree of Origin** levels (`T1`–`T5`) are unlocked. It must be regressed first (`5 Soul Symbols`).
3. **Exact Cumulative Upgrade Costs (from `E5`):**
   - `V4`: `4,935,000` Stellar Shards (`V1: 138,630` + `V2: 587,910` + `V3: 1,458,390` + `V4: 2,750,070`)
   - `T3 (Lvl 60)`: `233,460` Spiritual Essence (`T1: 31,020` + `T2: 69,820` + `T3: 132,620`) + `2,072,050` extra Stellar Shards (`7,007,120` total Stellar from E5)
   - `T5 (Lvl 120)`: `1,248,120` Spiritual Essence (`+ T4: 219,420` + `T5: 330,220` + `Lvl 120: 465,020`) + `9,994,100` extra Stellar Shards (`14,929,100` total Stellar from E5)
4. **All 9 Tree of Origin Glory Challenges & Rewards:**
   - **Tier 1 (`3× T3 / Lvl 60` — `200,000` Spiritual Essence & `100,000` Stellar Shards each):**
     1. `Shadow or Abyss` hero to `T3`
     2. `Fortress or Forest` hero to `T3`
     3. `Light or Dark` hero to `T3`
   - **Tier 2 (`6× T5 / Lvl 120` — `350,000` Spiritual Essence & `150,000` Stellar Shards each):**
     1. `Shadow` hero to `Lvl 120`
     2. `Abyss` hero to `Lvl 120`
     3. `Fortress` hero to `Lvl 120`
     4. `Forest` hero to `Lvl 120`
     5. `Light` hero to `Lvl 120`
     6. `Dark` hero to `Lvl 120`
   - **Total Payout:** **`+2,700,000` Spiritual Essence** & **`+1,200,000` Stellar Shards**.
   - **Self-Funding Threshold:** Because the three `T3` challenges award `3 × 200,000 = 600,000` Spiritual Essence, an account only needs **`~650,000` organically farmed Spiritual Essence** (`~850,000` after claiming Eloise's Stage 1 `Shadow/Abyss T3`) + **`~15M` Stellar Shards** + **`35–40` Soul Symbols** to chain `T3` into `T5 (Lvl 120)` across all 6 factions in a single pass.

### Proposed Single-Pass Loop at the Stage 3 Pivot (`Only 1 New Hero: Holmes Young`)
Because `5` of the `6` base factions already have heroes in `README.md`, executing one regression loop during the **Stage 3 Pivot** (when `Eloise` and `GSSW` are already being regressed) clears **all 9 Tree Achievements** and **all 6 Seal Land 20s** while adding only **1 temporary Fortress hero (`Holmes Young`)**:

| Step | Faction | Hero | Already in Guide? | Action (`T5 Lvl 120` + `Splendid Melodic Strings`) | Post-Clear Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| *(Stage 1)* | **Shadow** | **Eloise** (`#1`) | **Yes** | Clears **Shadow SL20** + **Shadow/Abyss `T3`** naturally in Stage 1. | Keep until Stage 3 |
| **1** | **Shadow** | **Eloise** (`#1`) | **Yes** | Regress `GSSW` (`5 SS`) → push Eloise `T3 → T5 (Lvl 120)` → claim **Shadow `Lvl 120`**. | **Regress** (`5 SS`) |
| **2** | **Light** | **Sun Wukong** (`#8`) | **Yes** | Rebuild base `Sun Wukong` (`9` copies from `GSSW`) to `T5 (Lvl 120)` → **Light/Dark `T3` + Light `Lvl 120`** + **Light SL20**. | **Regress** (`5 SS`) |
| **3** | **Abyss** | **Waldeck** (`#3`) | **Yes** | Upgrade retiring `9* Waldeck` (`+6` copies) to `E5 → T5 (Lvl 120)` → **Abyss `Lvl 120`** + **Abyss SL20** (with `9* Ignis`). | **Regress** into food (`5 SS`) |
| **4** | **Fortress** | **Holmes Young** | **New (Temp)** | Build `E5 → T5 (Lvl 120)` → **Fortress/Forest `T3` + Fortress `Lvl 120`** + solo **Fortress SL20**. | **Regress** into food (`5 SS`) |
| **5** | **Forest** | **Melissa** (`#16`) *(or `Garuda`/`Rogan`)* | **Yes** *(if `Melissa`)* | Build `E5 → T5 (Lvl 120)` → **Forest `Lvl 120`** + **Forest SL20**. | **Regress** (`5 SS`; keep `Melissa` copies for Stage 7 `LBRM`) |
| **6** | **Dark** | **Aspen** (`#9`) | **Yes** | Build base `Aspen` to `T5 (Lvl 120)` → **Dark `Lvl 120`** + **Dark SL20** (with `E5 Carrie + Drake`). | **Regress** (`5 SS`), then transcend **`Aspen → LFA`** & **`Queen → SQH`** |

### Open Questions Awaiting User Confirmation
1. **Forest Hero Choice:** Use **`Melissa`** (0 extra Forest heroes added to the guide; pulls `Melissa`'s 9 copies in Stage 3 and keeps them in bag after regression for Stage 7 `LBRM`) vs. adding **`Garuda` or `Rogan`** as a 2nd temporary hero (since Newbie Growth Plan gives free `Garuda` copies without spending selection chests early).
2. **Placement in `README.md`:** Whether to embed this 6-step loop directly inside **Stage 3** (plus adding temporary `Holmes Young` and `assets/heroes/holmes-young.png` to Quick Reference) and note `Shadow SL20` in Stage 1 / `All 6/6 SL20s` in Stage 3.

---

## 5. Validation Script

Whenever editing `README.md` or adding assets, run this sanity check from the repository root to verify that all `<img>` paths exist, are valid PNGs, and all Markdown tables have consistent column counts:

```bash
python3 -c '
import os, re, glob

with open("README.md") as f:
    text = f.read()

srcs = re.findall(r"src=\"([^\"]+)\"", text)
unique_srcs = set(srcs)
for s in sorted(unique_srcs):
    assert os.path.isfile(s) and os.path.getsize(s) > 0, f"Missing: {s}"
    with open(s, "rb") as imgf:
        assert imgf.read(8) == b"\x89PNG\r\n\x1a\n", f"Invalid PNG: {s}"

all_assets = set(glob.glob("assets/**/*.png", recursive=True))
print(f"<img> tags: {len(srcs)} | Unique referenced: {len(unique_srcs)} | Unreferenced: {sorted(all_assets - unique_srcs)}")

lines = text.splitlines()
i = 0
while i < len(lines):
    if lines[i].startswith("|"):
        expected = lines[i].count("|")
        while i < len(lines) and lines[i].startswith("|"):
            assert lines[i].count("|") == expected, f"Line {i+1} column mismatch"
            i += 1
    else:
        i += 1
print("All tables and image assets valid.")
'
```
