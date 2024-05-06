### Leveraging neural networks and edge detection for better UAV localization 🚁🗺️📍
Official implementation for the paper "Leveraging neural networks and edge detection for better UAV localization".

Paper accepted to IGARSS 2024 : [arXiv submission](https://arxiv.org/abs/2404.06207)

> [!WARNING]  
> Code is still in development.

## Method Overview

Offline, the contours of the RGB reference images are extracted to obtain images with a single channel. An AutoEncoder is trained on these images for a pixel-by-pixel reconstruction task. Positions, embeddings and the frozen encoder are taken on board the drone.
Online, the view of the drone is extracted from a camera located underneath the drone. The contours of the RGB image are extracted and passed to the encoder, which produces an embedding. This embedding is compared, by cosine similarity, to all the embeddings of the reference images, and the position is deduced from the position of the reference image with the highest similarity.

<img src="https://github.com/theodpzz/uav-localization/blob/main/figures/overview_method_final.png" alt="Method overview" width="600">

## Getting Started

> [!TIP]
> This section outlines the main steps to discover the code.

### Clone the Repository

To clone this repository, use the following command:

```bash
git clone https://github.com/TheoDpPro/uav-localization.git
```

### Installation

Make sure you have Python 3 installed. Then, install the dependencies using:

```bash
pip install -r requirements.txt
```

### Training

To train the model, run the following command:

```bash
python train.py
```

### Data

Example data is available in example-data folder.

> [!WARNING]  
> These are toy examples and do not correspond to the dataset used.

train.csv, test.csv contain filenames and coordinates of each tile.
Below the structure of the data folder for n reference tiles and m uav views.

```bash
├── train/
│   ├── reference_tile_1.npy
│   ├── reference_tile_2.npy
│   ├── ...
│   └── reference_tile_n.npy
│
├── test/
│   ├── uav_view_1.npy
│   ├── uav_view_2.npy
│   ├── ...
│   └── uav_view_m.npy
│
├── train.csv
└── test.csv
```

## Acknowledgment

Thanks to ABGRALL Corentin, BASCLE Benedicte, DAVAUX Jean-Clément, FACCIOLO Gabriele and MEINHARDT-LLOPIS Enric.

## Citation

> [!IMPORTANT]  
> This project is based on the work by Di Piazza et al. If you use this code in your research, please cite the following paper:

```BibTeX
@inproceedings{dipiazza2024uavloc,
  author    = {Di Piazza Theo, Meinhardt-Llopis Enric, Facciolo Gabriele, Bascle Benedicte, Abgrall Corentin and Devaux Jean-Clement},
  title     = {Leveraging neural networks and edge detection for better UAV localization},
  booktitle = {Proceedings of the IEEE International Geoscience and Remote Sensing Symposium (IGARSS)},
  year      = {2024},
  organization = {IEEE},
}
```
