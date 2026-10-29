# Charm++ and reconverse coverage reports

Published site: <https://charmplusplus.org/charm-coverage/>

Weekly line, function and region coverage of
[Charm++](https://github.com/charmplusplus/charm) (branch `recharm`) and
reconverse, from clang source-based coverage measured over Charm++'s own
tests and examples. The `coverage` workflow of charmplusplus/charm writes
each run here with `coverage/publish.py`; how the numbers are made, and
their traps, is in that repository's
[coverage/README.md](https://github.com/charmplusplus/charm/blob/recharm/coverage/README.md).

Layout:

- `index.html`: front page, headline numbers of every run.
- `latest/`: redirect to the newest run's report.
- `runs/<date>-<charm sha>/`: `REPORT.md` and `REPORT.html`, `meta.txt`,
  the result tables (`results-*.tsv`, `vacuous-*.tsv`, `unreached-*.txt`,
  `programs-*.txt`), per cumulative tier the llvm-cov summary JSON, the
  `llvm-cov report` text and the gzipped lcov export, and `html/`, the
  llvm-cov per-file view (kept for the newest eight runs only).
- `runs/index.json`: what the front page is built from.

Everything in this repository is written by the workflow; edits by hand are
overwritten at the next run except this file.
