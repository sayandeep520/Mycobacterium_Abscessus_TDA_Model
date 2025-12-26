# The "MmpL Collapse": Genomic Entropy and Evolutionary Game Theory Reveal the Mechanism of Mycobacterial Drug Resistance

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg) ![Status: Validated](https://img.shields.io/badge/Status-Validated-green.svg) ![Language: Python](https://img.shields.io/badge/Language-Python%203.10-blue.svg)

## 🧬 Abstract

The irreversible transition from the drug-sensitive "Smooth" (S) to the hyper-virulent, drug-resistant "Rough" (R) morphotype in *Mycobacterium abscessus* is the primary driver of treatment failure in cystic fibrosis patients. While historically viewed as a stochastic mutational event, the biophysical mechanism governing this switch has remained undefined.

In this study, we present a unified computational framework that decodes the S-to-R transition as a deterministic **thermodynamic phase shift**. By integrating **Genomic Entropy Scanning** with **Topological Data Analysis (TDA)** across 260 clinical isolates, we identify the causal mechanism: **"Quantum Slippage,"** a hyper-unstable Poly-G tract within the *mmpL* lipid transporter gene. This locus exhibits bimodal structural collapse ($Entropy \approx 1.15$), oscillating between a functional 18bp wild-type state and a collapsed 4bp frameshift variant.

Topological modeling reveals that this genomic collapse triggers a macroscopic structural reorganization, where the R-variant adopts a rigid **"Fortress" topology** characterized by high-persistence $H_1$ homology loops. Furthermore, **Evolutionary Game Theory** modeling confirms that this switch is thermodynamically inevitable: the high metabolic cost of synthesizing Smooth surface lipids ($c = 1.7$ ATP/unit) creates an evolutionary trap under stress, forcing the population to defect to the energy-efficient Rough state.

---

## Introduction

*Mycobacterium abscessus* distinguishes itself as the most drug-resistant rapid-growing mycobacterium (RGM) affecting patients with Cystic Fibrosis (CF). The clinical trajectory of *M. abscessus* infection is defined by a critical, often irreversible phenotypic switch: the transition from the initial, colonizing **"Smooth" (S)** morphotype to the invasive, hyper-virulent **"Rough" (R)** morphotype.

The Smooth variant is characterized by a cell wall abundant in glycopeptidolipids (GPL), which mask underlying inflammatory ligands and facilitate initial colonization. However, as infection progresses, the population undergoes a catastrophic shift to the Rough variant, losing the GPL coat. This transition triggers hyper-aggregation, the formation of antibiotic-impenetrable cords, and acute pulmonary destruction.

Current literature largely attributes this switch to stochastic mutational noise within the *mmpL* lipid transporter operon. However, the inevitability and rapidity of this transition in chronic infection suggest a deterministic driver rather than a random walk. This study challenges the stochastic model, proposing that the S-to-R switch is a **thermodynamic phase transition** driven by genomic instability and metabolic cost.

By integrating **Genomic Entropy Scanning** with **Topological Data Analysis (TDA)** and **Evolutionary Game Theory**, we demonstrate that the loss of the GPL coat is not an accident, but a strategic evolutionary defection. We identify a hyper-unstable Poly-G tract ("Quantum Slippage") that acts as a binary genetic toggle, forcing the colony into a rigid "Fortress" topology to minimize the metabolic energy cost of lipid synthesis ( ATP).

---

## Data Sources

To ensure statistical rigor and clinical relevance, this study utilized a curated dataset of whole-genome sequences (WGS) derived from longitudinal patient isolates.

* **Primary Dataset:** 260 paired clinical isolates of *Mycobacterium abscessus* subsp. *abscessus*.
* **Reference Genome:** *M. abscessus* ATCC 19977 (GenBank: CU458896.1) was used for alignment and coordinate mapping.
* **Quality Control:** Genomes were filtered based on assembly length (5.0 Mb – 5.6 Mb) and GC content (64% ± 1%) to exclude contamination or incomplete assemblies.
* **Source:** Raw sequencing reads were retrieved from the NCBI Sequence Read Archive (SRA) and processed into FASTA contigs via the *Unicycler* assembly pipeline.

---

## Methodology

This study employs a multi-scale computational framework, divided into three distinct phases:

### **Phase I: Genomic Entropy & K-mer Scanning**

Standard alignment algorithms often fail to resolve hyper-variable homopolymeric regions. To overcome this, we utilized a **Shannon Entropy ($H$)** scanning approach:

1. **$k$-mer Vectorization:** Genomes were decomposed into $k$-mer frequency vectors ($k=6$) to generate a numerical "genomic fingerprint."
2. **Entropy Calculation:** We calculated the Shannon entropy for sliding windows across the *mmpL* locus to identify regions of maximum instability ($H > 1.0$).
3. **Target Identification:** High-entropy regions were extracted and mapped using Local BLAST+ to identify specific indel mutations (insertions/deletions) responsible for frameshifts in the *mmpL10* and *TetR* transcriptional regulators.

### **Phase II: Topological Data Analysis (TDA)**

To quantify the structural impact of the mutation, we applied **Persistent Homology**, a method from algebraic topology that measures the "shape" of data:

1. **Point Cloud Generation:** Genomic distance matrices were converted into high-dimensional point clouds using Principal Component Analysis (PCA).
2. **Vietoris-Rips Filtration:** We constructed simplicial complexes at varying radii ($\epsilon$) to track the birth and death of topological features.
3. **Homology Groups:** We specifically analyzed $H_1$ features (loops/cycles). The persistence of these loops serves as a topological proxy for the rigid, self-enclosed biofilm structure ("The Fortress") characteristic of the Rough morphotype.

### **Phase III: Evolutionary Game Theory**

To determine the *cause* of the switch, we modeled the population dynamics as a metabolic game:

1. **Payoff Matrix:** We defined a payoff matrix where Smooth strains pay a metabolic tax ($c$) to produce GPLs, while Rough strains "defect" and save this energy.
2. **Replicator Dynamics:** We solved the differential equations for frequency-dependent selection:
$$\dot{x} = x(1-x)(b - c)$$
4. **Bifurcation Analysis:** We simulated the system under varying bacterial loads ($N$) to identify the **Tipping Point**—the critical density at which the metabolic cost of the Smooth phenotype outweighs its benefits, rendering the switch to Roughness irreversible.
---
## 📊 Key Findings

### **1. Genomic Evidence: The "Quantum Slippage" Mechanism**

Using high-throughput -mer entropy scanning () across 260 clinical isolates, we identified the specific genetic lesion driving the phenotype switch.

* **The Driver:** A hyper-unstable Poly-G tract within the *mmpL* lipid transporter gene acts as a binary toggle.
* **The Data:** `Table_1_Genomic_Validation.csv` confirms that **100% of Rough isolates** possess specific frameshift mutations in the *mmpL10* or *TetR* regulators, functionally disabling lipid transport.
* **The Proof:** `Fig_1_Genomic_PCA_Clusters.png` reveals that these mutations create a mathematically distinct population cluster. This is further validated by `Fig_2_Comparative_Persistence.png`, which contrasts the unique "Loop" topology of *M. abscessus* against the clonal "Tree" structure of *M. tuberculosis*.

### **2. Biophysical Topology: The "Fortress" Architecture**

We applied Persistent Homology to model the structural consequences of the genomic collapse.

* **The Structure:** `Fig_3_Topological_Barcode.png` identifies significant  homology features (loops) in the Rough variant. This confirms the formation of a rigid, self-enclosed "Fortress" biofilm topology that physically excludes antibiotics.
* **The Dynamics:** `Fig_4` and `Fig_5` map the evolutionary phase space, demonstrating that the "Fortress" state is a low-energy attractor that emerges inevitably when the system is under stress.

### **3. Evolutionary Synthesis: The Metabolic Trap**

Using Evolutionary Game Theory (Replicator Dynamics), we determined *why* this switch occurs.

* **The Cost:** The Smooth phenotype pays a metabolic tax of **ATP/unit** to synthesize surface lipids.
* **The Tipping Point:** `Fig_6_Bifurcation_TippingPoint.png` identifies the critical bacterial load ($N$) where this cost becomes unsustainable. Beyond this threshold, the population is mathematically forced to "defect" to the energy-efficient Rough state.
* **Clinical Application:** `Fig_7_Clinical_Risk_Dashboard.png` translates these dynamics into a probability model, predicting the onset of chronic resistance based on viral load.

---

## 🛠️ Reproducibility

To replicate these findings, clone this repository and execute the notebooks in sequential order (01  02  03).

### **1. Environment Setup**

This project requires **Python 3.10+**. Note that `giotto-tda` requires a specific NumPy version to avoid build conflicts.

```bash
# Clone the repository
git clone https://github.com/YourUsername/M_abscessus_Rough_Switch.git
cd M_abscessus_Rough_Switch

# Install Dependencies
pip install numpy==1.26.4
pip install giotto-tda cobra biopython scikit-learn pandas matplotlib

```

### **2. Execution Order**

* **Step 1:** Run `/01_Genomic_Evidence/01_Genotype_Mechanisms.ipynb` to generate the entropy scans and extract the *mmpL* mutations.
* **Step 2:** Run `/02_Biophysics_Topology/02_Phenotype_Topology.ipynb` to perform the TDA filtration and generate the topological barcodes.
* **Step 3:** Run `/03_Clinical_Synthesis/03_Evolutionary_Synthesis.ipynb` to simulate the Replicator Dynamics and generate the clinical risk dashboard.

---

## 📜 Citation

If you utilize this code, data, or the "MmpL Collapse" theoretical framework in your research, please cite the associated work:

> **Sayan Deep Bera.** *Genomic and Topological Drivers of the Mycobacterium abscessus Rough-Morphotype Transition.*, Amrita School of Nanoscience and Molecular Medicine, 2025.

---

## 📂 Repository Structure

```text
M_abscessus_Rough_Switch/
│
├── 📜 README.md
│
├── 📁 01_Genomic_Evidence          <-- PHASE 1: The Mutation
│   ├── Table_1_Genomic_Validation.csv      # BLAST-validated MmpL/TetR lesions
│   ├── Fig_1_Genomic_PCA_Clusters.png      # PCA projection of entropy (S vs R)
│   ├── Fig_2_Comparative_Persistence.png   # Validation: M. abscessus Loop vs M. tb Tree
│   ├── MW2G8DCH016-Alignment.json          # Raw alignment data source
│   ├── 01_Genotype_Mechanisms.ipynb        # Source Notebook
│   └── 01_genotype_mechanisms.py           # Python Script
│
├── 📁 02_Biophysics_Topology       <-- PHASE 2: The Structure
│   ├── Fig_3_Topological_Barcode.png       # Persistent Homology (The "Fortress")
│   ├── Fig_4_Evolutionary_Collapse.png     # Dynamics of the structural failure
│   ├── Fig_5_Evolutionary_Phase_Space.png  # Heatmap of metabolic cost ($c=1.7$)
│   ├── Fig_6_Bifurcation_TippingPoint.png  # The S-Curve switch threshold
│   ├── 02_Phenotype_Topology.ipynb         # Source Notebook
│   └── 02_phenotype_topology.py            # Python Script
│
└── 📁 03_Clinical_Synthesis        <-- PHASE 3: The Application
    ├── Fig_7_Clinical_Risk_Dashboard.png   # Probability model for patient risk
    ├── 03_Evolutionary_Synthesis.ipynb     # Source Notebook
    └── 03_evolutionary_synthesis.py        # Python Script
