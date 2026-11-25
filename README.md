<h1 align="center">White matter mask in DWI space from FreeSurfer</h1>

<p align="center">
  A binary white matter mask on the diffusion voxel grid, from a FreeSurfer aparc+aseg segmentation and a DWI (or dtiInit) dataset of the same subject.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.341"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.341-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-lightgrey.svg" alt="MIT license"></a>
</p>

> 📍 **This branch, `v1.0`, runs 2 brainlife.io Apps** that share the same code:
>
> - Make white matter mask in dwi space from Freesurfer (dtiinit) ([doi:10.25663/brainlife.app.341](https://doi.org/10.25663/brainlife.app.341))
> - Make white matter mask in dwi space from Freesurfer ([doi:10.25663/brainlife.app.340](https://doi.org/10.25663/brainlife.app.340))
>
> The other Apps in this repository are listed under **Versions on brainlife.io** below.

## 🧠 At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

### 🧩 Make white matter mask in dwi space from Freesurfer (dtiinit)

> **Creates a white matter mask in DWI space from a FreeSurfer aparc+aseg segmentation, using the aligned DWI of a dtiInit output as reference, with FreeSurfer mri_label2vol and mri_binarize.**

Same as the DWI variant, but takes the reference image from a dtiInit output (files.alignedDwRaw in dt6.json): aparc+aseg.mgz is resampled onto that grid by header and white matter, cerebellar white matter, corpus callosum, brainstem and subcortical labels are binarized. The FreeSurfer anatomy must be in the same ACPC space as the dtiInit-aligned DWI. Requires a FreeSurfer license.

| | |
|---|---|
| 📥 **Inputs** | `neuro/freesurfer` · `neuro/dtiinit` |
| 📤 **Outputs** | `neuro/mask` |
| 🐳 **Container** | `brainlife/freesurfer-mini:6.0.1` |
| ⚙️ **Resources** | 1 CPUs · 16 GB memory · 0.17 h walltime |
| 🔑 **Requires** | `FREESURFER_LICENSE` |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.341](https://doi.org/10.25663/brainlife.app.341) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `freesurfer` | `neuro/freesurfer` | yes | FreeSurfer recon-all output; mri/aparc+aseg.mgz is used. |
| `dtiinit` | `neuro/dtiinit` | yes | dtiInit output directory; its aligned DWI (dt6.json files.alignedDwRaw) defines the output mask space. Must be aligned with the FreeSurfer anatomy; no registration is computed. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `mask` | `neuro/mask` | Binary mask in DWI voxel space covering FreeSurfer aparc+aseg white matter, cerebellar white matter, corpus callosum, brainstem and subcortical structures (thalamus, caudate, putamen, pallidum, hippocampus, amygdala, ventral DC). |

### 🧩 Make white matter mask in dwi space from Freesurfer

> **Creates a white matter mask in DWI space from a FreeSurfer aparc+aseg segmentation with FreeSurfer mri_label2vol and mri_binarize, e.g. for tractography seeding.**

Resamples aparc+aseg.mgz onto the DWI voxel grid (mri_label2vol --regheader) and binarizes white matter, cerebellar white matter, corpus callosum, brainstem and subcortical labels into a mask. The FreeSurfer anatomy and the DWI must already be aligned (same scanner/ACPC space), since only the header is used for registration. Requires a FreeSurfer license.

| | |
|---|---|
| 📥 **Inputs** | `neuro/freesurfer` · `neuro/dwi` |
| 📤 **Outputs** | `neuro/mask` |
| 🐳 **Container** | `brainlife/freesurfer-mini:6.0.1` |
| ⚙️ **Resources** | 1 CPUs · 16 GB memory · 0.17 h walltime |
| 🔑 **Requires** | `FREESURFER_LICENSE` |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.340](https://doi.org/10.25663/brainlife.app.340) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `freesurfer` | `neuro/freesurfer` | yes | FreeSurfer recon-all output; mri/aparc+aseg.mgz is used. |
| `dwi` | `neuro/dwi` | yes | DWI image whose voxel grid defines the output mask space. Must be aligned with the FreeSurfer anatomy; no registration is computed. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `mask` | `neuro/mask` | Binary mask in DWI voxel space covering FreeSurfer aparc+aseg white matter, cerebellar white matter, corpus callosum, brainstem and subcortical structures (thalamus, caudate, putamen, pallidum, hippocampus, amygdala, ventral DC). |

<!-- brainlife-app:end -->

## 🏷️ Versions on brainlife.io

Both Apps are built from the same branch; they differ only in where the reference DWI image comes from.

| App | FreeSurfer | Branch | Run it | Status |
|---|---|---|---|---|
| **Make white matter mask in dwi space from Freesurfer (dtiinit)** (this branch) | 6.0.1 | [`v1.0`](https://github.com/brainlife/app-make-white-matter-mask-freesurfer/tree/v1.0) | [doi:10.25663/brainlife.app.341](https://doi.org/10.25663/brainlife.app.341) | current |
| **Make white matter mask in dwi space from Freesurfer** (this branch) | 6.0.1 | [`v1.0`](https://github.com/brainlife/app-make-white-matter-mask-freesurfer/tree/v1.0) | [doi:10.25663/brainlife.app.340](https://doi.org/10.25663/brainlife.app.340) | current |

## 🚀 Running the App

### ☁️ On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.340](https://doi.org/10.25663/brainlife.app.340) (DWI reference) or [doi.org/10.25663/brainlife.app.341](https://doi.org/10.25663/brainlife.app.341) (dtiInit reference), choose a FreeSurfer output and a DWI or dtiInit dataset of the same subject from your project, and press **Execute**. The output is a `neuro/mask` dataset tagged `white_matter`, archived to your project, which can be used, for example, to seed or constrain tractography.

### 💻 Locally

You need [Singularity/Apptainer](https://apptainer.org/), [`jq`](https://jqlang.github.io/jq/) and a [FreeSurfer license](https://surfer.nmr.mgh.harvard.edu/registration.html). The `brainlife/freesurfer-mini:6.0.1` container is pulled from Docker Hub on first use.

1. Clone this repository and check out the registered branch (`git checkout v1.0`).
2. Create `config.json` with the paths to your inputs. With a DWI reference:

   ```json
   {
       "dwi": "/input/dwi/dwi.nii.gz",
       "bvals": "/input/dwi/dwi.bvals",
       "bvecs": "/input/dwi/dwi.bvecs",
       "freesurfer": "/input/freesurfer/output"
   }
   ```

   With a dtiInit reference, replace the DWI keys with `"dtiinit": "/input/dtiinit"`; the aligned DWI listed in `dt6.json` (`files.alignedDwRaw`) is then used.

3. Export your license and run the App:

   ```bash
   export FREESURFER_LICENSE="$(cat ~/freesurfer/license.txt)"
   ./main
   ```

### 🧪 Sample data

Download sample datasets from brainlife.io with the [brainlife CLI](https://github.com/brainlife/cli):

```bash
npm install -g brainlife
bl login
mkdir input
bl dataset download <dataset id>
```

## 📦 Outputs

```text
mask/
└── mask.nii.gz   binary white matter mask on the DWI voxel grid
```

`aparc+aseg.mgz` is resampled onto the DWI grid with `mri_label2vol --regheader`, and `mri_binarize` keeps the cerebral and cerebellar white matter, corpus callosum, brainstem and subcortical labels (thalamus, caudate, putamen, pallidum, hippocampus, amygdala, ventral DC). The resampled `aparc+aseg.nii.gz` and a whole-brain mask (`mask_anat.nii.gz`) are left in the working directory.

## 🩺 Troubleshooting

- **`Please set FREESURFER_LICENSE in .bashrc`**: export the contents of your FreeSurfer `license.txt` in `FREESURFER_LICENSE` before running `./main`.
- **`failed`**: `mask/mask.nii.gz` was not written. Check that the FreeSurfer directory contains `mri/aparc+aseg.mgz` and, for the dtiInit App, that `dt6.json` is present.
- **Mask does not overlap the brain in the DWI**: no registration is computed; only the image headers are used. The FreeSurfer anatomy and the DWI must already be aligned (same scanner or ACPC space).

## 📚 Citing

> [!TIP]
> If you use this App in your work, please cite the App, the software it builds on and brainlife.io (below). GitHub's **Cite this repository** button gives the App citation in APA and BibTeX.

- Dale AM, Fischl B, Sereno MI. Cortical surface-based analysis. I. Segmentation and surface reconstruction. *NeuroImage* 9:179–194 (1999).
- Make white matter mask in dwi space from Freesurfer (dtiinit). brainlife.io App. [doi:10.25663/brainlife.app.341](https://doi.org/10.25663/brainlife.app.341)
- Make white matter mask in dwi space from Freesurfer. brainlife.io App. [doi:10.25663/brainlife.app.340](https://doi.org/10.25663/brainlife.app.340)
- Dale AM, Fischl B, Sereno MI. Cortical surface-based analysis. I. Segmentation and surface reconstruction. NeuroImage 9:179-194 (1999).
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. Sci Data 6, 69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)

## 👥 Authors

- Brad Caron

**Contributors:** Soichi Hayashi

## 💰 Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io is publicly funded, and acknowledging that support helps keep it running. This App was developed with support from Wellcome, the U.S. National Institutes of Health (including the BRAIN Initiative BRAIN CONNECTS program: The Axonal Projectome EXchange, U24NS140384, and the Center for Mesoscale Connectomics, UM1NS132207) and the U.S. National Science Foundation.</sub>

## ⚖️ License

[MIT](LICENSE). FreeSurfer itself is distributed under its own [license](https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferSoftwareLicense).
