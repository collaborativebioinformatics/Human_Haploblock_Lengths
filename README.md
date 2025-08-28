# Human_Haploblock_Lengths  
*Structural Variants Hackathon at Baylor College of Medicine, August 27–29, 2025*  

---

## 👩‍🔬 Contributors  
  

---

## 🎯 Aim  
To construct a **consensus map of haploblock breakpoints** by integrating **trio-based haplotype-resolved assemblies** with **pangenome graph methods**, and to explore how **structural variants (SVs)** affect haploblock length distributions.  

**Desired MVP (Minimum Viable Product):**  
- Jupyter notebook → graph construction → parse recombination breakpoints  
- Haploblock length estimation → clustering → visualization of hotspots  

---

## 📖 Introduction  

The concept of **haploblocks** (blocks of DNA inherited without recombination) is central to human genetics.  
- Traditional **HapMap studies** estimated haploblocks at ~50–100 kb.  
- However, large **structural variants (SVs)** (>2 Mb) disrupt haploblock boundaries and can cause many true haploblocks to be invisible in population-level LD-based maps.  

**Why this matters:**  
- **Haploblock = minimal unit of inheritance**  
- Trio-based assemblies allow direct identification of **recombination breakpoints**.  
- **Pangenome graphs** (HPRC, T2T-CHM13) capture structural variation missed by linear references.  
- Together, these resources allow us to build **fine-scale haploblock maps** and compare them with **population recombination maps** (e.g., deCODE).  

---

## 🛠️ Methods  

### Concept  
- Use diverse genomes (T2T, HPRC) + ~30 trios  
- Detect recombination hotspots from trios  
- Estimate haploblock lengths from pangenome variation  
- Compare and validate across methods  

### Trio Data  
- **HG002 (child)** — Genome in a Bottle (GIAB)  
- **HG004 (mother):** [Haplotype assembly for mother](https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_018852615.3/)  
- **HG003 (father):** [Haplotype assembly for father](https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_018852605.3/)  

Assemblies:  
- Mother: [HG004 latest release](https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/release/AshkenazimTrio/HG004_NA24143_mother/latest/)  
- Father: [HG003 latest release](https://ftp-trace.ncbi.nlm.nih.gov/ReferenceSamples/giab/release/AshkenazimTrio/HG003_NA24149_father/latest/)  

### External Datasets  
- **Population recombination maps:** [deCODE recombination rates (UCSC hg38 track)](https://genome.ucsc.edu/cgi-bin/hgTrackUi?db=hg38&g=recombRate2)  
- **Diverse genome assemblies:**  
  - [Human Pangenome Reference Consortium (HPRC)](https://humanpangenome.org/data/)  
  - [HPRC intermediate assemblies GitHub](https://github.com/human-pangenomics/hprc_intermediate_assembly)  

---

### 🔄 Workflow  

<img width="450" alt="workflow_diagram" src="https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Flowchart.JPG" />

**Step-by-step:**  
1. **Assembled Genomes:** Obtain haplotype-resolved assemblies for trios and diverse genomes.  
2. **Graph Construction:** Build a **pangenome graph** using *minigraph-cactus* or equivalent tools.  
3. **Hotspot Detection:**  
   - In trios → find recombination breakpoints by comparing child vs parental haplotypes.  
   - In diverse genomes → estimate hotspots from graph variation density.  
4. **Comparison:** Integrate trio breakpoints with graph-based hotspots.  
5. **Consensus Outputs:**  
   - Recombination site list  
   - Haploblock lengths (per chromosome)  
   - Haploblock clusters (around hotspots)  

---

## 🧪 DNAnexus  

- **Data Management:** Store HG002/HG003/HG004 assemblies and reference genomes in project folders.  
- **Computation:** Run *minimap2* alignments inside **Swiss-Army-Knife** app.  
- **Parsing & Analysis:**  
  - Use Python/Jupyter notebooks to parse alignment results  
  - Identify breakpoints → haploblocks  
  - Cluster haploblocks  
- **Visualization:**  
  - Histograms of haploblock lengths  
  - Hotspot density maps  
  - Comparison with deCODE recombination maps  

---

## 📊 Results (Expected)  

- **Consensus haploblock map** for HG002 trio  
- **Haploblock length distribution** (most 50–200 kb, some >1 Mb due to SVs)  
- **Overlap with known hotspots** (deCODE, PRDM9 motifs)  
- **Preliminary clustering** of haploblocks around hotspots  

---

## 💡 Use Cases  

- Studying recombination in **structurally complex regions** (e.g., centromeres, segmental duplications)  
- Benchmarking new **pangenome graph algorithms**  
- Teaching and training on **trio-based recombination detection**  
- Enhancing **clinical variant interpretation** by incorporating haploblock structure  

---

## 🚀 Future Directions  

- Scale up from a single trio → **30 trios**  
- Extend to the **HPRC dataset** for population-level recombination landscapes  
- Integrate with **functional genomic annotations** (promoters, enhancers, regulatory motifs)  
- Apply **machine learning models** to predict recombination landscapes  
- Release as an **open-source Jupyter pipeline** for reproducibility and collaboration  

---

## 📚 References  

1. Agarwal I, et al. *Fine-scale recombination landscapes.* Nat Commun. 2024. [link](https://www.nature.com/articles/s41467-024-50079-5)  
2. Nurk S, et al. *The complete human genome assembly.* Nat. 2023. [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC10234299)  
3. Halldorsson BV, et al. *Population-scale recombination maps.* Nat Genet. 2019. [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC12350169)  
4. NIST Genome in a Bottle Consortium. [link](https://www.nist.gov/programs-projects/genome-bottle)  
5. Human Pangenome Reference Consortium. [link](https://pubmed.ncbi.nlm.nih.gov/40702183/)  

---
