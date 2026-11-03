# CMU Graphics Coach

A Codio Custom Assistant (Virtual Coach) for middle school students learning Python with [CMU Graphics](https://academy.cs.cmu.edu/).

## What it does

- Reads the student's open files, the other `.py` files in the project, and the current guide page before every answer.
- Includes a full CMU Graphics reference in its instructions: shapes, properties, event handlers, groups and collision detection.
- Connects new ideas to micro:bit concepts students may already know.
- Gives direct help with errors and typos and Socratic guidance on design questions. Code examples are short and generic (1-3 lines). It never writes the student's program.
- Tells students how to run their work in Codio: **▶ Run**, then **🖥 Open Graphics** to see the canvas.

One `index.js` plus `metadata.json`, with no build step and no dependencies.

## Using it in Codio

1. In Codio, go to **Organization > Extensions**, click **Add extension**, and paste this repository's URL. You need to be an organization owner.
2. Choose the coach in the [Virtual Coach settings](https://docs.codio.com/instructors/setupcourses/assignment-settings/virtual-coach.html) for a course or assignment.
3. After a new release, click **Check for Updates** on the Extensions page. Students can type `version` in the coach to see which version is running.

Every change to `index.js` or `metadata.json` needs a new GitHub release, with a tag that matches the `VERSION` constant in `index.js`.

## Session log

Each coach session adds a short summary to a hidden `.coach-log.json` file in the student's workspace: when it started and ended, the coach version, how many questions were asked, the questions themselves (up to 50, each cut to 300 characters), and a short fingerprint of the files the coach saw each turn (to tell whether the files changed between questions). Codio's own coach-log export leaves the student's question blank for message-based coaches like this one, so this file is the only record of what students asked. It's never sent to the model, and logging can't break the coach.

## Development

```bash
node --check index.js
```

## Strict mode

If a workspace's own `.coach-log.json` shows a student leaning on the coach (many questions, or a run of "next step" asks), the coach adds a short "try first" nudge to its instructions. It still helps with every question and never mentions the mode. Sessions record `strict`, `strictReason` and `strictReleased`; the thresholds are named constants near the top of the strict-mode block in `index.js`.
