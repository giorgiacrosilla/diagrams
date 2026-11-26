### STEP 1 — DESCRIPTION
Perform Step 1 on the diagram in the image.
 
### GOAL
Your goal is to:
1. Identify all the geometrical and figurative elements in the diagram. Proceed in reading order: start at the top left, move to the right, then continue downward row by row.
2. Transcribe all the text in the diagram, following the TRANSCRIPTION rules.
3. Define the relationships between the text and the geometrical or figurative elements.
4. Define the relationships between the geometrical and figurative elements.
5. Do not rely on external knowledge. 
Each relationship you identify becomes one entry in the output. Every element and every text you identify must appear in at least one entry.
 
### OBJECTIVITY
This is a purely visual description. Do not add any interpretation, identification, or iconographic, symbolic or theological reading.
- Describe figures only by what is visible: posture, clothing, attributes, objects held, and position. For example, write "woman seated on a throne holding a child", never "Mary with Jesus". Write "figure with a halo", never "saint" or "Christ". Write "winged figure", never "angel".
- Never name or identify a figure, symbol or object using your knowledge of medieval iconography, even if the identification seems obvious.
- A name may appear only as transcribed text, exactly as written in the diagram. Relate that text to the nearby element using only the allowed predicates. Do not state that the text identifies the figure.
- If you cannot tell what an element depicts, describe its shape or visible features and lower the certainty. Do not guess.
- "evidence" must refer only to visible features.
### OUTPUT FORMAT
Return only a valid JSON array, with no explanation, no additional text, and no markdown code fences.
 
[
  {
    "id": 1,
    "relation_type": "text_shape",
    "subject": "",
    "predicate": "",
    "object": "",
    "certainty": "high",
    "evidence": "",
    "updated_at": ""
  },
  {
    "id": 2,
    "relation_type": "",
    "subject": "",
    "predicate": "",
    "object": "",
    "certainty": "medium",
    "evidence": "",
    "updated_at": ""
  }
]
 
### FIELD RULES
- "id": an integer, starting at 1 and increasing by 1 for each relation. Order the entries following the reading order defined in GOAL.
- "relation_type": apply the first rule that matches:
  1. "text_shape": one of the two elements is a free-standing text, or both elements are identified by their text labels.
  2. "figurative": at least one of the two elements is figurative (figure, animal, object, plant, etc.).
  3. "geometric": both elements are geometrical (circle, square, band, line, arc, etc.).
- "subject": a single element, named as described in ELEMENTS AND LABELS.
- "predicate": must be exactly one of the allowed predicates listed in the PREDICATES section. No other value is permitted.
- "object": the element the subject relates to, named in the same way as the subject.
- "certainty": your confidence in that specific relation: "high", "medium", or "low".
- "evidence": the visual evidence that supports the relation. Leave it as an empty string only if the relation is self-evident.
- "updated_at": always an empty string; it will be filled in by a Python library.