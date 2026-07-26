# Study Workspace

This directory contains personal exercises, notes, and experiments. It is intentionally separated from the upstream textbook source.

## Structure

```text
study/
├── exercises/   # Exercise implementations and written answers
├── notes/       # Concept notes written in my own words
├── experiments/ # Small programs for testing claims and measuring behavior
└── README.md
```

## Suggested workflow

1. Read a small textbook section.
2. Before running code, predict its behavior and complexity.
3. Write the exercise or experiment under `study/`.
4. Test empty, minimal, typical, and adversarial inputs.
5. Explain why the result is correct in a nearby Markdown file or docstring.
6. Update `/LEARNING.md` with uncertainties and questions.
7. Commit the completed learning unit.

## File naming

Use chapter-oriented directories and descriptive file names, for example:

```text
study/exercises/algorithm-analysis/anagram_detection.py
study/notes/algorithm-analysis/big-o.md
study/experiments/basic-data-structures/list_front_insertion.py
```

Exercise files should start with a short header such as:

```python
"""Textbook section: 3.4

Goal:
My prediction:
Invariant or correctness argument:
Time complexity:
Space complexity:
Remaining questions:
"""
```

## Local setup on Windows

The textbook build is pinned to PreTeXt 2.3.8, which depends on `lxml<5`. Use Python 3.12 for the build environment because `lxml 4.9.4` provides a Windows wheel for CPython 3.12 but not CPython 3.13. Python 3.13 can still be used separately for personal exercise files if desired.

From PowerShell:

```powershell
git clone --branch study/answers https://github.com/amatouhake/pythonds.git
Set-Location pythonds
py -3.12 -m venv .\study\.venv
.\study\.venv\Scripts\python.exe -m pip install --upgrade pip
.\study\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Build and view the textbook:

```powershell
.\study\.venv\Scripts\pretext.exe build web
.\study\.venv\Scripts\pretext.exe view web
```

Run a personal exercise directly with the virtual environment interpreter:

```powershell
.\study\.venv\Scripts\python.exe .\study\exercises\path\to\exercise.py
```
