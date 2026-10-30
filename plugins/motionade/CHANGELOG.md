# Plugin changelog

The `motionade` plugin for Claude Code and Codex. Versions follow Semantic Versioning;
the plugin is versioned separately from Motionade's Studio.

## 0.1.4 — 2026-10-29

Made for Studio 0.1.4: the skill names tools, operations and fields that Studio 0.1.2 does not
serve. 0.1.3 was never published, so this release also brings everything in its entry below.

Sign in again once. The plugin's server is now named `motionade`, as the plugin is, so Claude
Code lists `plugin:motionade:motionade` and Codex signs in with `codex mcp login motionade`.
After updating, run `/mcp`, choose `plugin:motionade:motionade` and Authenticate, or run
`codex mcp login motionade`. Tool approvals you gave the old `motion-studio` server ask again
the first time.

Edit by text. `getProject` with `format: "text"` reads a project, or one object's subtree, one
line an entity, and `applyOperations` takes changed lines back with their `base`: retime,
change a key, a word or a style, or move a layer by editing its line. A text write before
Accept revises the Stage it read. The authoring guide has a section on it.

Finishing, naming and roles. `acceptOperations` takes a short `name` for each change, which
Studio's Activity tab shows and the person can undo without losing their own history.
`finishTask` ends a task with a one-line summary, and notes the person leaves in Studio arrive
as `notesFromPerson`. The four agents of a split film (Director, Kit builder, Reviewer, Scene
author) pass their `hat`, or a Scene author its `sceneId`, so each has its own task and notes.

Fonts. `listCapabilities({"section":"fontFaces"})` lists the library and the person's My fonts,
one row per family. A font the library lacks stages as the nearest one, and the answer names it.
With the person's agreement, a brand font file from their repository goes into My fonts through
`createMediaUpload`.

Motion. `updateMotionBlockInfluence` sets how much of an Action shows, from 0 to 1. A layer's
Actions run outside its visible range, as in After Effects, so what follows or looks at it sees
the pose it has reached. Fewer writes are refused: every hold applies, and a running write wins
over a held one. The skill suggests putting parts that appear together in one Frame, which the
person can then move in one drag on Studio's timeline, and names the inspector's Appear and
Disappear.

Export. `motionade export` no longer refuses a project that carries notes, and warns, rather
than stops, when a font isn't loaded or a medium isn't ready.

## 0.1.3 — 2026-10-20

Made for Studio 0.1.3: the skill names a tool, operations and fields that Studio 0.1.2 does not
serve (`addFreehandPath`, `createProjectBrush` and the other project-brush operations, a fully
specified dry brush, and uploaded tips and grains). Projects saved by Studio 0.1.3 can't be
opened by an older Studio.

The capability map's brush entries say what an agent can now paint with: a library dry brush
with overrides of any parameter; a freehand stroke from the points a hand would make, with
`addFreehandPath`, steadied, fitted and given its pressure as Studio's Pencil does; a project
brush that many strokes share by `brushId`, so one edit repaints a whole painting; and a dry
treatment written in full, with a built-in, uploaded or generated tip, flow, pressure and colour
that change along the stroke, ink that runs dry or pools at the edges, and grain that moves with
the tip. A Draw can play along the route of a connector, mark or caret.

`medium.md` says that After, `hold` or `release`, now applies to Draw, Erase, Follow Path and
Morph: `release` brings back the whole stroke, the follower's own place or the outline the Morph
started from. `authoring.md` says that an anchored Path takes no `trailIds`, and that a stage
checks each operation against what it adds or changes, with the new timings: 3,642 operations
painting 1,000 Paths fold in about 9 s.

## 0.1.2 — 2026-10-16

