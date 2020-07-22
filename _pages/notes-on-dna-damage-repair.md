---
layout: archive
title: "Notes on DNA damage repair"
permalink: /dna-damage-repair/
---

{% include base_path %}

These notes are heavily based on [Chatterjee and Walker](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5474181/).

## General remarks 

### On DNA damage repair

* 10^5 spontaneous or induced DNA lesions *per* day in humans ([De Bont and van Larebeke](https://pubmed.ncbi.nlm.nih.gov/15123782/)). This makes the importance for DNA damage repair (DDR) quite clear. Five major DNA repair pathways act during mitosis - base excision repair (BER), nucleotide excision repair (NER), mismatch repair (MMR), homologous recombination (HR) and non-homologous end joining (NHEJ) - and interstrand crosslink is capable of directly chemically reversing the damage. Translesion synthesis (TLS) polymerases are capable of bypassing the error (i.e. insterting the correct base on the replicated strand even if the one on the template strand is mutated) but often have a high error rate ([Chatterjee and Walker](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5474181/)).
* Proteins responsible for damage detection have some affinity for nondamaged DNA as well, but since damage repair is a multistep process it is unlikely that this general affinity for DNA may lead to erroneous repair ([Sancar *et al.*](https://www.annualreviews.org/doi/full/10.1146/annurev.biochem.73.011303.073723)).
* Two main types of damage can be identified, **endogenous** and **exogenous**.
* **Endogenous** damage arises from DNA molecules participating in hydrolytic reactions with water and oxidative reactions with reactive oxygen species (ROS)
	* Upon mitosis, $3 * 10^9$ bases are replicated with _high_ fidelity by two polymerases - $\delta$ (*POLD*) and $\epsilon$ (*POLE*). However, several other _low_ fidelity polymerases will participate in DNA replication and damage repair, namely $\alpha$, $\beta$, $\sigma$, $\gamma$, $\lambda$, REV1, $\zeta$, $\iota$, $\eta$, $\kappa$, $\mu$, $\theta$, $\mu$, Tdt and PrimPol ([Loeb and Monnat](https://pubmed.ncbi.nlm.nih.gov/18626473/)). High fidelity replication is obtained thanks to not only lower error insertion rates but also to DDR mechanisms executed by the polymerase. In addition to this MMR contributes to improving rare error correction by 100-fold. However, this does not prevent the cell from accumulating insertion and deletion errors at a rate of $10^{-6}$ to $10^{-5}$ per cell division ([Kunkel](https://pubmed.ncbi.nlm.nih.gov/14988392/), [Kunkel](https://pubmed.ncbi.nlm.nih.gov/19903750/), and [Kunkel](https://pubmed.ncbi.nlm.nih.gov/21862387/)). 
	* On top of this, **strand slipage** (spontaneous shifts in the strand while replicating) can happen, **uracil can be wrongly incorporated in the DNA strand** and **topoisomerases** (enzymes responsible for removing hyperhelical tension in the DNA) can accidentally join the wrong strands.
	* Additionally, we must also consider **spontaneous base deamination**, where cytosine, adenine, guanine, and 5-methyl cytosine get converted to uracil (pairs with adenine), hypoxanthine (binds cytosine), xanthine (binds cytosine) and thymine, respectively. This is more prone to happen with single stranded DNA and the circumstances that increase "single-strandedness" lead to increased. Cytosine deamination plays a crucial role in antibody development through APOBEC1
	* During BER, **abasic sites** are formed. These sites are formed by breaking the N-glycosyl bond between the nitrogenous base and the phosphate backbone and their formation is positively impacted by high temperatures and extreme pH conditions. This typically leads to single-strand breaks, which are quickly repaired as a part of BER or bypassed by TLS polymerases. 
	* **ROS** are typically produced by cells but, when in excess, can lead to many forms of 2-deoxyribose modifications, making them a powerful mutating agent. Cells will typically control their impact on DNA by moderating mytochondria activity, rolling DNA in histones and through the quenching of ROS surplus by anti-oxidant enzymes. The most reactive ROS is the hydroxyl radical, which can open or oxidise DNA bases and cause breaks on the backbone. In the first case this is repaired by BER, whereas the latter case is repaired by single strand break repair (SSBR)
	* **DNA methylation** can be cause by S-adenosylmethionine (SAM), a methyl donor used by methyl transferases, nitrosated bile salts, betaine, choline, tobacco smoke, specific diets, pollution or derivatives of N-nitroso compounds. N7-methylguanine, N3-methyladenine and $O^6$-methylguanine are the products of these reactions, with the latter (and associated products) being associated with G:C --> A:T and T:A --> C:G transitions. Two pathways can remove this damage: direct reversal of DNA damage with $O^6$-methylguanine and BER. DNA methylation is a major source of spontaneous DNA damage. 
* **Exogenous** DNA damage involves, as the name implies, external sources of damage. This includes UV and ionizing radiation and crosslinking agents, for example

