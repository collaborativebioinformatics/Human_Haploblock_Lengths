# Human_Haploblock_Lengths  
*Structural Variants Hackathon at Baylor College of Medicine, August 27–29, 2025*  

---

## 👩‍🔬 Contributors  
Team 5 – Human Haploblock Lengths Project (Hackathon group)  


Ben Busby (👑 Group Lead)
Jędrzej Kubica
Rahaf M. Ahmad
 Kirtan Dave 
Soham Sengupta
Suhasini Lulla
Talal AL Yazeedi
Aung Myat Phyo
Lingfeng Meng


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
- Trio-based assemblies allow direct identification of **recombination breakpoints**  
- **Pangenome graphs** (HPRC, T2T-CHM13) capture structural variation missed by linear references  
- Together, these resources allow us to build **fine-scale haploblock maps** and compare them with **population recombination maps** (e.g., deCODE)  

---

## 🛠️ Methods  

The analysis focused on chr6:70–80 Mb in the Ashkenazim Trio (HG002 child, HG003 father, HG004 mother).  
- **Data sources:** GIAB v4.2.1 VCFs + chr6 reference FASTA  
- **Tools:** bcftools, samtools, Python (pandas, numpy, matplotlib, seaborn, biopython)  
- **Steps:**  
  1. Filter and merge trio VCFs  
  2. Assign parental origin of child’s heterozygous alleles  
  3. Collapse consecutive origins into haploblocks  
  4. Identify recombination breakpoints  
  5. Generate consensus hap1, hap2, and IUPAC FASTAs  
  6. Visualize haploblocks, block size distribution, and variant density  

---

## 🔄 Workflow  

![Workflow Flowchart](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Flowchart.JPG)  

---

## 📊 Results  

**Summary statistics (chr6:70–80 Mb):**  
- Total variants: 8,453  
- Informative child heterozygotes: 8,453  
- Hap1 blocks: 1,625 | Hap2 blocks: 1,942  
- Hap1 recombinations: 1,983 | Hap2 recombinations: 2,300  
- Hap1: 42.2% paternal, 45.7% maternal  
- Hap2: 41.7% paternal, 46.2% maternal  
- Smallest block: 0 bp | Largest block: 199,542 bp  

---

### Figures  

**Figure Team 5-1.** Flowchart of the workflow  
![Workflow](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Flowchart.JPG)  

**Figure Team 5-2.** Haploblot of HG002 haplotypes across chr6:70–80 Mb (green = paternal, purple = maternal)  
![Haploblot](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Figure%20Team%205-2.png)  

**Figure Team 5-3.** Distribution of haplotype block sizes. Vertical dashed lines = smallest (0 bp) and largest (199,542 bp) blocks  
![Block size distribution](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Figure%20Team%205-3.png)  

**Figure Team 5-4.** Variant density histogram (100 kb bins) showing heterogeneous SNP density across the interval  
![Variant density](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Figure%20Team%205-4.png)  

**Figure Team 5-5.** Divergence between hap1 and hap2, with red ticks marking heterozygous differences  
![Hap divergence](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Figure%20Team%205-5.png)  

---

### Table  

**Table Team 5-1.** Consensus sequence composition (length, GC content, N bases) for HG002 consensus, hap1, and hap2  
[View Table (CSV)](https://github.com/collaborativebioinformatics/Human_Haploblock_Lengths/blob/main/Table%20Team%205-1.csv)  

---

## 🚀 Future Directions  

This workflow establishes a proof-of-concept for fine-scale recombination mapping in human trios. Future directions include scaling the analysis to the whole genome and across multiple trios to generate population-level recombination landscapes. The integration of long-read assemblies and trio-aware phasing algorithms will refine haploblock boundaries, while the adoption of pangenome graph references will allow hotspot detection in structurally complex regions that are inaccessible to linear references. Linking recombination hotspots with regulatory annotations and disease-associated loci will further bridge evolutionary insights with clinical genomics. Longer-term, the pipeline can be extended into a reproducible open-source framework, enabling machine learning approaches to predict recombination patterns from sequence features and epigenomic signals.  

---

## 📚 References  

1. Agarwal I, et al. *Fine-scale recombination landscapes.* Nat Commun. 2024. [link](https://www.nature.com/articles/s41467-024-50079-5)  
2. Nurk S, et al. *Telomere-to-telomere assembly of a complete human genome.* Nature. 2025. [link](https://doi.org/10.1038/s41586-025-09140-6)  
3. Halldorsson BV, et al. *Population-scale recombination maps.* Nat Genet. 2023. [link](https://pubmed.ncbi.nlm.nih.gov/36711673/)  
4. NIST Genome in a Bottle Consortium. [link](https://www.nist.gov/programs-projects/genome-bottle)  
5. Human Pangenome Reference Consortium. [link](https://pubmed.ncbi.nlm.nih.gov/40702183/)  
6. Eizenga JM, et al. *Pangenome graph resources.* Nat Biotechnol. 2023.  
7. Liao W-W, et al. *Graph genomes in practice.* Nat Methods. 2024.  

---

🙌 Special thank you to the organizers of the BCM Hackathon 2025!
