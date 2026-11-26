 Giorgia Crosilla & Erica Andreose

# **A multi-layered approach for understanding medieval diagrams using MLLMs**

This repository holds the data, prompts and model outputs for experiments on how a multimodal large language model (Claude, `claude-sonnet-5-5`) reads medieval diagrams. It looks at two levels:

- **Element level**: what the model *sees*. It identifies the geometric and figurative elements, transcribes the text, and states how text and shapes relate to each other.
- **Diagram level**: what the model *understands*. It classifies the diagram by subject (cosmological, computistical, …) and interprets it.

Every diagram is tested in two versions: the **original** image, and a **masked** image where the text is hidden. Comparing the two shows how much the model's reading depends on the written labels and how much on the visual structure alone.

## Repository structure

```
├── dataset/
│   ├── original images/       # 12 diagrams as they appear in the manuscripts
│   ├── masked images/         # the same 12 diagrams with the text masked
│   └── catalogo_gruppo.csv    # metadata: manuscript, date, author, theme, IIIF manifest, licence, bibliography
├── prompts/                   # system and user prompts for each experiment (Markdown)
├── outputs/
│   ├── original images/       # model outputs (JSON), one folder per image
│   └── masked images/         # model outputs (JSON) for the masked images
├── complete_annotations.json  # manual reference annotations (relations per image)
└── script.ipynb               # notebook that runs the experiments through the Anthropic API
```

## Corpus

The corpus has 12 medieval diagrams: circular schemas of elements, qualities and humours, planetary and lunar diagrams, computus tables, the *Scutum Fidei*, the *Tetragonus* and others.

- **7 images** come from the dataset of [*From Wisdom to Data*](https://ifilosofia.up.pt/proj/fdtw/fdtw_project). The project publishes IIIF manifests for medieval diagrams that cover a range of subjects and date from the late 9th to the mid-16th century. The manifests also carry descriptive and typological annotations of each diagram, verified by experts.
- **5 images** (`manual_*` IDs) were added by hand by Erica Andreose. She selected them while exploring the manuscript witnesses of Isidore of Seville's *De natura rerum* listed on [Biblissima](https://portail.biblissima.fr/fr/ark:/43093/oedatab585de699cd5ae95eab7de9d462451b3bb081fe2): BSB Clm 14300, Laon MS 422 and Besançon MS 184.

> Rubio, José Higuera, Alberto Romele, Dario Rodighiero, and Celeste Pedro, eds. 2022. *From Wisdom to Data: Philosophical Atlas on Visual Representations of Knowledge*. University of Porto Press. https://www.up.pt/press/books/978-989-746-315-0

`dataset/catalogo_gruppo.csv` (`;`-separated) gives full metadata for each image, linked by its ID.

## Experiments

| Output suffix | Approach | Prompts |
|---|---|---|
| `_elementlevel` | Zero-shot, element level only: elements, transcription, relations | `systemprompt_elementlevel.md` |
| `_interpretation` | Zero-shot, single pass: classification and interpretation | `systemprompt_interpretation.md` |
| `_CoT` | Two steps in one conversation: Step 1 describes, Step 2 interprets on top of Step 1 | `systemprompt_general.md` → `userprompt_basic.md` → `userprompt_interpretation.md` |
| `…_without_external(_knowledge)` | The same experiment, with the model told not to use external knowledge (visible evidence only) | `systemprompt_without_external_knowledge_masking.md` |

Outputs are JSON arrays of relations shaped as `subject – predicate – object`. Each relation has a type (`geometric`, `text_shape`, …), a certainty level and the supporting visual evidence. `complete_annotations.json` follows the same structure, so the model outputs can be compared directly with the manual annotations.

## Running the notebook

```bash
pip install "anthropic>=2.8.0,<3" pillow pendulum python-dotenv openai
```

1. Create a `.env` file in the project root containing `ANTHROPIC_API_KEY=...`. It is already in `.gitignore`.
2. Open `script.ipynb` and set the image folder and prompt paths. They are currently relative to the working directory.
3. Run section 1 for the zero-shot experiments or section 2 for chain of thought. The notebook skips images that already have an output file.

Images over 4.5 MB are resized automatically before they are sent to the API.

## Authors

Giorgia Crosilla and Erica Andreose

## Licence

Code: [MIT](LICENSE). Images and metadata from *From Wisdom to Data*: [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/), as stated in the catalogue. For the other images, see the licence of each holding library.
