# PSR-detection
Source (software &amp; hardware) for Pulsar detection

## Software

### RFI analysis
- [CygnusRFI](https://github.com/0xCoto/CygnusRFI) for **frequency-domain** search.
- [VIRGO](https://github.com/0xCoto/VIRGO) for **time-domain** analysis.

### Pulsar data acquisition & pre-processing
- Pulsar channelizer (GNU Radio flowgraph that performs real-time digital signal processing and writes the data directly to a filterbank-formatted file for further processing & analysis with e.g. [PRESTO](https://github.com/scottransom/presto)). To be uploaded.

### Pulsar data analysis
- [PRESTO](https://github.com/scottransom/presto) for de-dispersion and folding (DM-search and P-search also used).
- Potentially a variation of [simpleReader](https://github.com/0xCoto/simpleReader) in the future for further feature support.

## Hardware
- **Parabolic antenna aperture:** 1.5m ([PICTOR](https://github.com/0xCoto/PICTOR))
- **Feed:** [Cloverleaf Antenna](https://arxiv.org/pdf/1708.08521.pdf) (identical to the one used on [CHIME](https://chime-experiment.ca))
- **First-stage LNA:** [Mini-Circuits ZX60-P103LN+](https://www.minicircuits.com/pdfs/ZX60-P103LN+.pdf) (NF ≈ 0.4 dB, G ≈ 20 dB)
- **In-line amplifier:** [Mini-Circuits ZX60-P103LN+](https://www.minicircuits.com/pdfs/ZX60-P103LN+.pdf) (NF ≈ 0.4 dB, G ≈ 20 dB)
- **Transmission line:** 3-meter LMR-400 Coaxial Cable (insertion loss: ~0.3 dB)
- **Receiver:** [LimeSDR Mini](https://wiki.myriadrf.org/LimeSDR-Mini)\*
- **Computer for real-time DSP:** [Jetson Nano Developer Kit](https://developer.nvidia.com/embedded/jetson-nano-developer-kit)\*

*\*Installed inside a custom-built double-shielded Faraday cage for EMI mitigation and EMC maximization.*

### RFI mitigation from hardware
For EMI suppresion (spurious emission reduction), two Faraday cages were considered: one that had a single layer of shielding, and one that had a double layer of shielding (custom-built with two fans for heat dissipation). For a sample frequency of **460 MHz**, preliminary EMI tests (conducted with [CygnusRFI](https://github.com/0xCoto/CygnusRFI)) have given the following results:
![Preliminary EMI Test Results](https://i.imgur.com/aNMDl4k.png)

The apparent inconsistency appears to be due to SDR noise floor variability with time (e.g. SDR temperature (T) is proportional to the system noise temperature (T_sys) and dT/dt ≠ 0). Therefore, because the measurements were taken at slightly different times (waiting for each measurement to finish), the noise floor varies (T ∝ T_sys ∧ dT/dt ≠ 0 ∴ dT_sys/dt ≠ 0)). Besides internal factors, T_ant variability (caused by DUT-unrelated RFI) may also have a significant impact.

### Further EMC updates
Further preliminary EMI checks, this time on a different receiving computer candidate:
![EMI Check](https://i.imgur.com/Vkt4Ihi.jpg)

##### Reference level
EMI Source (DUT under suspicion) out of the antenna's beam (equivalent to turning it off):
![EMI Check](https://i.imgur.com/zC0v21f.jpg)

##### EMI Source in front of the beam
![EMI Check](https://i.imgur.com/HsgBkaM.jpg)

##### Narrower span
![EMI Check](https://i.imgur.com/AdguLUM.jpg)

##### Pulse profile span
![EMI Check](https://i.imgur.com/FjZIeI2.jpg)

More to be added soon...
