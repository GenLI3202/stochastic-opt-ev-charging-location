# Environment Setup Guide

This directory contains all necessary configuration files to set up the development and runtime environment for the **Electric Vehicle Charging Station Allocation Problem (SP-EVCSAP)** project.

## 📋 Quick Start

### Option 1: Conda Environment (Recommended)

```bash
# Create and activate the conda environment
conda env create -f conda/environment.yml
conda activate evcsap

# Verify installation
python -c "import pyomo, geopandas, plotly; print('Environment ready!')"
```

### Option 2: Pip Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate
# Activate (Linux/macOS)
source venv/bin/activate

# Install dependencies
pip install -r pip/requirements.txt

# For development
pip install -r pip/requirements-dev.txt
```

### Option 3: Docker Environment

```bash
# Build the container
docker build -f docker/Dockerfile -t evcsap .

# Run with mounted workspace
docker run -it -v ${PWD}:/workspace evcsap
```

## 🛠️ Detailed Setup Instructions

### Prerequisites

- **Python 3.8+** (3.8 recommended for compatibility)
- **Git** for version control
- **Conda** (Anaconda/Miniconda) or **pip** for package management
- **Docker** (optional, for containerized environment)

### Commercial Solver Setup (Optional but Recommended)

The project supports multiple optimization solvers:

#### CPLEX (IBM Academic License)
```bash
# After obtaining CPLEX license
pip install cplex
# or
conda install cplex
```

#### Gurobi (Academic License)
```bash
# After obtaining Gurobi license
pip install gurobipy
# or
conda install gurobi
```

#### Open Source Alternatives
- **CBC**: Included in conda environment
- **IPOPT**: Included for nonlinear optimization
- **GLPK**: Available via conda

### Platform-Specific Instructions

#### Windows
```powershell
# Using Conda (recommended)
conda env create -f conda/environment.yml
conda activate evcsap

# Using pip with virtual environment
python -m venv venv
venv\Scripts\activate
pip install -r pip/requirements.txt
```

#### Linux/macOS
```bash
# Using Conda (recommended)
conda env create -f conda/environment.yml
conda activate evcsap

# Using pip with virtual environment
python3 -m venv venv
source venv/bin/activate
pip install -r pip/requirements.txt
```

#### Visual Studio Code
1. Install the Python extension
2. Open the project folder
3. Select the conda environment (`evcsap`) as the Python interpreter
4. Install recommended extensions from `.vscode/extensions.json`

## 🔧 Development Environment

### Pre-commit Hooks
```bash
# Install pre-commit hooks (included in dev requirements)
pre-commit install

# Run hooks manually
pre-commit run --all-files
```

### Code Quality Tools
```bash
# Format code
black .
isort .

# Lint code
flake8 .
pylint src/

# Type checking
mypy src/
```

### Testing
```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src tests/

# Run specific test file
pytest tests/test_optimization.py
```

## 📁 Directory Structure

```
environment/
├── conda/
│   └── environment.yml          # Complete conda environment
├── pip/
│   ├── requirements.txt         # Core pip dependencies
│   └── requirements-dev.txt     # Development dependencies
├── docker/
│   ├── Dockerfile              # Production container
│   └── docker-compose.yml      # Multi-service setup
├── development/
│   ├── .pre-commit-config.yaml # Pre-commit hooks
│   ├── .flake8                 # Linting configuration
│   ├── .isort.cfg              # Import sorting
│   ├── pyproject.toml          # Black, pytest config
│   └── mypy.ini                # Type checking
└── README.md                   # This file
```

## 🔍 Troubleshooting

### Common Issues

#### Import Errors
```bash
# Verify environment activation
conda info --envs
# or
which python

# Reinstall problematic packages
conda install --force-reinstall <package>
# or
pip install --force-reinstall <package>
```

#### Solver Issues
```bash
# Test solver availability
python -c "import pyomo.opt; print(pyomo.opt.SolverFactory('cbc').available())"
python -c "import pyomo.opt; print(pyomo.opt.SolverFactory('ipopt').available())"
```

#### Geospatial Dependencies
```bash
# Common fix for GDAL/Fiona issues
conda install gdal fiona geopandas --force-reinstall -c conda-forge
```

#### Jupyter Kernel Issues
```bash
# Register kernel with Jupyter
python -m ipykernel install --user --name evcsap --display-name "EVCSAP (Python 3.8)"
```

### Environment Verification

Run the verification script to ensure all components are working:

```python
# verification_script.py
import sys
import importlib

required_packages = [
    'numpy', 'pandas', 'geopandas', 'pyomo', 
    'plotly', 'folium', 'jupyter', 'matplotlib'
]

print(f"Python version: {sys.version}")
print("\nPackage verification:")

for package in required_packages:
    try:
        mod = importlib.import_module(package)
        version = getattr(mod, '__version__', 'unknown')
        print(f"✓ {package}: {version}")
    except ImportError:
        print(f"✗ {package}: NOT FOUND")

# Test optimization solver
try:
    import pyomo.opt
    solver = pyomo.opt.SolverFactory('cbc')
    if solver.available():
        print("✓ CBC solver: Available")
    else:
        print("✗ CBC solver: Not available")
except Exception as e:
    print(f"✗ Solver test failed: {e}")
```

## 📞 Support

For environment setup issues:
1. Check this README first
2. Verify prerequisites are installed
3. Try recreating the environment from scratch
4. Check the project's main README for additional context

## 🔄 Environment Updates

### Updating Dependencies
```bash
# Update conda environment
conda env update -f conda/environment.yml --prune

# Update pip requirements
pip install -r pip/requirements.txt --upgrade
```

### Adding New Dependencies
1. Add to appropriate requirements file
2. Test in clean environment
3. Update this README if needed
4. Commit changes to version control

---

**Note**: This project was developed for research purposes. Some dependencies may require academic licenses for full functionality.