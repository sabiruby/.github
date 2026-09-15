# Contributing

Issues are welcome in every repository of this organization; a fix is not promised, and a pull
request is read with the same care as an issue. What follows is mostly for the people (and the
agents) who write these repositories.

## Where documents go

Every repository keeps its documents under `docs/`, in the same shape, so that a reader who knows
one repository can find their way in the next:

| directory | the question it answers | what goes there |
|---|---|---|
| `docs/README.md` | *where do I look?* | the index: every file under `docs/` with one line each, and its status where it has one |
| `docs/design/` | *how is it built?* | the current state of a part of the system, kept up to date as the code changes |
| `docs/verification/` | *how do we know it is right, and how fast is it?* | test suites, benchmarks and their results, what deviates from a reference and why |
| `docs/plans/` | *what do we do, in what order?* | dated instructions for a piece of work; a plan stays after the work is done, with its status marked in the index |
| `docs/worklog/` | *what happened, when?* | one file per piece of work, named `YYYY-MM-DD-<slug>.md`: what was read, tried, measured, kept and dropped, and why — written while the work happens and not rewritten afterwards |

The rules:

* A subdirectory is used when a repository has two or more documents of that kind; a small
  repository keeps its few documents flat under `docs/` and still has the `README.md` index.
  `worklog/` is always a directory.
* A plan and the design it produces share a name: `plans/<topic>-plan.md` and
  `design/<topic>.md`.
* File names are lowercase with hyphens. A document written in Japanese carries no marker in its
  name; the index says which language each document is in.
* A document in `design/` describes what is; a `worklog/` entry describes what was done. When
  the code changes, the design document changes with it, and the worklog entry does not.
* Numbers (test counts, benchmark results) live in `verification/` and in the worklog; a design
  document points at them rather than repeating them.
