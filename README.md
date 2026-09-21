# 🚀 2026 AI Inference & Hardware Economics Telemetry Index

[![EyesTech Canonical](https://img.shields.io/badge/Canonical%20Research-EyesTech.in-002050?style=for-the-badge&logo=google-chrome)](https://eyestech.in/ai-inference-hardware-economics-statistics-tco-2026/)
[![Kaggle Dataset](https://img.shields.io/badge/Kaggle-Dataset-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/prithuvardhanmishra/2026-ai-inference-and-hardware-economics-telemetry)
[![Hugging Face](https://img.shields.io/badge/Hugging%20Face-Dataset-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co/datasets/devidasmishra/ai-inference-hardware-economics-2026)
[![PyPI](https://img.shields.io/pypi/v/eyestech-mla?color=38BDF8&label=PyPI%20Reference%20Kernel&style=for-the-badge)](https://pypi.org/project/eyestech-mla/)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg?style=for-the-badge)](https://creativecommons.org/licenses/by/4.0/)

Official open-access empirical telemetry dataset for **2026 AI Inference, Silicon Architecture, and Hardware Economics**, curated by **[EyesTech Systems & FinOps Intelligence](https://eyestech.in)**.

> 📖 **Primary Research Publication & Full Whitepaper**:  
> For the complete architectural derivations, interactive memory calculators, and per-token FinOps modeling, read the primary publication:  
> 👉 **[2026 AI Inference & Hardware Economics Telemetry: Memory Walls and Cluster TCO](https://eyestech.in/ai-inference-hardware-economics-statistics-tco-2026/)** at **[EyesTech Systems Lab](https://eyestech.in)**.

---

## 📊 Dataset Overview

This dataset compiles empirical measurements taken across **58 bare-metal production cluster configurations** across 8 hyperscaler and private datacenter providers (AWS, CoreWeave, Lambda Labs, Google Cloud, RunPod, Oracle Cloud Infrastructure, Scaleway, Crusoe Cloud).

### Serving Frameworks Audited
- **vLLM v0.9.2** (FlashAttention-3 + PagedAttention + FP8 KV Cache)
- **TensorRT-LLM v1.2.0** (FP8 / FP4 GEMM with in-flight batching)
- **Triton Inference Server 26.08**
- **Google MaxText** (TPU v5p multi-slice runtime)
- **AWS NeuronCore SDK 2.21** (Trainium2 / Inferentia2)

### Hardware Accelerators Included
- **NVIDIA H100 SXM5 80GB**
- **NVIDIA H200 SXM 141GB HBM3e**
- **NVIDIA B200 NVL72**
- **Google TPU v5p**
- **AWS Trainium2 (trn2.48xlarge)**
- **AMD Instinct MI300X 192GB**
- **NVIDIA L40S 48GB**

---

## 💾 Files Included

| File | Format | Description |
| :--- | :---: | :--- |
| `hardware_accelerators.csv` | CSV | Normalized tabular matrix of memory bandwidth, TDP, dense TFLOPs, and cloud hourly pricing. |
| `ai-inference-statistics-2026.json` | JSON | Complete hierarchical telemetry schema with model-specific TTFT, TPOT, and MTBF reliability logs. |

---

## 🔍 Data Dictionary (`hardware_accelerators.csv`)

| Column Name | Type | Description |
| :--- | :--- | :--- |
| `accelerator` | string | Silicon accelerator model name |
| `architecture` | string | Micro-architecture family (Hopper, Blackwell, CDNA3, etc.) |
| `memory_capacity_gb` | integer | Physical on-package memory capacity in Gigabytes |
| `memory_type` | string | Memory standard (HBM3, HBM3e, GDDR6, LPDDR5X) |
| `memory_bandwidth_tb_s` | float | Peak theoretical memory bandwidth (TB/s) |
| `tdp_watts` | integer | Thermal Design Power in Watts |
| `fp8_dense_tflops` | integer | Peak dense FP8 compute capability |
| `fp16_dense_tflops` | integer | Peak dense FP16 compute capability |
| `blended_cloud_hourly_rate_usd` | float | Median on-demand hourly rental cost ($/hr) |
| `reserved_3yr_hourly_usd` | float | 3-year committed enterprise rate ($/hr) |
| `idle_power_watts` | integer | Idle idle power draw per accelerator |
| `peak_inference_power_watts` | integer | Peak power draw under 128k context decoding |

---

## 🐍 Python Quickstart

```python
import pandas as pd

# Load tabular accelerator metrics
df = pd.read_csv("hardware_accelerators.csv")

# Sort by memory bandwidth efficiency
df["bandwidth_per_dollar"] = df["memory_bandwidth_tb_s"] / df["blended_cloud_hourly_rate_usd"]
top_efficiency = df.sort_values(by="bandwidth_per_dollar", ascending=False)
print(top_efficiency[["accelerator", "memory_capacity_gb", "bandwidth_per_dollar"]])
```

---

## 📑 Citation & Attribution

If you use this dataset in your research or benchmarks, please cite the primary research investigation:

```bibtex
@misc{eyestech2026hardware,
  title        = {2026 AI Inference & Hardware Economics Telemetry: Memory Walls and Cluster TCO},
  author       = {Vance, Marcus and Sethi, Arjun},
  institution  = {EyesTech Systems Lab},
  year         = {2026},
  month        = {September},
  url          = {https://eyestech.in/ai-inference-hardware-economics-statistics-tco-2026/}
}
```

*Published under Creative Commons Attribution 4.0 International (CC BY 4.0) by [EyesTech Systems Lab](https://eyestech.in).*
