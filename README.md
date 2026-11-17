# dwreml-bin

### Precompiled dwreml `R` packages

Binary `dwreml` packages for

- macOS (Apple Silicon),
- macOS (Intel),
- Linux (x86_64)
  - a recent Ubuntu build (Uxx.xx, glibc >= 2.41)
  - built on an older OS requiring glibc >= 2.31, and
- Windows (x86_64)

are available under the
[releases](https://github.com/mmaedhub/dwreml-bin/releases) tab.

## Installation

For macOS on Apple Silicon (for example), install from the system command line with

```shellscript
> R CMD INSTALL dwreml_1.0.95_Darwin_arm64.tgz
```

or at the `R` console using

```R
> install.packages("dwreml_1.0.95_Darwin_arm64.tgz", repos = NULL)
```

or interactively from within `R-gui`, `Rstudio` or `R.app`. Replace the above
package name with the appropriate target archive.

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