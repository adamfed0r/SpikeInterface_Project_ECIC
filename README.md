# Linking Membrane Potentials and Extracellular Population Signals Using Ground-Truth Recordings
**Bachelor's Thesis Project**

**by adamfed0r**

Analysis pipeline for simultaneous extracellular (EC) and intracellular (IC)
electrophysiological recordings from *in vitro* rat hippocampal slices.

The project uses [SpikeInterface](https://spikeinterface.readthedocs.io/) to
load, preprocess, analyze, and visualize extracellular recordings acquired with
a custom **Spiky** electrode. It also contains scripts and notebooks for
local-field-potential (LFP) processing and exploratory statistical analysis.

> **Note:** Raw recordings are not included in this repository.

---

## Experimental context

The dataset contains simultaneous recordings from hippocampal brain slices:

- **Intracellular recording (IC):** patch-clamp measurement
- **Extracellular recording (EC):** custom one-shank, 32-channel Spiky probe
- **Imaging Providing 3D Morphological Data:** two-photon (2P) imaging

The extracellular recordings are spike-sorted with **KiloSort** and manually
curated in **Phy** before being imported into SpikeInterface for downstream
quality control, waveform analysis, and visualization.

## Repository structure

```text
.
├── SI_analysis_complete.ipynb   # Main SpikeInterface analysis workflow
├── stat_anal.ipynb              # Statistical / exploratory analysis
├── spiky_25.json                # ProbeInterface definition: 25 µm configuration
├── spiky_50.json                # ProbeInterface definition: 50 µm configuration
├── LFP codes/
│   └── ...                      # LFP loading, filtering, and export workflows
└── README.md
```

### Main files

| File / directory | Purpose |
|---|---|
| `SI_analysis_complete.ipynb` | Loads recordings and curated sortings, creates a `SortingAnalyzer`, computes quality metrics, and launches visualization tools. |
| `LFP codes/` | Preprocessing and analysis workflows for low-frequency extracellular signals. |
| `stat_anal.ipynb` | Statistical analysis and result exploration. |
| `spiky_25.json` | Probe geometry for the 25 µm Spiky probe configuration. |
| `spiky_50.json` | Probe geometry for the 50 µm Spiky probe configuration. |

---

## Analysis workflow

The principal extracellular spike-sorting analysis follows this sequence:

1. Load the raw extracellular recording into a SpikeInterface `Recording`.
2. Attach the appropriate Spiky probe definition.
3. Apply preprocessing as required (for example, filtering and referencing).
4. Import KiloSort output after curation in Phy as a `Sorting`.
5. Create a SpikeInterface `SortingAnalyzer`.
6. Compute waveform features and unit-quality metrics.
7. Inspect units and metrics using the SpikeInterface GUI or widgets.
8. Export results for statistical analysis and comparison with IC/LFP data.

---

## Probe definitions

The files `spiky_25.json` and `spiky_50.json` store probe geometries compatible
with ProbeInterface.

Always verify that:

- Channel IDs in the recording match the probe-contact channel IDs.
- The selected JSON file corresponds to the probe used in the experiment.
- Units, contact positions, and device-channel indices are correct before
  waveform extraction or spatial visualization.

---

## Expected inputs

The workflow assumes access to:

- Raw extracellular recording files supported by SpikeInterface.
- A valid Spiky probe configuration (`spiky_25.json` or `spiky_50.json`).
- KiloSort output for the same recording.
- Curation labels and cluster information from Phy, when applicable.
- Metadata describing sampling frequency, channel mapping, experimental
  condition, and recording session.

---

## Outputs

Typical outputs produced or inspected by the pipeline include:

- Unit IDs and curated spike trains
- Spike waveforms and templates
- Firing rates and inter-spike-interval statistics
- Signal-to-noise ratio and other quality metrics
- Unit locations and channel-localization information
- LFP-filtered recordings and derived features
- Figures and tables for downstream statistical analysis

## Status

This repository is under active development. Some notebooks, especially
statistical analysis components, may be exploratory or incomplete.

Future work will include:
- Sharp-Wave Detection,
- Quality Metrics and Statistical Analysis on the spike-sorted recordings,
- IC-LFP Comparison for Describing the Patched Cell's activity in relation to the LFP

---

## Contributors

- **Ádám Fedor**

---

## Citation

If you use this repository, please cite the relevant experimental work and the
software packages used in the analysis:

- SpikeInterface
- ProbeInterface
- KiloSort
- Phy

Please also acknowledge the development of the Spiky extracellular electrode by
Domokos Meszéna, PhD, where appropriate.
