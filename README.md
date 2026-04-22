# NumericalEarthArtifacts

Fallback data artifacts for [NumericalEarth.jl](https://github.com/NumericalEarth/NumericalEarth.jl) tests.

## Purpose

This repository stores test data files as GitHub Release assets. When the original data sources
(Dropbox, NASA ECCO, ORNL ESGF, UK Met Office, NOAA NCEI, etc.) are temporarily unavailable,
NumericalEarth.jl falls back to downloading from these artifacts so that CI tests continue to pass.

A warning annotation is emitted on the pull request whenever a fallback is used, so maintainers
are aware which original links are broken.

## Release structure

Data files are stored as assets on the `data-v1` release. Each file uses the same name as
the original dataset file so that the fallback URL can be constructed from the filename alone:

```
https://github.com/NumericalEarth/NumericalEarthArtifacts/releases/download/data-v1/<filename>
```

## Datasets

| Dataset | Source | Files |
|---------|--------|-------|
| JRA55 RepeatYear | Dropbox | `RYF.*.1990_1991.nc` |
| JRA55 MultiYear | ORNL ESGF | `*_input4MIPs_*.nc` |
| ECCO2/4 | NASA JPL | `THETA_*.nc`, `SALT_*.nc`, ... |
| ECCO Darwin | NASA JPL | `*.data` |
| EN4 | UK Met Office | `EN.4.2.2.f.analysis.g10.*.nc` |
| ETOPO | Dropbox | `ETOPO_2022_v1_60s_N90W180_surface.nc` |
| WOA | NOAA NCEI | `woa_{t,s}_annual.nc`, `woa_{t,s}_monthly_{01..12}.nc` |

## Adding new files

```bash
gh release upload data-v1 path/to/file.nc --repo NumericalEarth/NumericalEarthArtifacts
```