Made for Studio 0.1.0. Adds the `remake` command: you give it a reference video and what your
film is for, and the agent makes your own film in the reference's structure. It keeps the
reference's cuts, timing, beats, rhythm and soundtrack, and tells the story with your brand and
your product: it maps each element of the reference to the one that plays its role in your film,
and leaves none of the reference's brand, copy, logos or pictures on screen. It learns your
product from the repository it runs in, or from your site and a search beyond it, claims nothing
your product does not do, and asks when the subject or the brand is unclear. It asks where the
pictures should come from, then shows you a brand kit and a storyboard with its story and waits
for your word before it builds. It reports scene by scene where the film follows the reference and
where it departs, and delivers an MP4 with the Studio link. In Claude Code run
`/motionade:remake <video path> [your product, site or notes]`; in Codex type `$`, choose
`motionade:remake` and add the path. The agent never starts it on its own.

The skill gains the route the command follows, `references/remake.md`: read the reference as a
skeleton, learn the brand and product, map roles rather than pixels, show the brand kit and the
storyboard, then build and review as a reconstruction does, judged against the storyboard and
the reference's structure rather than its pixels. `SKILL.md` and `reconstruction.md` point to it.

## 0.1.1 — 2026-10-14

Made for Studio 0.1.0. Adds the plugin's first command, `reconstruct`: you give it a rendered
video and any notes, and the agent rebuilds the video as an editable Motionade project, as close
to it as it can, from text, shapes and paths in named groups with keyframed motion, not from
frames of the video. It follows the skill's reference reconstruction route, reports honestly,
scene by scene, how close it got and which groups and controls to adjust in Studio, and delivers
an MP4 beside the reference with the Studio link. How the work is split and run is left to your
host. In Claude Code run `/motionade:reconstruct <video path> [notes]`; in Codex type `$`,
choose `motionade:reconstruct` and add the path. The agent never starts it on its own.

## 0.1.0 — 2026-10-12

The alpha release, the first that testers install from the public repository. The founder
chose 0.1.0 to mark the milestone. Made for Studio 0.1.0; it names nothing that Studio 0.0.5
does not serve.

Two changes to the skill's words, from the M3 add-on round. The Scene author's and the Kit
builder's parts in `roles.md` (and in their agent definitions) say to look a mechanism up in
`listCapabilities({"section":"needs"})` before building it, such as a wipe, a motion blur, a
field of dots or shapes that fuse, and to use the native construction it names: in that round
no hat opened `needs`, and a motion blur was faked although `style.motionBlur` exists.
`reconstruction.md` says that a Text takes only a family the server lists in `fonts` and that
nothing adds another yet: when a reference's typeface is not listed, the agent chooses the
nearest listed family, fits it to the reference widths, and tells the person which family stands
in before it builds. SKILL.md says the same of a brand typeface when it creates a film.

## 0.0.5 — 2026-10-11

