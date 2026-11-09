# Open issues for the manual

Unsettled points found while writing the first version of the manual (2026-11-08), from the
mod's `tutorial-notes.md` and its source. Each is written to become one GitHub issue once the
repository exists; delete it here when it has one.

Source of the notes: `C:\SML\SatisfactoryModLoader\Mods\GameFeatures\PipeFlow\Docs\tutorial-notes.md`.

## Decisions needed

1. **How a player turns FicstFluids on.** In the current build networks are handed to the mod
   with `PipeFlow.TakeOver add` / `add all` (a run is restored from the save at load). The
   manual is written as if the mod runs every network on its own, as the release must (no
   vanilla fallback). Once that is built, check the overview, "Coming from vanilla" and the
   Advanced page's TakeOver entries.
2. **Rename PipeFlow to FicstFluids in the mod.** Console commands (`PipeFlow.*`), log
   categories (`LogPipeFlow`), the `Saved\PipeFlow\` folder, and panel text. The Advanced page
   and the bug-report page quote these. Must be done before the first ficsit.app upload (the
   mod reference can't change after).
3. **Which console commands survive into the release, and how a player opens the console.**
   The Advanced page lists all 23; most are development tools.
4. **The plasma chain's pressures** (Particle Accelerator and Quantum Encoder at 48.3–68.9 MPa):
   "under review", the user expects to tweak them for gameplay. The manual says so.
5. **Compressor numbers.** Mk1/Mk2 displacement, efficiency and built-in volume ratio are
   placeholders in PipeFlowSim (`types.jl`, design doc §14.11). The manual quotes displacement
   300/600 m³/min and ratio limits about 3.5 (Mk1) and 7.9 (Mk2) on nitrogen, computed from
   `compressorRatioLimit` (κ = 1.4); recheck when they are settled.
6. **The report key.** The manual says L "by default". Confirm the default and that it can be
   rebound.

7a. **Revise the bug-reporting process.** The user may change how players report bugs; the
   `reporting-bugs.adoc` page and the issue form (`.github/ISSUE_TEMPLATE/`) follow whatever is
   decided (user, 2026-11-08).
7b. **Rename "Relieving" to "Unloading"** in the compressor panel and the report (UI session,
   `PipeFlowCompressorPanelBody.cpp:118`, `PipeFlowReport.cpp:193`). Since PipeFlowSim v1.38 the
   band above the set pressure is an unloader. The manual says "unloading" and notes the old
   word; drop the note and fix `report.adoc` once renamed.

## To confirm in game or against the code

7. **A pump with its power cut holding at 37% speed.** Seen live 2026-11-06, not confirmed with
   `PipeFlow.Aim`. The manual describes it as correct (flow driving it as a turbine). If no head
   was driving the flow, it is a coasting bug and the manual entry goes.
8. **A tank feeding a downhill pipe holds about 1.6 m back** (PipeFlowSim v1.29). The notes say
   "check in game after the build"; not yet done.
9. **The downhill pipe that "reads empty".** The notes' entry (2026-10-27) predates the geometric
   fill display (2026-11-02). The manual now says a downhill pipe shows part full; confirm in
   game, then update or delete the notes' entry.
10. **Truck station: unloading into a line already running** is not yet tested.
11. **Compressor power on Dark Matter Residue** (about 12.7 MW for two Mk2 stages): PipeFlowSim
    v1.37 figure, not yet tested in game.
12. **The pipe-flush and whole-network gas flush descriptions** in the Pipes page: check against
    the liquid whole-network flush (stage 10), which the manual doesn't describe yet.

## Content still to provide

13. **The tower height that worked**, from the save's water-tower networks (notes: "To add").
14. **Gas line practical limits:** how many wells, or what flow, one line carries, and over what
    length (notes: "to fill in"; the user found them very high).
15. **How pumps compare with vanilla** beyond lift and flow cap (notes: "the user's to fill in").
16. **What the report shows during a start-up** (which warnings mean "still filling"), and a rule
    of thumb for how many machines to switch back on at a time.
17. **The water-return backup** seen without a valve limit: this layout problem, or start-up
    sequencing? (open question, user, 2026-10-25).
18. **Gas fill times** are being tuned. The manual gives times only as estimates ("about half an
    hour", "hours"); recheck after tuning.

## Images and plots

19. **Screenshots and schematics.** Every page marks its slots with an "Image to come" sidebar;
    search for that phrase. The example networks may come from the tutorial save.
20. **Pump curve plot** from PipeFlowSim's `curveHead`, so it is the solver's own curve.
21. **Live pump and compressor curves in the panels** (UI, `HANDOFF-UI.md` item 3a); the manual's
    static plot stands in meanwhile.

## Kept out of the manual

22. **A gas platform pushing a nearby Fluid Buffer past equal pressure** (notes, Rail freight,
    2026-11-01). The notes call it mostly an artifact of how the model handles short pipes.
    Departures from real physics are issues for PipeFlowSim, not player documentation, so it is
    left out. Raise it with PipeFlowSim if it isn't already there.

## Process

23. **The machine pressures table** in `machines.adoc` is hand-copied from
    `machine-pressures.toml` (the authority). Generate it from the TOML so the two can't drift.
24. **Keep the notes and the manual in step.** Mark each `tutorial-notes.md` entry once it is
    covered by a page, so new entries stand out.
