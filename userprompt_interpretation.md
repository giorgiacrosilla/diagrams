### STEP 2 — INTERPRETATION
Perform Step 2 on the same diagram, building on the JSON array you produced in Step 1.
 
### GOAL
Your goal is to:
Interpret each element and relation named in Step 1: identify what it represents, using the transcribed labels, the visible features and your knowledge of medieval iconography, texts and diagrammatic traditions. Your goal is to take information from the Step 1 and provide a general classification and interpretation of the diagram. Work at a general level, do not follow the separation in "relations" present in Step 1. 

### RULES
- If you think a Step 1 entry is wrong (wrong reading, wrong predicate, missing element), do not correct it: explain the problem in "evidence" and lower the certainty.
- Base every interpretation on the visible evidence and the transcribed text first; use external knowledge only to complete them. State in "basis" what the interpretation mainly relies on.
- Do not invent sources. Mention an author, text or tradition only if you are confident of it; otherwise describe the interpretation without naming a source and lower the certainty.
- If an element or relation cannot be interpreted, write "uninterpreted" in the corresponding field and set "certainty" to "low".
- Do not rely on external knowledge. 
### OUTPUT FORMAT
Return only a valid JSON array, with no explanation, no additional text, and no markdown code fences.
 
[
  {
    "diagram_classification": "",
    "interpretation": "",
    "basis": "textual",
    "certainty": "high",
    "evidence": "",
    "updated_at": ""
  }
]
 
### FIELD RULES
- "classification": the category of the diagram (e.g. cosmological, theological...).
- "interpretation": interpretation of the meaning of the diagram.
- "basis": the main ground of the interpretation, exactly one of "visual" (visible features), "textual" (transcribed text in the diagram).
- "certainty": your confidence in the interpretation of that entry: "high", "medium", or "low".
- "evidence": the reasons supporting the interpretation.
- "updated_at": always an empty string; it will be filled in by a Python library.
