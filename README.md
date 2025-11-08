# The Laboratory: A Data Scientist Gone Mad

## Overview
This notebook is an intro guide to the infrastructure, systems, and experiments of The Lab. My personal AI, ML, and Data Science Research and Development environment that has consumed and become my home. 

The Lab is not just infrastructure. It is integrated into every aspect of daily existence at a level that would make most people scream. I am by far the most digital of digital natives. The Laboratory operates as a fully self contained, high performance compute environment for continuous experimentation, reproducibility, and finding out what happens when you refuse to separate life from computation.


## Purpose
I am by nature a technologist, an engineer. I build. I tinker. Always have. The Lab exists because I need to touch the metal, feel the heat of the GPUs, hear the fans spin up when models train. This is how I think. This is how I live. No cloud abstractions. No external dependencies. Just me, the machines, and whatever I can make them do. Every system here is something I can take apart, rebuild, and push past its limits. Because that's what I do.

### The Nodes
The on-premise AI, ML, and Data Science Research and Development Lab currently consists of four active, on-prem, bare-metal linux HPC compute nodes. Each node supports internal experimentation, benchmarking, and reproducibility validation. All systems operate on Ubuntu 24.04 LTS with synchronized driver, CUDA, and library versions to maintain bit-level reproducibility.

---
**Platform Note:** All four nodes are Lenovo ThinkStation P5 and P7 towers; this standardization has been critical, enabling component interchangeability and operational consistency that mirrors real enterprise environments and scientific research and development and high-technology innvations labs. Unlike the Frankenstein custom builds that define most HPC enthusiast clusters, this approach prioritizes maintainability and reproducibility over boutique performance.

**Linux Note**: For the first time in nearly a decade, the environment runs a mostly stock GNOME desktop. From 2015 through 2024 the lab standard was pure Debian with the XFCE tiling manager introduced on Kali; that workflow defined my baseline Linux configuration for years.

### Node 001 — mad-scientist-w32445(Zenon)
* **CPU:** Intel Xeon W3-2435  
* **Memory:** 128 GB ECC DDR5  
* **GPU:** NVIDIA RTX A4000 (16 GB GDDR6)  
* **Role:** Baseline performance and benchmark reference node  
* **Commissioned:** 2025-09  

Zenon serves as the control system for environment validation and performance baselining across CUDA, PyTorch, TensorFlow, RAPIDS, and distributed-data frameworks.  

Every new configuration or driver stack is validated here before replication to the Gemini pair or Rocinate.

---

### Gemini Group(The Twins)

Two Xeon W5-2445 nodes identical in hardware and firmware form the **Gemini** pair. 

They support mirrored workload testing, distributed compute trials, and regression verification.

#### Node 002 — mad-scientist-w52445(Gemini Twin I)
* **CPU:** Intel Xeon W5-2445  
* **Memory:** 128 GB ECC DDR5  
* **GPU:** NVIDIA RTX A5500 (24 GB GDDR6)  
* **Role:** Primary production twin for mirrored and distributed workloads  
* **Commissioned:** 2024-06  

#### Node 003 — mad-derpy-w52445(Gemini Twin II / Derpy)
* **CPU:** Intel Xeon W5-2445  
* **Memory:** 128 GB ECC DDR5  
* **GPU:** NVIDIA RTX A5500 (24 GB GDDR6)  
* **Role:** Dedicated test and validation system; transient mirror of Twin I  
* **Commissioned:** 2024-06  
* **Lifecycle:** Factory-restored to stock Ubuntu 24.04.3 every ~2 weeks  

**Derpy** provides a clean-room testbed ensuring all changes to CUDA, Python environments, and ML libraries are validated in isolation before promotion to production nodes or Rocinate.  

Her transient lifecycle guarantees reproducibility and dependency-drift detection.

---

### Node 004 — mad-scientist-w72475x(Rocinate)
* **CPU:** Intel Xeon W7-2475X
* **Memory:** 128 GB ECC DDR5  
* **GPU:** NVIDIA RTX A5500 (24 GB GDDR6)  
* **Role:** High-throughput research node for compute-intensive AI, ML, and data-science experimentation  
* **Commissioned:** 2025-07  

Rocinate('Workhorse' in Spanish) is the lab workhorse for large-scale training, multi-framework benchmarking, and experimental pipeline development. 

Its W7-class processor and DDR5 memory bandwidth provide superior data-parallel throughput for tensor and GPU-accelerated workloads.  

All prototype pipelines originate here before replication to the Gemini pair for validation.

---

### Storage and Networking

* **Primary NAS:** QNAP 8-bay enclosure with 8 × 26 TB WD Red Pro drives ≈ 208 TB raw capacity  
* **Offline Control Plane:** Dual 2.5 Gbps switches dedicated to the NAS HPC Master node to worker orchestration
* **Network Segmentation:** Two independent 1.25 Gbps ISP service connections for network segmentation. 
* **Topology:** Offline NAS Control Plane + isolated research network for true physical and logical segmentation  

Even under sustained heavy workloads the current configuration provides stable throughput with ample headroom for concurrent experiments.

---

### Summary of Roles

| Group | Nodes | Function |
|--------|--------|-----------|
| **Control Node** | Zenon (001) | Environment baselines, benchmark reference |
| **Gemini Group** | Twin I (002) & Twin II (003) | Mirrored testing, regression validation, and production preparation |
| **Exploratory Node** | Rocinate (004) | High-throughput AI / ML / Data-Science research workloads |

---

This configuration defines the operational topology of the the labs HPC node cluster; a closed, reproducible, service-free environment built for end-to-end experimentation in artificial intelligence, machine learning, and data-engineering systems development.  

The intent behind these systems is to sustain genuine R&D capability at home: real hardware, controlled infrastructure, and clustering capacity beyond single-node desktop limits.

