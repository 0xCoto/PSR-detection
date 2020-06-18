# PSR-detection
Source (software &amp; hardware) for the [not-yet-achieved] first ever Pulsar detection in Greece

## Software

### Data acquisition & pre-processing
Pulsar channelizer (GNU Radio flowgraph that performs real-time digital signal processing and writes the data directly to a filterbank-formatted file for further processing & analysis with e.g. [PRESTO](https://github.com/scottransom/presto)).

### Data analysis
[PRESTO](https://github.com/scottransom/presto) for de-dispersion and folding (DM-search and P-search also used).

## Hardware
- **Parabolic antenna aperture:** 1.5m ([PICTOR](https://github.com/0xCoto/PICTOR))
- **Feed:** [Cloverleaf Antenna](https://arxiv.org/pdf/1708.08521.pdf) (identical to the used on [CHIME](https://chime-experiment.ca))
- **First-stage LNA:** [Mini-Circuits ZX60-P103LN+](https://www.minicircuits.com/pdfs/ZX60-P103LN+.pdf) (NF ≈ 0.4 dB, G ≈ 20 dB)
- **In-line amplifier:** [Mini-Circuits ZX60-P103LN+](https://www.minicircuits.com/pdfs/ZX60-P103LN+.pdf) (NF ≈ 0.4 dB, G ≈ 20 dB)
- **Transmission line:** 3-meter LMR-400 Coaxial Cable (insertion loss: ~0.3 dB)
- **Receiver:** [LimeSDR Mini](https://wiki.myriadrf.org/LimeSDR-Mini)\*
- **Computer for real-time DSP:** [Jetson Nano Developer Kit](https://developer.nvidia.com/embedded/jetson-nano-developer-kit)\*

*\*Installed inside a custom-built double-shielded Faraday cage for EMI mitigation and EMC maximization.*
