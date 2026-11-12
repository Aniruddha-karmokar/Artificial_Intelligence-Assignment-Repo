Symbolic Reasoning Agent - AI Assignment 2026
Aniruddha Karmokar (P26CS0001)

Files
  reasoning_agent.ipynb   complete implementation, evaluation, traces, CSV export
  report.pdf              report (representation, algorithms, experiments, traces)
  submission.csv          id,predicted_label for the public evaluation rows
  data/                   optional public data used for development and evaluation
      ruletaker.jsonl, counterbench.jsonl, folio.jsonl   (linked Hugging Face datasets)
      ruletaker_standard.jsonl      1000 theories in the original RuleTaker style,
                                    labelled by ProbLog (closed world)
      make_ruletaker_standard.py    script that generated it (needs problog; not
                                    needed to run the notebook)

Requirements
  Python 3.10+ and Jupyter. The notebook only uses the Python standard library.

Running on the private test set
  1. In the first code cell set  TEST_FILE = 'path/to/test.jsonl'  (or .json / .csv).
     Each row needs id, context and statement. Labels are optional; the names
     premises/conclusion/query/question are also accepted.
  2. Run all cells. submission.csv (id,predicted_label) is written in this folder,
     with the inference time, and the accuracy if labels are present.
  The data/ folder is optional: without it the evaluation cells are skipped and
  only TEST_FILE is predicted.

Method
  Pattern-based parser -> logic formulas -> grounding ->
    forward chaining with stratified negation as failure (rule bases, closed world)
    or CNF + DPLL refutation (open world);
  cause-effect questions use a structural causal model (abduction, do(), propagation).
