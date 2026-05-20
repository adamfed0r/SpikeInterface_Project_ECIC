# SpikeInterface_Project_ECIC
**by adamfed0r**


## This is the complete pipeline for SpikeInterface Analysis for our datasets
It includes the following steps:
- importing libraries (np, mpl, pd, si and subfolders, probeinterface)
- creating a Recording object
- adding our own *spiky probe*
- creating a Sorting object from a KiloSort-ed and *phy* curated dataset
- creating a SortingAnalyzer
- computing various metrics
- opening the SpikeInterface GUI for visualization of the metrics and the Sorting Analyzer

## Our recordings
Simultaneous IC and EC recordings from in vitro rat hippocampus slices
IC is done with Patch-Clamp
EC is done with *spiky*, a one-shank, 32-channel "sawtooth-like" EC electrode developed by Domokos Meszéna, PhD
The recordings also include 2P imaging
