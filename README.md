# Electric Vehicle Charging Station Allocation Problem (EVCSAP)

## Overview

This repository contains the research implementation for the **Stochastic Programming approach to Electric Vehicle Charging Station Allocation Problem (SP-EVCSAP)**. The project addresses the optimal placement and sizing of electric vehicle charging stations under demand uncertainty, incorporating grid constraints and multiple objectives.

## 🎯 Project Scope

This research focuses on:
- **Stochastic Programming Models** for EV charging station allocation
- **Multi-period Dynamic Planning** with demand uncertainty
- **Grid Integration Constraints** for sustainable infrastructure
- **Optimization Algorithms** using Pyomo and commercial solvers
- **Data-Driven Scenario Generation** for demand modeling

## 📁 Repository Structure

```
├── Documentation/           # Project documentation and research outputs
│   ├── *.pdf               # Technical documentation
│   └── *.xlsx              # Model input data and graph data
├── journal_ver_2025_data_codes/
│   ├── Data/               # Processed datasets (included)
│   ├── *.ipynb            # Jupyter notebooks for analysis
│   └── archived_dec2022_tests/  # Historical test results
├── Thesis_latex/           # LaTeX thesis documents
├── draft_comparison/       # Comparative analysis materials
└── py_env_setup/          # Python environment configuration
```

## 🔬 Research Contributions

1. **Novel Stochastic Programming Formulation**: Incorporates demand uncertainty and grid constraints
2. **Multi-Period Planning Framework**: Addresses temporal aspects of infrastructure development
3. **Comprehensive Data Processing Pipeline**: Handles real-world EV adoption and travel patterns
4. **Scalable Optimization Approach**: Tested on realistic problem instances

## 🚀 Getting Started

### Prerequisites

- Python 3.8+ (see `py_env_setup/requirements.txt`)
- Optimization solver (Gurobi, CPLEX, or CBC)
- Jupyter Notebook environment

### Environment Setup

1. Create a Python virtual environment:
```bash
pip install -r py_env_setup/requirements.txt
```

2. For conda users:
```bash
conda env create -f py_env_setup/EVCSAP_env_list.yml
```

### Data Access

The repository includes processed data files in the `journal_ver_2025_data_codes/Data/` directory. 
Model implementation files are excluded for confidentiality but the data structure and analysis notebooks are provided.

## 📊 Key Features

- **Stochastic Scenario Generation**: Creates realistic demand scenarios
- **Multi-Objective Optimization**: Balances cost, service quality, and grid stability
- **Scalable Implementation**: Handles networks with hundreds of potential locations
- **Comprehensive Analysis Tools**: Statistical evaluation and visualization

## 🎓 Academic Context

This work is part of a PhD thesis at Technical University of Munich (TUM), focusing on sustainable transportation infrastructure planning under uncertainty.

## 📝 Publications

Research findings from this project have been submitted to peer-reviewed journals in operations research and sustainable transportation.

## 📄 License

This project is for academic research purposes. Please contact the author for usage permissions.

## 👥 Contact

**Author**: Gen Li  
**Affiliation**: Technical University of Munich (TUM)  
**Email**: ge75pax@mytum.de

## 🙏 Acknowledgments

- Technical University of Munich for research support
- Industry partners for providing real-world data insights
- Open-source optimization community for tool development

---

*Note: This repository contains the public-facing components of the research. Sensitive model implementations and proprietary data are handled separately under appropriate confidentiality agreements.*