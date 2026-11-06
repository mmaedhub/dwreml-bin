# dwreml-bin

### Precompiled dwreml `R` packages

Binary `dwreml` packages for

- macOS (Apple Silicon),
- macOS (Intel),
- Linux (x86_64), and
- Windows (x86_64)

are available under the
[releases](https://github.com/mmaedhub/dwreml-bin/releases) tab.

## Installation

From the system command line

```shellscript
> R CMD INSTALL dwreml_1.0.95_Darwin_arm64.tgz
```

or at the `R` console

```R
> install.packages("dwreml_1.0.95_Darwin_arm64.tgz", repos = NULL, type = "binary")
```

or interactively from within `R-gui`, `Rstudio` or `R.app`.

## Dependencies

Installing an `R` package from a local binary file will not automatically resolve or download
missing dependencies.

`dwreml` depends on

 - data.table (>= 1.16.0),
 - Matrix,
 - cli,
 - Rdpack

and _suggests_

 - dwrPlus,
 - ggplot2,
 - grid,
 - lattice,
 - grDevices,
 - stringr
 
 for non-core functionality.