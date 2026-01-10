# Generative AI, Expertise, and Effective Labor Supply  
**Public Data Release**

This repository contains the **task-level** and **occupation-level** datasets underlying the paper:

> **Generative AI, Expertise, and Effective Labor Supply**  
> Seyed M. Hosseini and Guy Lichtinger (2026)

The data are constructed from O*NET task descriptions combined with large language model (LLM) evaluations of automation exposure, task expertise, and GenAI-induced task transformation. The datasets are designed to support research on how generative AI reshapes occupational expertise, effective labor supply, and inequality.

---

## Overview of Datasets

We release **two complementary datasets**:

1. **Task-Level Dataset**  
2. **Occupation-Level Dataset**

Together, they allow researchers to move beyond standard “exposure” measures and study how GenAI affects:
- task expertise,
- occupational entry barriers,
- effective labor supply (Potential Supply Shift, PSS),
- and productivity-relevant task content.

---

## 1. Task-Level Dataset

**File:**  

Final_Task_Dataset.xlsx


**Unit of observation:** O*NET task  
**Coverage:** 19,265 tasks across 923 U.S. occupations

### Key Variables

#### Identifiers
- `onet_soc_code`: O*NET-SOC occupation code  
- `task_id`: O*NET task identifier  
- `task_description`: Text description of the task  
- `task_type`: Core vs. supplemental task

#### GenAI Automation Exposure
- `ai_exposed`: Binary indicator equal to 1 if the task is classified as automatable by GenAI  
- `automation_score`: Discrete automation category (based on updated Eloundou et al. (2024) rubric)

#### Task Expertise (Without GenAI)
- `expertise_score_noAI`: Ordinal expertise score (1–5)  
- `expertise_label_noAI`: Categorical label (no/minimal → very high)  
- `training_months_noAI`: Estimated months of task-specific training required

#### Task Expertise (With GenAI Assistance)
- `expertise_score_withAI`: Expertise score assuming access to a capable GenAI assistant  
- `training_months_withAI`: Training months required with GenAI assistance

#### Weights
- `task_weight`: Task weight used in aggregation (1 for core tasks, 0.5 for supplemental tasks)

### Construction Notes
- Automation exposure and expertise ratings are generated using frontier LLMs under clearly defined prompts (see paper Appendix).
- Expertise is defined as a **barrier to entry**, not task difficulty per se.
- Training-time estimates map ordinal expertise scores into a continuous scale (months).

---

## 2. Occupation-Level Dataset

**File:**  
Final_Occupation_Dataset.xlsx


**Unit of observation:** O*NET occupation  
**Coverage:** 923 occupations

### Key Variables

#### Baseline Characteristics
- `onet_soc_code`: O*NET-SOC occupation code  
- `occupation_title`: Occupation name  
- `mean_annual_wage_2024`: Mean annual wage (OEWS, 2024)  
- `total_employment_2024`: Employment level (OEWS, 2024)

#### Exposure Measures
- `share_tasks_exposed`: Share of tasks classified as automatable (standard exposure measure)

#### Expertise Measures
- `expertise_noAI`: Average expertise requirement (training months) without GenAI  
- `expertise_extensive`: Expertise after removing automated tasks (extensive margin)  
- `expertise_intensive`: Expertise with GenAI assistance (intensive margin)  
- `expertise_combined`: Combined post-GenAI expertise requirement

#### Potential Expertise Shift (PES)
- `PES_extensive`: Change in expertise from task removal  
- `PES_intensive`: Change in expertise from task simplification  
- `PES_combined`: Total expertise shift

#### Potential Supply Shift (PSS)
- `PSS`: Change in the share of the workforce qualified to perform the occupation  
- `ps_base`: Baseline potential supply  
- `ps_withAI`: Post-GenAI potential supply  

PSS is defined as:
\[
\text{PSS}_o = F(X_o^{\text{noAI}}) - F(X_o^{\text{combined}})
\]
where \( F(\cdot) \) is the employment-weighted distribution of baseline expertise.

#### Productivity
- `prod_gain`: Predicted occupation-level productivity gain from GenAI (log points)

---

## Relationship Between the Two Datasets

- The **task-level dataset** is the primitive input: it contains all LLM evaluations.
- The **occupation-level dataset** aggregates task-level information using O*NET task weights.
- All occupation-level measures (exposure, PES, PSS, productivity) are fully reproducible from the task-level data.

---

## Intended Use

These data are intended for:
- Research on AI, labor markets, and inequality
- Studying entry barriers and effective labor supply
- General equilibrium modeling of technological change
- Policy analysis beyond standard automation exposure metrics

---

## Important Caveats

- The data measure **potential** effects of GenAI, not realized outcomes.
- LLM-based assessments involve judgment and should be interpreted with caution.
- The analysis abstracts from endogenous retraining, new task creation, and new occupations.
- PSS depends on the assumed baseline distribution of expertise, constructed from observed occupational sorting.

---

## Citation

If you use these data, please cite:

> Hosseini, S. M., & Lichtinger, G. (2026).  
> *Generative AI, Expertise, and Effective Labor Supply.*

---

## Contact

- **Seyed M. Hosseini** — Harvard University  
  shosseinimaasoum@fas.harvard.edu  

- **Guy Lichtinger** — Harvard University  
  guylichtinger@g.harvard.edu  
