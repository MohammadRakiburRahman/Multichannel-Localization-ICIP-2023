# A Multichannel Localization Method for Camouflaged Object Detection (COD)

This repository implements a multichannel method for localizing camouflaged objects in images, as described in [our paper](https://ieeexplore.ieee.org/document/10222056). The method combines Fourier-based texture analysis and Class Activation Mapping (CAM) without requiring GPUs or pre-training.

## Features
- **Dual-Channel Pipeline**:
  - **R1 Channel**: CAM + Global Average Pooling (GAP) for coarse localization.
  - **R2 Channel**: Fourier phase/amplitude analysis + local entropy for texture-based localization.
- **CPU-Compatible**: Runs efficiently on low-resource devices.
- **Training-Free**: Works out-of-the-box on any input image.
- **Generalizable**: Effective on both COD and non-COD datasets.

## Installation
### Requirements
- Python 3.7+
- `opencv-python`, `scikit-image`, `tensorflow`, `scipy`, `numpy`, `matplotlib`

### Setup
```bash
pip install opencv-python scikit-image tensorflow scipy numpy matplotlib
Usage
Prepare Inputs:

Create a folder named DataSet and add your images (JPG/PNG format).

Run the Code:

bash
Copy
python main.py
Outputs:
Results are saved in 8 folders:

Folder	Description
GAP(R1)	CAM heatmaps
R1	Localized regions from CAM
Phase	Fourier-processed images
Entropy	Local entropy maps
R2_Mask	Binary masks from entropy analysis
R2	Localized regions from R2 channel
Mask(R1+R2)	Combined R1+R2 masks
ROI	Final localized images
Performance
| Dataset    | DSC (%) |   MAE | SSIM  |
|------------|--------:|------:|------:|
| COD10K     |    83.0 | 11.88 | 0.93  |
| CHAMELEON  |    73.0 | 14.69 | 0.92  |

Customization
Fourier Filter: Modify gaussianHP()/gaussianLP() cutoff

Entropy Window: Change disk(5) in entropy calculation 

Thresholds: Adjust Otsu thresholds 


Citation
bibtex
Copy
@article{rahman2023multichannel,
  title={A Multichannel Localization Method for Camouflaged Object Detection},
  author={Rahman, Md. Rakibur and Chowdhury, Md. Mafri and Sarkar, Md. Shohanur Rahaman and Karim, Md. Shahriar},
  journal={[arXiv preprint arXiv:XXXX.XXXXX](https://ieeexplore.ieee.org/document/10222056)},
  year={2023}
}
License
Open-source. See LICENSE for details.

Note: Datasets like COD10K must be downloaded separately from their official sources.
