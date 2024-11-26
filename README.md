# Probe Seek v1.10

A useful tool for quickly finding viable probes for any DNA sequence. Want to perform an experiment like probe hybridisation capture on a specific region of DNA but can't be bothered to spend time manually blasting sequences, checking Tm, and sequence quality? Here is a script that allows you to rapidly generate candidate probes for target enrichment.

## File description

* **Customisable**: Simply input your sequence of interest (tested up to 10kb but likely can input much larger) and adjust the parameters:
* **Adjust**: Probe length, distance between probes, ideal Tm, allowed GC content, homopolymer length and more!

## How it works
* Probe Seek takes your sequence and breaks it into small chunks *(default: 50 bp with 25 bp overlap between chunks)* and performs blastn locally to identify all viable regions that are unique or semi-unique (follow [directions online](https://dbsloan.github.io/TS2019/exercises/local_blast.html) or ask ChatGPT to set this up on your computer).
* Once all unique regions are mapped (green), probe design is performed by scanning across your viable sequences, adjusting length and spacing to meet your desired probe parameters. The script automatically alternates between forward and reverse complimentary with your target.
* The final probes are exported, along with a pretty little chunk uniqueness map showing your probes. 

![chunk_uniqueness map](https://github.com/user-attachments/assets/882645b4-9b32-4d29-8a6d-5377f293d994)
Green = unique (ideal!), Orange = 2-3 instances in reference genome (avoid on 3' end of probe and must be <50% of probe sequence), Red: > 3 instances (avoid), Purple = 0 instances (avoid) <-- happens if you have a deletion/indel

Forward probes = black, Reverse probes = blue


## Default parameters
**Blast Search:**
* I used the hg.38 human genome but you could input any genome you want to blast your sequence against
* Evalue: 1e-5
* word_size: 11
* Dust: "no"
* Chunk size: 50
* Chunk overlap: 25

**Probe design:**
* Probe length: 100 bp
* Probe spacing 250 bp
* Probe Melting Temperature: 75-80ºC based roughly on NEB Tm Calculator Q5 Hotstart polymerase (this can easily be adjusted for your desired kit, just modify mt.Tm_NN
* GC content: 40-60%
* Max homopolymer length: 5

## Authors
* J. Alexander Chalk

Happy probing!
