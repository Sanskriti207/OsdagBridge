# Osdag Bridge
## Overview
This repository contains the source code for Osdag bridge component of [Osdag](https://github.com/osdag-admin/Osdag).
## Technical Stack

OsdagBridge is a modular, shared-core software plugin for the analysis and design of steel bridges within the Osdag ecosystem.  
It supports desktop (PySide6), web (Django + React), and CLI interfaces through a unified Python core.

The system currently supports:
- Plate Girder Bridges  
 

Additional bridge types can be added through the plugin architecture.

---

## Key Features

### Shared Core Architecture
All numerical logic and I/O are implemented once in `osdagbridge.core`.  
The desktop GUI, web app, and CLI all reuse the same core for consistent behavior.

### Modular Bridge-Type System
Each bridge type includes:
- DTO (input model schema)
- Initial sizing routines
- Structural analysis configuration
- Design and code-check modules
- CAD geometry generation
- Report generation utilities

### Reusable Bridge Components
Common structural elements are defined in `bridge_components/`:
- Girders  
- Decks  
- Crash barriers  
- Pedestals  
- Piers  
- Foundations  
- Piles and pile caps  

Components are shared across multiple bridge types.

### Multi-Solver Analysis Support
Multiple analysis backends are supported:
- Native lightweight FEM solver  
- OpenSeesPy  
- OspGrillage  

Solvers are switchable at runtime via adapters.

### Integrated Indian Standards
Included under `core/utils/codes/`:
- IRC:6–2017  
- IRC:22–2015  
- IRC:24–2010  

These modules provide load models, combinations, material factors, and code checks.

---

## Project Structure

```
OsdagBridge/
├── docs/
├── examples/
├── tests/
└── src/
    └── osdagbridge/
        ├── core/              # Analysis, design, IO, solvers, codes
        ├── bridge_types/      # Plate girder, box girder, truss
        ├── bridge_components/ # Reusable components
        ├── cli/               # Command-line interface
        ├── desktop/           # PySide6 GUI
        └── web/               # Django + React web stack
```
