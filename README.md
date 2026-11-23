⚠️ Work in progress, not ready for production.

# Sprof generator in Python

This tool is a Python implementation of [matsprof](https://github.com/euroargodev/matsprof), a stand-alone version of the "nc_create_synthetic_profile" tool used at the Coriolis GDAC to generate mono-cycle synthetic profile (S-PROF) files (from C and B mono-cycle (C-PROF and B-PROF) files).

See http://doi.org/10.13155/55637 for details.

This module will be available in January 2027.


## API Design

### Argopy integration

If `output_dir` is not specified, only the `xr.Dataset` is return, otherwise netcdf file is created on disk.

```python
import argopy as ar

af = ar.ArgoFloat(6903091)

# Create the multi-profile synthetic file: 
af.sprof.make_multi(Optional[output_dir]: Path = None)

# Create one or more single mono-profile file(s):
af.sprof.make_mono(cyc: int | List[int], Optional[output_dir]: Path = None)  
```

### Standalone application

If `output_dir` is not specified, only the `xr.Dataset` is return, otherwise netcdf file is created on disk.

```python
from pysprof import sprof_multi, sprof_mono

# Create the multi-profile synthetic file: 
sprof_multi(wmo_input_dir: Path, Optional[output_dir]: Path = None, core_wmo_input_dir: Optional[Path], b_wmo_input_dir: Optional[Path])

# Create one or more single mono-profile file(s):
sprof_mono(wmo_input_dir: Path, cyc: int | List[int], Optional[output_dir]: Path = None, core_wmo_input_dir: Optional[Path], b_wmo_input_dir: Optional[Path])
```

As a ``cli``:
```bash
# multi-profile:
sprof make --src="/path/gdac/coriolis/6903091" --dest="/my_floats/WMO/6903091"

# mono:
sprof make --src="/path/gdac/coriolis/6903091/profiles/BD6903091_012.nc" --dest="/my_floats/WMO/6903091/profiles/S6903091_012.nc"
```
