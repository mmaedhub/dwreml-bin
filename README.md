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
R CMD INSTALL dwreml_1.0.95_Darwin_arm64.tgz
```

or at the `R` console using

```R
install.packages("dwreml_1.0.95_Darwin_arm64.tgz", repos = NULL)
```

or interactively from within `R-gui`, `Rstudio` or `R.app`, replacing the above
macOS package with the appropriate target archive.

### Dependencies

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

 ## BLAS Notes

`dwreml`, and in particular the `MUMPS` equation solver, make significant use of
the `BLAS` and `LAPACK` linear algebra libraries. Depending on the installation,
`R` may use its own _reference_ _BLAS_ which are computationally slow, or the
system-wide default libraries (Linux) which may not be optimised. Just which
libraries are in use can be checked with either
```R
sessionInfo()
```
or 
```R
La_library()             #LAPACK library in use
extSoftVersion()["BLAS"] #BLAS library in use
```
at the `R` command prompt. If `R` is configured to use the reference BLAS, these
libraries in the `R` installation tree may be linked to faster alternatives such as
the `Intel MKL`, `OpenBLAS` or the Apple accelerated libraries.

### Linux
    
`dwreml` is linked against the system _libblas.so_ and _liblapack.so_ libraries,
 however, these may not be optimised or multi-threaded and it is recommended
that either the optimized `OpenBlas`, `Atlas` or `Intel MKL` libraries be
installed. `Ubuntu` provides a convenient mechanism **update-alternatives** to
switch between default libraries. For example, the following installs the openMP
multi-threaded openBlas libraries and sets them as the system wide default:

```shellscript
sudo apt-get install libopenblas-openmp-dev
sudo update-alternatives --config libblas.so.3-x86-linux-gnu
sudo update-alternatives --config liblapack.so.3-x86-linux-gnu
```

### macOS

The default `R` reference BLAS symbolic link can be replaced by one to the pre-bundled
Apple accelerated _vecLib_ library. Only link BLAS, not LAPACK.

```shellscript
cd /Library/Frameworks/R.framework/Resources/lib
sudo rm libRblas.dylib
sudo ln -s libRblas.vecLib.dylib libRblas.dylib
```
  
### Windows

The `R` reference libraries _Rblas.dll_ and _Rlapack.dll_ can be symbollically linked to
(or replaced by) 
the `Intel MKL`
redistributable runtime library, for example. The following has been found to work:

1. Install the `Intel MKL` libraries for Windows,
2. In _C:\Program Files\R\R-x.x.x\bin\x64_ make back-up copies of _Rblas.dll_
  and _Rlapack.dll_,
3. Create symbolic links (_mklink.exe_ in an administrator command window) 
  from _Rblas.dll_ and _Rlapack.dll_ to\
  _C:\Program Files (x86)\Intel\oneAPI\mkl\latest\redist\intel64\mkl_rt.1.dll_\
  and from _mkl_intel_thread.1.dll_ to\
  _Program Files (x86)\Intel\oneAPI\mkl\latest\redist\intel64\mkl_intel_thread.1.dll_,
4. Ensure the path to the `Intel MKL` _redist\intel64_ directory 
  is in your PATH environment variable,

substituting installation paths and versions numbers as necessary.

## Developers

David Butler, dbutler@uow.edu.au, author, maintainer\
Sue Welham, stats4biol@gmail.com, author\
Brian Cullis, bcullis@uow.edu.au, contributor\
Luke Mazur, luke.mazur@agtbreeding.com.au, contributor\
Alison Smith, alismith@uow.edu.au, contributor

## Acknowledgements

The Australian Grains Research and Development Corporation is recognised and
thanked for their financial contribution to the team members from 1996 to 2020,
which allowed the development of the skills, confidence, and research that
enabled this project.
