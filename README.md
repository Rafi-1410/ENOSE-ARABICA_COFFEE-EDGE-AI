# Edge-AI Electronic Nose for Arabica Coffee Quality Assessment

An electronic nose (e-nose) that classifies Arabica coffee as **High Grade** or **Low Grade** from its volatile aroma, with machine-learning inference running on an **NVIDIA Jetson Orin Nano** edge device.

This repository accompanies the paper *"Development of an Edge-AI-based Electronic Nose for Quality Assessment of Arabica Coffee"* (IEEE Sensors Journal, accepted 2026) and documents the on-device measurements of the five models compared in the study.

![System overview](docs/figures/system_overview.png)

*Figure: (a) system architecture, (b) monitoring GUI, (c) gas sensor array PCB, (d) electronics enclosure with the Jetson Orin Nano, (e) sampling setup. Reproduced from the authors' paper [1].*

---

## System overview

| Stage | Components |
|---|---|
| Sampling | Mini heater with coffee powder, inlet/outlet pumps and valves, sensor chamber |
| Sensing | 8 metal-oxide gas sensors: TGS2600, TGS2602, TGS2611, TGS2620, MQ3, MQ6, MQ7, MQ135 |
| Acquisition | Signal conditioning (filter + amplifier) and ESP32-S3, streamed over serial USB |
| Edge inference | NVIDIA Jetson Orin Nano with a monitoring GUI |
| Output | High Grade / Low Grade classification |

Models compared: **SVM, Random Forest, MLP, 1D-CNN and LSTM**, evaluated with Leave-One-Origin-Out (LOOO) validation across 12 coffee origins.

---

## Jetson Orin Nano measurements

All values below were measured on the Jetson Orin Nano. Power, thermal and resource figures were logged during training.

| Model | Inference latency (single sample) | Model size | Parameters | Avg / peak total power | Avg CPU+GPU power | Energy used | Training time |
|---|---|---|---|---|---|---|---|
| SVM | 0.001051 ms | 5.20 KB | 101 | 10.89 W / 10.91 W | 5.39 W | 6.5 J | 720 ms |
| Random Forest | 0.001079 ms | 71.48 KB | 1,500 | 7.33 W / 9.27 W | 2.42 W | 145.2 J | 20.68 s |
| MLP | 0.022010 ms | 439.22 KB | 21,314 | 9.48 W / 9.98 W | 4.30 W | 292.1 J | 31.69 s |
| 1D-CNN | 0.954360 ms | 3,243.44 KB | 182,978 | 9.81 W / 11.31 W | 4.55 W | 11,472.7 J | 20.20 min |
| LSTM | 2.594 ms | 349.90 KB | 642 | 9.09 W / 11.37 W | 3.85 W | 59,648.0 J | 113.11 min |

### Full measurement reports (PDF)

- [SVM](reports/jetson/Jetson_Measurement_SVM.pdf)
- [Random Forest](reports/jetson/Jetson_Measurement_RF.pdf)
- [MLP](reports/jetson/Jetson_Measurement_MLP.pdf)
- [1D-CNN](reports/jetson/Jetson_Measurement_CNN.pdf)
- [LSTM](reports/jetson/Jetson_Measurement_LSTM.pdf)

Each report includes model configuration, inference latency, power, CPU/GPU temperature, RAM and GPU utilisation, and energy use.

---

## Repository structure

```
.
├── README.md
├── docs/
│   └── figures/
│       └── system_overview.png
└── reports/
    └── jetson/
        ├── Jetson_Measurement_SVM.pdf
        ├── Jetson_Measurement_RF.pdf
        ├── Jetson_Measurement_MLP.pdf
        ├── Jetson_Measurement_CNN.pdf
        └── Jetson_Measurement_LSTM.pdf
```

---

## Publication

[1] [Authors], "Development of an Edge-AI-based Electronic Nose for Quality Assessment of Arabica Coffee," *IEEE Sensors Journal*, 2026 (accepted). DOI: [to be added on publication]

Preprint: [TechRxiv, doi:10.36227/techrxiv.177204616.68724692](https://doi.org/10.36227/techrxiv.177204616.68724692)

If you use this work, please cite the paper above.

---

## Author

**Muhammad Rafi Cahyafazri**, second author of [1]
AI and Edge Compute Researcher, National Taiwan University of Science and Technology (NTUST)
[LinkedIn](https://www.linkedin.com/in/muhammad-rafi-cahyafazri)