Made for Studio 0.0.5: the skill names a tool, answers and an export field that Studio 0.0.4
does not serve (`setSceneNote`, the Stage answer's `scope`, `sceneNotes` in `getProject` and in
the Accept receipt, `scene_merge_invalid`, and the export page's `review`). On Studio 0.0.4 a
project still holds one Stage at a time, so authors of different Scenes take turns.

A film can be split among several agents. A new reference, `roles.md`, gives the rules every
hat holds and one part per hat. The Director plans the film, writes the project-level state
(the Scene list, durations, transitions, fonts, the format) before any author starts, and gives
each Scene one author. The Kit builder writes the shared parts as code that returns operations,
checks them on throwaway candidates, and writes nothing to the project. Each Scene author sets
its Scene's `owner` with `setSceneNote`, stages and accepts only inside that Scene, hands any
whole-project change to the Director, and marks the Scene `done`. An author names itself the
same way on every Scene it owns, such as "Author · A", so Studio counts one agent per name. A fresh Reviewer repairs
nothing and sets only the status: `reviewed`, or `draft` to send a Scene back, with findings and
their evidence for the Director. The plugin carries the four hats as Claude Code agents in its
`agents` folder (director, kit-builder, scene-author, reviewer). Codex 0.160.0 cannot load a
plugin's agents, so there the Director passes the shared rules and that hat's part as each
agent's brief. A new line in SKILL.md says to read Roles when a film is split among several
agents, and to use the plugin's agents where the host lists them.

The skill teaches the Scene-scoped Stage and the Scene note. `authoring.md` says that each
Stage answer's `scope` says what it settles against and that a newer Stage replaces only one
of the same scope: a Stage that changes one Scene lands on the latest project while that Scene
is unchanged, and any other Stage needs the whole project unchanged. `stale_revision` names the
Scene when it is one, `scene_merge_invalid` names a rule the merge breaks across Scenes, and the
Accept receipt carries `sceneNotes`. A new paragraph there introduces `setSceneNote`, and the
`needs` index in `capability-map.md` gains "Share one film among several agents". In
`reconstruction.md`, parallel authors may each own one Scene of a shared project, once the
director has registered the fonts and other project-level state they use. SKILL.md's loop
names `renderMotionStrip` among the tools that try `operations` without a Stage.

The built package's `.mcp.json` also names the host in the `X-Motionade-Agent-Host` header,
`Claude Code` under `headers` and `Codex` under `http_headers`, so Studio can name an agent that
reaches the hosted server. The name is for display only.

The export receipt reports review. `review.notesKept` says whether the server keeps Scene
notes. When it does, `review.unreviewed` lists each exported Scene that is not marked
reviewed: one with no note, another status, or changes since its review. It gives the Scene's
`status` and `changedSinceReview`, and a warning names those Scenes. It never fails the
receipt. Studio 0.0.5 keeps notes in File Mode and hosted; Studio 0.0.4 sends no `review`, and
the receipt then has none.

The export receipt no longer fails a correct film because the page tried to load a script it
does not use (#701). On a staging or preview deploy, Vercel injects its toolbar script; the
runner blocks it, as it blocks anything but the film's own requests, and `everythingLoaded`
then failed and named the block twice. It now fails when an image, medium, font, stylesheet
or fetch the film needs, or anything from the export link's own server, was blocked or failed
to load. A blocked or failed script, document or frame from another server is named in
`warnings`, and a block is counted once.

## 0.0.4 — 2026-10-09

Made for Studio 0.0.4: the skill names tools and options that Studio 0.0.3 does not serve
(`createOperationsUpload` and `operationsRef`, `deliver: "link"`, `keyShaderProperty`,
`createExportLink`).

The plugin carries a command, `motionade` (its `bin` folder; Node 18 or later, no
dependencies), for the mechanics the agent's shell does. `motionade send <ops.json>` checks
that a batch file is an array of operations and prints the `path`, `size` and `sha256` that
`createOperationsUpload` takes; with `--to <upload url>` it uploads the file. `motionade fetch
<link>` saves a render link, or a project download link unpacked. `motionade compare <frame>
<reference>` measures a frame against a reference image with ffmpeg (SSIM, PSNR, the share of
changed pixels) and saves the pair side by side and a difference image; it gives no verdict.
The command holds no sign-in and prints no signed link, and every step also works without it:
`shasum`, the ticket's `curl` line, the render's `save` line. Its exit codes say what to do
next: 4, the link no longer works, ask for a new one; 5, the link cannot be reached, allow the
command network access.

A new section of `authoring.md`, Large batches by file, teaches the path: write the operations
to a file, ask `createOperationsUpload` for a ticket, upload it, and stage by `operationsRef`;
and fetch renders by link when a script handles many frames. SKILL.md's review and
`reconstruction.md`'s comparison loop name `motionade compare`. The skill's Shaders you write
and `medium.md` say that an agent keys a Shader's or an Effect's Property with
`keyShaderProperty`. The `needs` index in `capability-map.md` names all of these; its pointers
into the overview name the call ("`listCapabilities` with no arguments: keys …"), and it says
that a Merge gives the exact joined outline a Morph can animate into. The README says the agent
can export the film itself and what that needs.

The agent exports films on the user's machine. `motionade export <link> --out <file>.mp4`
opens a link from the new `createExportLink` tool in the user's own Chrome or Edge, headless
and sandboxed, where the page renders the film through Studio's own export, then saves the
MP4 and prints a receipt as JSON. The receipt checks that the file is the one the page made,
that every image, medium and font loaded, that the project did not change meanwhile, and,
with ffmpeg, the picture, a full decode, and that the sound covers the picture, starts in
step with the mix and keeps its loudness; `--play` also plays the file to its end. It runs
on playwright-core 1.60 or later, installed once with one `npm` line (it downloads no
browser). The command wraps the runner module in the plugin's `scripts` folder,
`export-film.mjs`; `motionade-export.mjs` there runs the same module on its own, with its
own exit codes. The skill's Export and deliver section teaches
the path; the agent exports when the person asks for a file or for delivery, and the film at
speed stays the person's to watch in Studio (#670).

A coding agent's shell sandbox can stop Chrome from starting, and the driver's install needs
network. The skill, the no-browser exit (14) and `createExportLink`'s answer say so, and tell
the agent to ask the person to approve running that one command outside the sandbox; when no
Chrome or Edge is installed, the exit says to install one instead. The agent checks
`command -v motionade` first, then exports with `motionade export` when it prints a path or
with `node <plugin folder>/bin/motionade export` when it prints nothing, as a command of its
own, so the person approves once, the exact command it runs (#670).

Because that approval can cover every later `motionade export`, `--browser` names a browser,
never a program: it takes `chrome`, `edge` or `chromium` (Playwright's own build), or the
absolute path of Chrome or Edge where it installs, matched by its real path, and the runner
launches it by Playwright's channel. Anything else, a script, a link to one or a relative path,
is refused as usage (exit 1) before the driver loads. The driver loads without Playwright's
environment overrides, so `PLAYWRIGHT_BROWSERS_PATH` cannot move where `chromium` comes from (#655).

## 0.0.3 — 2026-10-09

Made for Studio 0.0.3: the skill names sections and answers that older servers do not serve.
The `build` entry at the top of the `listCapabilities` overview says whether the installed
plugin is compatible with the server; the released `.mcp.json` sends the plugin's version in the
`X-Motionade-Plugin-Version` header, under both keys Claude Code and Codex read, so the server
can tell.

The skill opens with where to look, in order: call `listCapabilities` first, then its `model`
section for how the medium works, then `needs` from what the picture needs, then `kinds` for
an operation's exact input; when the server refuses an operation, its `read` names the next
call. Three routes, create a film, reconstruct a reference and revise an existing film, share
one loop: stage, check with frames, strips and numbers, accept, read back, and give the person
the Studio link. Review uses the server's own checks (`renderFrame`, `renderMotionStrip`,
`previewRange`, `getPacingReport`); the agent no longer tries to watch playback at speed or
check the export itself, and reports those as left to the person in Studio.

A new reference, How Motionade works (`references/medium.md`), is the page the server serves
as `model`. The capability map, now titled Find a capability from the need, carries the `needs`
index in place of its hand-written purpose entries. The page and the index are generated from
the server's own source, so they name only what it serves. `authoring.md` says what the stage
fills and reports in `filled`, what a refusal carries (`kind`, `issues`, `fix`, `read`), that
each kind's contract has conditions and units, how a font change on an existing Text is bound,
and, in a new section, Shaders you write: the agent writes the SkSL and decides which values a
person can retune and keyframe in Studio. Stale lines are gone: the "Experimental package v0.3"
stamps, the minimum-engine commit, and internal type names in the skill's Shared core.

Bounded answers (added 2026-10-09: it reached 0.0.3 through the M1 PR after the version PR).
`authoring.md` describes the grouped warnings of a Stage answer, and the `omitted` counts and
`download` of an answer past the 48 KiB tool result limit, whose `save` line is run at once.

## 0.0.2 — 2026-10-04

Installing the plugin now connects the agent to Motionade: the released package carries the MCP
configuration for the hosted server, so there is nothing to connect separately. The README is now the
install guide. The skill loses one sentence in Temporal design that pointed at records
testers cannot open; its guidance is unchanged. The plugin uses the proprietary Motionade Plugin
License 1.0 from Pixed Studio LLC, allowing Motionade workflows and commercial outputs while
restricting independent repackaging and reuse of the plugin materials for other creation products.

## 0.0.1 — 2026-10-02

First numbered version. Same content as pilot 0.3.4: the `motion-design` skill with
seven references. The plugin ships no MCP configuration; the Motionade MCP server is
connected separately.
