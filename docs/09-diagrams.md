# Diagrams — Lecture Intelligence

These are simple diagrams to help a beginner see how the product works. They match the spec in `docs/03-spec.md`. No image files are used — the diagrams below are written in Mermaid text, which GitHub renders as a picture.

## 1. How it works

```mermaid
flowchart TD
    A["One lecture: notes, slides, or transcript"] --> B["Pull out definitions, concepts, and examples"]
    B --> C["Draft a structured summary"]
    C --> D["Check every line against a source line"]
    D --> E{"Is every claim supported?"}
    E -- No --> F["Remove it or flag it as uncertain"]
    F --> D
    E -- Yes --> G["Add 5 practice questions linked to the summary"]
```

What this shows: accuracy comes first. A summary line without a source line is not allowed, and anything uncertain is flagged, never guessed.

## 2. User journey

```mermaid
flowchart TD
    A["Student misses a lecture"] --> B["Student opens the summary for that lecture"]
    B --> C["Student reads definitions with source lines"]
    C --> D["Student tries the 5 practice questions"]
    D --> E["Student checks answers against the summary"]
    E --> F["Student catches up without learning a wrong definition"]
```

What this shows: before the product, the student revised from incomplete notes. After it, the student can trust the summary because every claim can be traced back to the lecture.

## 3. Eval and release flow

```mermaid
flowchart TD
    A["Audit 6 lectures line by line"] --> B["Score each claim: supported, unsupported, or missing"]
    B --> C{"Is at least 95 percent supported, with zero invented definitions?"}
    C -- No --> D["Fix the worst failure and change the instructions"]
    D --> B
    C -- Yes --> E["Lecturer reviews summaries for their own course"]
    E --> F["One class pilot, with a report an error button"]
    F --> G["Errors go straight into the eval set"]
```

What this shows: the product is judged by fidelity, not by how long the summary is. Errors reported by students become new test cases.
