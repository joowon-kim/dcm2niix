[![Build Status](https://travis-ci.org/rordenlab/dcm2niix.svg?branch=master)](https://travis-ci.org/rordenlab/dcm2niix)
[![Build status](https://ci.appveyor.com/api/projects/status/7o0xp2fgbhadkgn1?svg=true)](https://ci.appveyor.com/project/neurolabusc/dcm2niix)

## About

dcm2niix is a designed to convert neuroimaging data from the DICOM format to the NIfTI format. This web page hosts the developmental source code - a compiled version for Linux, MacOS, and Windows of the most recent stable release is included with [MRIcroGL](https://www.nitrc.org/projects/mricrogl/). A full manual for this software is available in the form of a [NITRC wiki](http://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage).

## License

This software is open source. The bulk of the code is covered by the BSD license. Some units are either public domain (nifti*.*, miniz.c) or use the MIT license (ujpeg.cpp). See the license.txt file for more details.

## Dependencies

This software should run on macOS, Linux and Windows typically without requiring any other software. However, if you use dcm2niix to create gz-compressed images it will be faster if you have [pigz](https://github.com/madler/pigz) installed. You can get a version of both dcm2niix and pigz compiled for your operating system by downloading [MRIcroGL](https://www.nitrc.org/projects/mricrogl/).

## Versions

[See the VERSIONS.md file for details on releases](./VERSIONS.md).

## Running

Command line usage is described in the [NITRC wiki](https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#General_Usage). The minimal command line call would be `dcm2niix /path/to/dicom/folder`. However, you may want to invoke additional options, for example the call `dcm2niix -z y -f %p_%t_%s -o /path/ouput /path/to/dicom/folder` will save data as gzip compressed, with the filename based on the protocol name (%p) acquisition time (%t) and DICOM series number (%s), with all files saved to the folder "output". For more help see help: `dcm2niix -h`.

[See the BATCH.md file for instructions on using the batch processing version](./BATCH.md).

## Build

### Build command line version with cmake (Linux, MacOS, Windows)

`cmake` and `pkg-config` (optional) can be installed as follows:

Ubuntu: `sudo apt-get install cmake pkg-config`

MacOS: `brew install cmake pkg-config`

**To build:**
```bash
mkdir build && cd build
cmake ..
make
```
`dcm2niix` will be created in the `bin` subfolder. To install on the system run `make install` instead of `make` - this will copy the executable to your path so you do not have to provide the full path to the executable.

**optional building with OpenJPEG:**

Support for JPEG2000 using OpenJPEG is optional. To build with OpenJPEG change the cmake command to `cmake -DUSE_OPENJPEG=ON ..`:

```bash
mkdir build && cd build
cmake -DUSE_OPENJPEG=ON ..
make
```

**optional batch processing version:**

The batch processing binary `dcm2niibatch` is optional. To build `dcm2niibatch` as well change the cmake command to `cmake -DBATCH_VERSION=ON ..`. This requires a compiler that supports c++11.

### Building the command line version without cmake

If you have any problems with the cmake build script described above or want to customize the software see the [COMPILE.md file for details on manual compilation](./COMPILE.md).

## Links

  - [Dcm2Bids](https://github.com/cbedetti/Dcm2Bids) uses dcm2niix to create [BIDS](http://bids.neuroimaging.io/) datasets.
  - [bidskit](https://github.com/jmtyszka/bidskit) uses dcm2niix to create [BIDS](http://bids.neuroimaging.io/) datasets.
  - [DAC2BIDS](https://github.com/dangom/dac2bids) uses dcm2niibatch to create [BIDS](http://bids.neuroimaging.io/) datasets.
  - [heudiconv](https://github.com/nipy/heudiconv) can use dcm2niix to create [BIDS](http://bids.neuroimaging.io/) datasets.
  - [nipype](https://github.com/nipy/nipype) can use dcm2niix to convert images.
  - [pydcm2niix is a Python module for working with dcm2niix](https://github.com/jstutters/pydcm2niix).
  - [dcm2niir](https://github.com/muschellij2/dcm2niir) R wrapper for dcm2niix/dcm2nii.
  - [divest](https://github.com/jonclayden/divest) R interface to dcm2niix.
  - [sci-tran dcm2niix](https://github.com/scitran-apps/dcm2niix) docker.
  - [neuro_docker](https://github.com/Neurita/neuro_docker) includes dcm2niix as part of a single, static Dockerfile.
  - [neurodocker](https://github.com/kaczmarj/neurodocker) generates [custom](https://github.com/rordenlab/dcm2niix/issues/138) Dockerfiles given specific versions of neuroimaging software.
  - [dcm2niix_afni](https://afni.nimh.nih.gov/pub/dist/doc/program_help/dcm2niix_afni.html) is a version of dcm2niix included with the [AFNI](https://afni.nimh.nih.gov/) distribution.
  - [MRIcroGL](https://github.com/neurolabusc/MRIcroGL) is available for MacOS, Linux and Windows and provides a graphical interface for dcm2niix. You can get compiled copies from the [MRIcroGL NITRC web site](https://www.nitrc.org/projects/mricrogl/).