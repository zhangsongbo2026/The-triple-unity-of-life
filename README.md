# The Triple Unity of Life — Code and Data Package (v4.2, submission state)

> Zhang, S. (2026). *The triple unity of life: closure, code and the topology of
> living form.* Manuscript prepared for the Journal of Theoretical Biology.
> First public version; the full package will be archived with a Zenodo DOI at
> submission.

This repository accompanies the manuscript. It contains the complete,
deterministic pipeline — from raw public-data fetches to the final
submission-ready manuscript (PDF, DOCX with native OMML equations, and LaTeX) —
together with every intermediate result reported in the paper.

## What the paper claims

The framework unifies three observations of unequal strength — autonomous energy
metabolism is transmembrane and rotary; cellular life shares one genetic code
with a homologous decoder; the structures life depends on are typed by
topological invariants — closed into one regulatory loop (C1∧C2∧C3). The paper
develops it as an explicit Lakatosian research programme: a declared hard core,
a graded protective belt, a positive heuristic, and falsification conditions.

New results in this version:

1. **Thermodynamic margins as statistics.** Measured rotor/gradient pairs sit at
   a mean 12.5th percentile of a neutral null — robust across four registered
   null models (N0–N3, means 12.5/18.2/12.7/19.0), with a bootstrap CI excluding
   the null median. C-rings run close to the thermodynamic floor as a
   statistical fact; the mammalian c8 rotor is the tightest-constrained case,
   not a contradiction.
2. **The design table.** An exhaustive search of 9,936 three-node signed loop
   topologies (Michaelis–Menten dynamics, 200 parameter sets each):
   self-maintenance is generic (9,915 topologies qualify), robustness is graded
   by sign class (all-positive median Q = 63 vs 40 vs 18), and the canonical
   loop of this framework sits mid-class — the claim is about the class, not an
   individual.
3. **The founder requirement, quantified.** A basal-leak parameter ε unifies the
   exactly absorbing dead state with the design-table regime: the critical-leak
   line ε_c(ρ) falls smoothly from 5.7×10⁻² to 5.6×10⁻⁴ across the coupling
   range. Spontaneous genesis is rare (6.8% of parameter sets at ε = 0; 11.2%
   within the all-positive class) and leak-gated — genesis requires founder
   events.
4. **Spatial spread is structural.** With only the gradient diffusing, live
   patches are pinned at every coupling tested (including ρ = 4.0); vesicle-like
   dispersal unlocks invasion above a critical coupling (front velocity rising
   monotonically with ρ). Pinning is structural, not parametric.
5. **A second ignition.** The same loop accounts for eukaryogenesis: the
   prokaryotic genome ceiling, the non-transferability of membrane-buried genes
   (CoRR + tunnelling ruler), and the singularity and irreversibility of the
   event.
6. **Honest negatives, reported as results.** A blind re-analysis of 329 KEGG
   graphs finds the loops-versus-trees dichotomy holds as a class-level
   statistic but naive unsupervised clustering fails to recover it (ARI ≈ 0);
   the corrected enumeration engine overturns the earlier claim that knockdown
   self-repair requires negative feedback. Both are reported and located in the
   paper.

Eleven predictions with frozen, pre-registered protocols close the paper.

## Repository layout

```
code/       deterministic pipeline: fetch → analysis → figures → manuscript build
data/raw/   archived inputs: 408 KEGG KGML files, UniProt sequences, PDB manifest
data/processed/  analysis outputs (JSON/CSV) + CrossRef verification records
figures/    18 main-text figures (600 dpi PNG, Okabe–Ito palette)
manuscript/ Markdown source, LaTeX, PDF (51 pp), DOCX (native OMML,
            ISO-IEC 29500 strict XSD: 0 errors), bioRxiv extended abstract
LICENSE, requirements.txt
```

## Data sources

RCSB PDB (19 structures), UniProtKB (16 ATP-synthase subunits), KEGG (329
KGML graphs across hsa/eco/sce; full machine-readable inventory in
`data/processed/kgml_inventory.csv`), CrossRef (all 69 references verified).

## Reproducing

```bash
pip install -r requirements.txt
python code/01_fetch_data.py && python code/02_patch_fetch.py
python code/10_analysis_homology_tda.py
python code/11b_code_v2.py            # genetic-code error minimisation
python code/12b_models_fixed.py       # quasispecies + loop ODE + lambda2
python code/50_m1_margin.py           # thermodynamic margins + zero model
python code/51_design_engine.py       # design table (numba; see header for
                                      # env switches: NPARAM, EPS, RESTRICT)
python code/52_kegg_blind.py          # KEGG blind classification
python code/53c_founder_patch.py      # spatial founder experiments
python code/70_v4_fast.py             # eps boundary / budding / null models
python code/71b_eps_boundary_v2model.py  # critical-leak line + front speeds
python code/71_design_engine_v4.py    # criterion split + eps sweep
python code/20–22,55,74,76 _figures…  # figures
python code/40c_build_latex_v4.py     # LaTeX build (pandoc + xelatex)
```

The DOCX is built with pandoc (≥2.9) plus `code/docx_schema_fix.py`, and
validates against the ISO-IEC 29500 strict XSD with zero errors; all equations
are native OMML.

## Note on the manuscript's history

The version labels inside the manuscript's history note refer to a private
manuscript series; the present files are the first public version. Two
corrections made during that series are reported transparently in the paper:
an integration-protocol artefact behind an earlier self-repair claim, and the
downgrading of a KEGG classification claim. Neither is hidden; both are framed
as results.

## License

Code and data: MIT (see `LICENSE`). Manuscript text © the author.

## Citation

Zhang, S. (2026). The triple unity of life: closure, code and the topology of
living form. Manuscript in preparation for the Journal of Theoretical Biology.
DOI to be minted on acceptance.
