# EduAll — AI for Philanthropy course case

Data and notebooks for the **EduAll Foundation International Student Grant Call 2026** case.

- **Applicants:** 500 synthetic applicants (generated for teaching; no real people).
- **Budget:** CHF 500,000 to allocate.
- **Notebooks:** each one implements one of the course's decision-making approaches: data exploration, traditional
  machine learning, and an LLM workflow.

**To start:** click a notebook's **Open in Colab** badge below, then *Runtime → Run all*. Nothing to upload, and no
folders to set up.

## Notebooks

| Approach | Notebook | Colab |
|---|---|---|
| Data exploration | `free_generation/exploration_groupwork/EduAll_Exploration_Code.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/free_generation/exploration_groupwork/EduAll_Exploration_Code.ipynb) |
| Data exploration — report | `protocols/agentic_mimicking_protocols/DataExploration/DataExploration_Report.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/DataExploration/DataExploration_Report.ipynb) |
| Data exploration — agentic report | `protocols/agentic_mimicking_protocols/DataExploration/DataExploration_AgenticReport_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/DataExploration/DataExploration_AgenticReport_Protocol.ipynb) |
| Traditional AI — clustering | `free_generation/traditionalAI_groupwork/01_unsupervised_clustering.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/free_generation/traditionalAI_groupwork/01_unsupervised_clustering.ipynb) |
| Traditional AI — decision trees / random forest | `free_generation/traditionalAI_groupwork/02_decision_trees_random_forest.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/free_generation/traditionalAI_groupwork/02_decision_trees_random_forest.ipynb) |
| Traditional ML 1 — random-forest proximity | `protocols/agentic_mimicking_protocols/TraditionalML/1_RF_proximity/RF_Proximity_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/TraditionalML/1_RF_proximity/RF_Proximity_Protocol.ipynb) |
| Traditional ML 2 — text embeddings | `protocols/agentic_mimicking_protocols/TraditionalML/2_Text_embeddings/Text_Embeddings_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/TraditionalML/2_Text_embeddings/Text_Embeddings_Protocol.ipynb) |
| Traditional ML 3 — Gower distance | `protocols/agentic_mimicking_protocols/TraditionalML/3_Gower/Gower_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/TraditionalML/3_Gower/Gower_Protocol.ipynb) |
| Traditional ML 4 — hybrid | `protocols/agentic_mimicking_protocols/TraditionalML/4_Hybrid/Hybrid_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/TraditionalML/4_Hybrid/Hybrid_Protocol.ipynb) |
| Traditional ML 5 — survival | `protocols/agentic_mimicking_protocols/TraditionalML/5_Survival/Survival_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/TraditionalML/5_Survival/Survival_Protocol.ipynb) |
| LLM workflow (Gemini) | `protocols/agentic_mimicking_protocols/LLMWorkflow1/LLM_Workflow_Protocol.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AIforPhilanthropy/eduall/blob/main/protocols/agentic_mimicking_protocols/LLMWorkflow1/LLM_Workflow_Protocol.ipynb) |

Each notebook folder also has its executed **HTML report** and its result files (`decision_progression.csv`,
`final_allocation.csv`, …), so you can read the results without running anything.

**LLM workflow notebook:**

- **Without a key:** it replays the documented first run, at no cost.
- **To call Gemini yourself:** add your key as a Colab secret. Click the 🔑 icon in the left sidebar → *Add new
  secret* → name `GEMINI_API_KEY` → switch on *Notebook access*.

**Saving your work:** a notebook opened from GitHub is a read-only copy. Use *File → Save a copy in Drive* before you
change it.

## How the notebooks find the data on Colab

Every notebook starts with this cell. On Colab, it downloads this repository and moves into the notebook's folder,
so all data paths work exactly as on a course computer. On your own computer, inside a copy of the repository, it
does nothing.

```python
# --- Get the data -------------------------------------------------------------------------------
import os, pathlib, subprocess
REPO_URL = "https://github.com/AIforPhilanthropy/eduall.git"
NOTEBOOK_DIR = "protocols/agentic_mimicking_protocols/TraditionalML/1_RF_proximity"   # this notebook's folder
here = pathlib.Path.cwd()
if not any((p / "data" / "EduAll_500_Applications_Dataset.csv").exists() for p in [here, *here.parents]):
    if not pathlib.Path("/content/eduall").exists():
        subprocess.run(["git", "clone", "--depth", "1", REPO_URL, "/content/eduall"], check=True)
    os.chdir(pathlib.Path("/content/eduall") / NOTEBOOK_DIR)
print("working directory:", os.getcwd())
```

To add it to a notebook of your own, paste the cell at the top. Set `NOTEBOOK_DIR` to `""` if your code reads the
data as `data/...`, i.e. relative to the repository root.

## Using the data in your own notebook (straight from the URLs)

No download step is needed for the CSV or for a single file: read it directly from its GitHub URL.

**The applicant table (500 rows, one per applicant):**

```python
import pandas as pd
BASE = "https://raw.githubusercontent.com/AIforPhilanthropy/eduall/main/data"
df = pd.read_csv(f"{BASE}/EduAll_500_Applications_Dataset.csv", keep_default_na=False)
df.head()
```

**One applicant's full application text:**

```python
import requests
BASE = "https://raw.githubusercontent.com/AIforPhilanthropy/eduall/main/data"
text = requests.get(f"{BASE}/individual_applications/STU000001_application.md").text
print(text[:2000])
```

**All 500 application texts:** one small zip, unpacked into a dictionary `{student_id: text}`:

```python
import io, zipfile, requests
BASE = "https://raw.githubusercontent.com/AIforPhilanthropy/eduall/main/data"
z = zipfile.ZipFile(io.BytesIO(requests.get(f"{BASE}/individual_applications.zip").content))
applications = {name.split("/")[-1].split("_")[0]: z.read(name).decode("utf-8")
                for name in z.namelist() if name.endswith("_application.md") and "__MACOSX" not in name}
len(applications), list(applications)[:3]
```

**The foundation's documents:** grant call, FAQ, organisation profile, application guidelines, terms and conditions:

```python
import requests
BASE = "https://raw.githubusercontent.com/AIforPhilanthropy/eduall/main/data/eduall_data"
call = requests.get(f"{BASE}/EduAll_Grant_Call_2026.md").text
print(call[:1500])
```

## Repository layout

```
data/
  EduAll_500_Applications_Dataset.csv     structured data, 500 applicants x 44 columns
  individual_applications/                one application document per applicant (STU000001 ... STU000500)
  individual_applications.zip             the same 500 files in one zip
  eduall_data/                            grant call, FAQ, organisation profile and other foundation documents
free_generation/                          notebooks written freely, without a protocol
  exploration_groupwork/                  data exploration notebook
  traditionalAI_groupwork/                clustering and decision-tree notebooks
protocols/agentic_mimicking_protocols/    notebooks that follow the course protocols
  DataExploration/                        exploration reports
  TraditionalML/1_RF_proximity ... 5_Survival/   five traditional machine-learning protocols
  LLMWorkflow1/                           the LLM workflow (Gemini) and its AnythingLLM flow
```
