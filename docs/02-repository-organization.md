# Repository organization

[← Tutorial home](../README.md)

Organize by **purpose**, then by component. A small project can start with a README, source code, and tests; add folders when they contain something useful. This is a suggested research project structure, not the layout of this documentation-only tutorial.

```text
research-project/
├── README.md                # What it does and how to run it
├── LICENSE                  # License chosen by the owner
├── CHANGELOG.md              # User-facing changes by version
├── .gitignore               # Local/generated files to exclude
├── assets/                  # Logo and small documentation images
├── docs/                    # Design, methods, setup, and usage
├── src/                     # Reusable implementation
├── tests/                   # Automated checks and small fixtures
├── scripts/                 # Entry points and utilities
├── examples/                # Small runnable demonstrations
├── configs/                 # Experiment/runtime settings
├── notebooks/               # Exploratory analysis
├── data/
│   ├── README.md            # Source, access, schema, and units
│   ├── raw/                 # Original inputs, usually external or ignored
│   └── processed/           # Derived inputs, usually regenerated
└── results/                 # Generated figures, logs, and metrics
```

## Folder responsibilities

| Folder | Put here | Example |
| --- | --- | --- |
| `src/` | Reusable code | `state_estimator.py`, `propagate_orbit.m` |
| `tests/` | Checks of expected behavior with small inputs | `test_rotation.py` |
| `scripts/` | Tools that call reusable code | `run_experiment.py` |
| `configs/` | Parameters with documented units/defaults | `baseline.yaml` |
| `examples/` | Minimal reproducible usage | `demo_filter.m` |
| `notebooks/` | Exploration with explained assumptions | `compare_estimators.ipynb` |
| `docs/` | Methodology and operating instructions | `coordinate_frames.md` |
| `assets/` | Small documentation images | `srge-logo.png` |
| `data/` | Data documentation and chosen fixtures | `README.md` |
| `results/` | Reproducible outputs, normally ignored | `run_001/metrics.csv` |

## Choose a language layout

- **Python:** use a package under `src/<package_name>/`, with dependency and packaging metadata in `pyproject.toml` where appropriate. Document installation before import or execution.
- **MATLAB:** keep reusable `.m` functions in `src/` and demonstrations in `examples/`. Document required MATLAB release, toolboxes, and path setup.
- **C++:** keep implementation in `src/`, public headers in `include/`, and build configuration such as `CMakeLists.txt` at the root. Build into an ignored `build/` folder.
- **ROS:** preserve ROS package structure and manifests. Document the ROS distribution, workspace build process, and launch instructions.

Use folders that fit your tools; preserve locations required by a framework.

## Names and reproducibility

Use descriptive, consistent filenames without spaces. Follow language naming conventions. Prefer `camera_calibration.yaml` over `new_config_final2.yaml`, and use Git history instead of copies named `final`, `final_v2`, or `latest`.

For each experiment, record the Git commit, configuration, input dataset version, random seed where applicable, environment, and command used. State units and reference frames explicitly. Describe how to regenerate results and retrieve external data.

Track dependency declarations and appropriate lock files. Include a small shareable input fixture so a new member can try the project without downloading the full dataset.

## Before sharing

- Can a teammate find the entry point and run a small example?
- Are dependencies, data access, units, and expected outputs documented?
- Are generated files excluded and useful fixtures included?
- Does the README reflect the actual folders and commands?
